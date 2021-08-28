CC = gcc
CFLAGS = -s -O3

# Windows gets Compress.exe and Compress32.exe
# MacOS gets Compress.out (it doesn't support 32 bit programs)
# Linux gets Compress

ifeq ($(OS), Windows_NT)
	EXECUTABLES = Compress.exe Compress32.exe
else
	UNAME_S = $(shell uname -s)
	ifeq ($(UNAME_S), Darwin)
		EXECUTABLES = Compress.out
	endif

	ifeq ($(UNAME_S), Linux)
		EXECUTABLES = Compress
	endif
endif

all: $(EXECUTABLES)

.SUFFIXES: .c
Compress.exe: compressor.c
	$(CC) $(CFLAGS) -o $@ $^ -l:libpthread.a

.SUFFIXES: .c
Compress32.exe: compressor.c
	$(CC) $(CFLAGS) -m32 -o $@ $^ -l:libpthread.a

.SUFFIXES: .c
Compress.out: compressor.c
	$(CC) $(CFLAGS) -o $@ $^

.SUFFIXES: .c
Compress: compressor.c
	$(CC) $(CFLAGS) -o $@ $^ -lpthread
