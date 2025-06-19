cmake_minimum_required(VERSION 3.10)
project(fastp)
add_compile_options(-Wall -O3 -g)

find_package(Threads REQUIRED)
find_package(ZLIB REQUIRED)

# configure required header and source file
include_directories(src)
include_directories(src/zlib)
include_directories(src/sdust)
aux_source_directory(src SRC_FILES)

# build
add_executable(${PROJECT_NAME} ${SRC_FILES} src/sdust/sdust.c src/sdust/kalloc.c)
# Link with required isal pthreads and zlib
target_link_libraries(${PROJECT_NAME} isal deflate pthread z)

