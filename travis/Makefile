#!/usr/bin/make

kcov_deps=libdw-dev libelf-dev elfutils libcurl4-openssl-dev python-pip python3 cmake binutils-dev

.PHONY: prepare_environment

build:
	mkdir -p build
	cd build && cmake ..
	make -C build

run-tests: build run-tests-${CC}

run-tests-gcc: run-tests
	kcov /tmp/kcov build/calc 1+1
	kcov /tmp/kcov build/calc -h 9-99
	kcov --coveralls-id=$(TRAVIS_JOB_ID) /tmp/kcov build/calc -h 9^3

run-tests-clang:

prepare_linux:
	sudo apt-get update -y
	sudo apt-get install -y ${kcov_deps} gcc-multilib debootstrap git time wget
	wget https://github.com/SimonKagstrom/kcov/archive/master.tar.gz
	sh -c "tar xzf master.tar.gz && mkdir kcov-master/build && cd kcov-master/build && cmake .. && make && sudo make install"

prepare_environment: prepare_${TRAVIS_OS_NAME}
