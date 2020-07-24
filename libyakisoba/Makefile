PREFIX = /usr/local
DEST_HEADER = $(PREFIX)/include/yakisoba

TARGET = libyakisoba.so
SRCS = Crypto.cpp  Decoder-ECM.cpp  Keys.cpp  Keyset.cpp winscard.cpp
OBJS = $(subst .cpp,.o,$(SRCS))
HEADERS = Crypto.h  Decoder.h  Global.h  Keys.h Keyset.h
CNFPATH = /usr/local/lib/pkgconfig
CNFFILE = libyakisoba.pc

RM := rm
CC := g++ 

PCSCFLAGS = `pkg-config --cflags libpcsclite`
CPPFLAGS = -g -fPIC -O2 $(PCSCFLAGS)
LDFLAGS = -g -fPIC -shared

$(TARGET): $(OBJS)
▸---$(LINK.o) $^ $(LOADLIBES) -o $@

install: $(TARGET) $(HEADERS)
▸---install -m644 $(TARGET) $(PREFIX)/lib/$(TARGET)
▸---mkdir -p $(DEST_HEADER)
▸---install -m644 $(HEADERS) $(DEST_HEADER)
▸---mkdir -p $(CNFPATH)
▸---install -m644 $(CNFFILE) $(CNFPATH) 

uninstall: $(TARGET) $(HEADERS)
▸---$(RM) $(PREFIX)/lib/$(TARGET)
▸---$(RM) $(CNFPATH)/$(CNFFILE) 
▸---$(RM) -rf $(DEST_HEADER)

.PHONY: clean

clean:
▸---$(RM) $(OBJS) $(TARGET)

