M_PREFIX=$(PREFIX)

TARGET=libamadec.so

TARGET_OBJS=adec-external-ctrl.o adec-internal-mgt.o adec-ffmpeg-mgt.o adec-message.o adec-pts-mgt.o feeder.o adec_write.o adec_read.o\
           dsp/audiodsp-ctl.o audio_out/alsa-out.o audio_out/aml_resample.o audiodsp_update_format.o spdif_api.o pcmenc_api.o dts_transenc_api.o dts_enc.o audio_out/alsactl_parser.o 

INSTALL_DIR=${M_PREFIX}/lib

LDFLAGS += -shared -lpthread -lm -lasound -lrt -ldl

CFLAGS+=-O2 -fPIC
CFLAGS+=-I$(shell pwd) -I$(shell pwd)/include -I$(shell pwd)/../amavutils/include -I${PREFIX}/include -I${PREFIX}/usr/include -L${PREFIX}/lib -L${PREFIX}/usr/lib
CFLAGS+=-DALSA_OUT -DENABLE_WAIT_FORMAT

export CC CFLAGS

all: $(TARGET) 

$(TARGET): $(TARGET_OBJS)
	$(CC) $(CFLAGS) $(TARGET_OBJS:%.o=%.c) $(LDFLAGS) -o $@  

install:$(TARGET)
	-install -m 555 ${TARGET} $(INSTALL_DIR)

force:

clean:
	-rm -rf *.o ${AMADEC_DIST} ${MP3LIB} $(PCMLIB) $(ADPCMLIB) $(AACLIB) $(A52LIB)
