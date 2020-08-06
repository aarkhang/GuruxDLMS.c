cmake_minimum_required(VERSION 3.12)

project(GuruxDLMS VERSION 1.0
                  DESCRIPTION "This is a high-performance ANSI C component that helps you to read you DLMS/COSEM compatible electricity, gas or water meters"
                  LANGUAGES C)

add_subdirectory(development)
add_subdirectory(GuruxDLMSServerExample)
add_subdirectory(GuruxDLMSClientExample)
