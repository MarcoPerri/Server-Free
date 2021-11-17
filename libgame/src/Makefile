CXX	= clang++-devel
BIN_DIR = ../lib
BIN = $(BIN_DIR)/libgame.a

USING_VCPKG = 1

CFLAGS = -Wall -O2 -pipe -mtune=i686 -fno-exceptions -I../include

ifeq ($(USING_VCPKG), 1)
CFLAGS += -m32
VCPKG_DIR = /main/vcpkg
IFLAGS = -I$(VCPKG_DIR)/installed/x86-freebsd/include
endif

LIBS =

OBJFILES = grid.o attribute.o targa.o

default:
	$(MAKE) $(BIN)

$(BIN): $(OBJFILES)
	if [ ! -d $(BIN_DIR) ]; then mkdir $(BIN_DIR); fi
	ar cru $(BIN) $(OBJFILES) $(LIBS)
	ranlib $(BIN)
	chmod 700 $(BIN)

clean:
	rm -f *.o
	rm -f $(BIN)

dep:
	touch Depend
	$(CXX) $(CFLAGS) -MM *.cc > Depend

$(OBJFILES):
	$(CXX) $(CFLAGS) -c $<

include Depend

