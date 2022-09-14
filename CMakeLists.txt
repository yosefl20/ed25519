# CMakeLists files in this project can
# refer to the root source directory of the project as ${HELLO_SOURCE_DIR} and
# to the root binary directory of the project as ${HELLO_BINARY_DIR}.
cmake_minimum_required (VERSION 2.8.11)
project (ed25519)

# Create a library called "Hello" which includes the source file "hello.cxx".
# The extension is already found. Any number of sources could be listed here.
add_library (ed25519
		src/add_scalar.c
		src/key_exchange.c
		src/seed.c
		src/verify.c
		src/fe.c
           	src/keypair.c
      		src/sha512.c
		src/ge.c
           	src/sc.c
           	src/sign.c)

# Make sure the compiler can find include files for our Hello library
# when other libraries or executables link to Hello
target_include_directories (ed25519 PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

# Add executable called "helloDemo" that is built from the source files
# "demo.cxx" and "demo_b.cxx". The extensions are automatically found.
add_executable (ed25519-tests test.c)

# Link the executable to the Hello library. Since the Hello library has
# public include directories we will use those link directories when building
# helloDemo
target_link_libraries (ed25519-tests LINK_PUBLIC ed25519)
