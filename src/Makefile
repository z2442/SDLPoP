# Project: SDLPoP

CC = psp-gcc
RM = rm -f

TARGET = SDLPop_PSP

HFILES = common.h config.h data.h proto.h types.h
OBJS = main.o data.o seg000.o seg001.o seg002.o seg003.o seg004.o seg005.o seg006.o seg007.o seg008.o seg009.o seqtbl.o replay.o options.o lighting.o screenshot.o menu.o midi.o opl3.o stb_vorbis.o
BIN = ../prince


CPPFLAGS += -Wall -D_GNU_SOURCE=1
CFLAGS += -std=gnu99 -O2 -G0 -DUSE_ALPHA=1

LIBS := -lSDL2_image -lSDL2 -lpng -ljpeg -lGL -lGLU -lglut -lz -lpspvfpu -lpsphprm -lpspsdk -lpspctrl -lpspumd -lpsprtc \
       -lpsppower -lpspgum -lpspgu -lpspaudiolib -lpspaudio -lpsphttp -lpspssl -lpspwlan \
	   -lpspnet_adhocmatching -lpspnet_adhoc -lpspnet_adhocctl -lm -lpspvram


EXTRA_TARGETS = EBOOT.PBP
BUILD_PRX=1
PSP_LARGE_MEMORY=1
PSP_EBOOT_TITLE = SDLPop_PSP
PSP_FW_VERSION=500

PSPSDK=$(shell psp-config --pspsdk-path)
include $(PSPSDK)/lib/build.mak

install:
	./install.sh

uninstall:
	./uninstall.sh

$(BIN): $(OBJ)
	$(CC) $(LDFLAGS) $(OBJ) -o $@ $(LIBS) -lm

%.o: %.c $(HFILES)
	$(CC) $(CPPFLAGS) $(CFLAGS) $(LDFLAGS) -c $<

.PHONY: all clean

