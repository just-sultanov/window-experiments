.PHONY: build

HELLO_WORLD=hello-world/cpp/example.o


ifdef DEBUG
DBG_OPT_FLAGS=-g
else
DBG_OPT_FLAGS=-O2
endif

ifdef ASAN
ASAN_FLAGS=-fsanitize=address
else
ASAN_FLAGS=
endif


CC=clang++
CFLAGS=-Wall -std=c++20 -I../macos/metal/cpp/core -I../macos/metal/cpp/extensions -fno-objc-arc $(DBG_OPT_FLAGS) $(ASAN_FLAGS)
LDFLAGS=-framework Metal -framework Foundation -framework Cocoa -framework CoreGraphics -framework MetalKit 

VPATH=../macos/metal/cpp/core



%.o: %.cpp
	$(CC) -c $(CFLAGS) $< -o $@



build: clean build/hello-world



build/hello-world: $(HELLO_WORLD) Makefile
	$(CC) $(CFLAGS) $(LDFLAGS) $(HELLO_WORLD) -o $@



clean:
	rm -f $(HELLO_WORLD) build/hello-world

