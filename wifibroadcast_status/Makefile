PREFIX=/usr
BINDIR=$(PREFIX)/bin
LIBDIR=$(PREFIX)/lib

# CPPFLAGS+= -I/opt/vc/include/ -I/opt/vc/include/interface/vcos/pthreads -I/opt/vc/include/interface/vmcs_host/linux
# LDFLAGS+= -lfreetype -lz
# LDFLAGS+=-L/opt/vc/lib/ -lGLESv2 -lEGL -lopenmaxil -lbcm_host -lvcos -lvchiq_arm -lpthread -lrt -lm -lshapes

# VC_LIBDIR ?= /opt/vc/lib
# VC_INCDIR ?= /opt/vc/include

# INCLUDEFLAGS=-I$(VC_INCDIR) -I$(VC_INCDIR)/interface/vmcs_host/linux -I$(VC_INCDIR)/interface/vcos/pthreads 
# LIBFLAGS=-L$(VC_LIBDIR) -lEGL -lGLESv2 -ljpeg

LIB_SHAPES=-L$(SYSROOT)$(LIBDIR) -lshapes
# LD_RPATH=-Wl,-rpath=$(LIBDIR)

PROGRAM=wbc_status

all: $(PROGRAM)

%.o: %.c
	$(CC) -c -o $@ $< $(CFLAGS)

$(PROGRAM): $(PROGRAM).o
	$(CC) -o $@ $^ $(LDFLAGS) $(LD_RPATH) $(LIB_SHAPES) 

clean:
	rm -f $(PROGRAM) *.o *~

.PHONY: install
install: $(PROGRAM)
	install -D -m 0755 $(PROGRAM) $(DESTDIR)$(BINDIR)/$(PROGRAM)



