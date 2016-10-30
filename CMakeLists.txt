cmake_minimum_required (VERSION 2.6)

project (calc)

set (CMAKE_C_FLAGS "-g -O0")

add_executable(calc
	src/calc.c
	src/precedence.c
	src/stk.c
	src/stk.h
)
