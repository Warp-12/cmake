cmake_minimum_required(VERSION 3.10)
project(Greeter VERSION 1.0)

set(CMAKE_CXX_STANDARD 17)
set(CXX_STANDARD_REQUIRED ON)

set(SRC
    main.cpp
    greeter.cpp
    person.cpp
)

add_library(${PROJECT_NAME}-lib STATIC  ${SRC})
add_executable(${PROJECT_NAME} ${SRC})
add_executable(${PROJECT_NAME}-ut ../test/greeter.ut.cpp)

target_link_libraries(${PROJECT_NAME} ${PROJECT_NAME}-lib)
target_link_libraries(${PROJECT_NAME}-ut ${PROJECT_NAME}-lib)

set(FLAGS -Wall -Wextra -Werror -pedantic -Wconversion -O3)

target_compile_options(${PROJECT_NAME} PRIVATE ${FLAGS})
target_compile_options(${PROJECT_NAME}-ut PRIVATE ${FLAGS})
target_compile_options(${PROJECT_NAME}-lib PRIVATE ${FLAGS})

enable_testing()
add_test(NAME greeterTEsts COMMAND ./${PROJECT_NAME}-ut)
