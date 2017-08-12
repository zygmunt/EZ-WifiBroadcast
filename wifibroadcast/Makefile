PREFIX=/usr
BINDIR=$(PREFIX)/bin

LIBPCAP=-lrt -lpcap 
LIBWIRINGPI=-lwiringPi
# CPPFLAGS=-Wall -D _GNU_SOURCE

PROGRAMS = rx rcrx rssirx rssitx tx rx_status channelscan check_alive rssi_forward rssi_forward_stdout rssi_write_shmem
PROGRAMS_FULL = $(PROGRAMS) tracker 

all: $(PROGRAMS)
full: $(PROGRAMS_FULL)

%.o: %.c
	$(CC) -c -o $@ $< $(CFLAGS)

rx: rx.o lib.o radiotap.o fec.o
	$(CC) -o $@ $^ $(LDFLAGS) $(LIBPCAP)

rcrx: rcrx.o lib.o radiotap.o
	$(CC) -o $@ $^ $(LDFLAGS) $(LIBPCAP)

rssirx: rssirx.o lib.o radiotap.o
	$(CC) -o $@ $^ $(LDFLAGS) $(LIBPCAP)

rssitx: rssitx.o lib.o radiotap.o
	$(CC) -o $@ $^ $(LDFLAGS) $(LIBPCAP)

tx: tx.o lib.o fec.o
	$(CC) -o $@ $^ $(LDFLAGS) $(LIBPCAP)

rx_status: rx_status.o
	$(CC) -o $@ $^ $(LDFLAGS) $(LIBPCAP)

tracker: tracker.o
	$(CC) -o $@ $^ $(LDFLAGS)  $(LIBPCAP) $(LIBWIRINGPI)

channelscan: channelscan.o
	$(CC) -o $@ $^ $(LDFLAGS) $(LIBPCAP)

check_alive: check_alive.o
	$(CC) -o $@ $^ $(LDFLAGS) $(LIBPCAP)

rssi_forward: rssi_forward.o
	$(CC) -o $@ $^ $(LDFLAGS) $(LIBPCAP)

rssi_forward_stdout: rssi_forward_stdout.o
	$(CC) -o $@ $^ $(LDFLAGS) $(LIBPCAP)

rssi_write_shmem: rssi_write_shmem.o
	$(CC) -o $@ $^ $(LDFLAGS) $(LIBPCAP)

.PHONY: install
install: $(PROGRAMS)
	$(foreach prog,$(PROGRAMS),install -D -m 0755 $(prog) $(DESTDIR)$(BINDIR)/$(prog);)

clean:
	rm -f $(PROGRAMS_FULL) *~ *.o
