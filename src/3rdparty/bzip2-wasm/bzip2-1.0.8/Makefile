CC = emcc
SRC = $(wildcard *.c )
CFLAGS = -Wall -Winline -O2 -D_FILE_OFFSET_BITS=64
LDFLAGS = -s EXPORT_ES6=1 -s MODULARIZE=1 -s EXPORT_NAME=loadBZip2WASM
LDFLAGS += -s EXPORTED_FUNCTIONS="[_BZ2_bzBuffToBuffDecompress,_BZ2_bzBuffToBuffCompress,_malloc,_free]"
LDFLAGS += -s EXPORTED_RUNTIME_METHODS="[setValue,getValue]"
LDFLAGS += -s ALLOW_MEMORY_GROWTH=1
OBJ = $(SRC:.c=.o)

bzip2.mjs: $(OBJ)
	$(CC) -o $@ $^ $(LDFLAGS)

clean:
	rm -f *.wasm *.o bzip2.mjs
