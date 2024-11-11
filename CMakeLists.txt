cmake_minimum_required(VERSION 3.28)
project(ShellCodeDev)

set(CMAKE_CXX_STANDARD 17)

enable_language(ASM_MASM)

add_executable(ShellCodeDev
        shellcode64.cpp
        shellcode64.h
        GetModule.asm
)

target_link_options(ShellCodeDev PRIVATE
        "/ENTRY:ShellCodeEntry"
        "/SUBSYSTEM:CONSOLE"
        "/FILEALIGN:16"
        "/ALIGN:16"
        "/NODEFAULTLIB"
        "/DYNAMICBASE"
        "/NODEFAULTLIB"
        "/BASE:0x140000000"
)

target_compile_options(ShellCodeDev PRIVATE "/MT")
target_compile_options(ShellCodeDev PRIVATE "/GS-")
target_compile_options(ShellCodeDev PRIVATE "/Od")

set(CMAKE_VERBOSE_MAKEFILE ON)