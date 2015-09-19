AM_CFLAGS = -I$(top_srcdir)/include

lib_LTLIBRARIES = libshairport.la
libshairport_la_SOURCES = alac.c alac.h audio.c audio_dummy.c audio_pipe.c audio.h common.h daemon.c daemon.h getopt_long.h metadata.c metadata.h mdns.c mdns_external.c mdns_tinysvcmdns.c common.c mdns.h rtp.c rtp.h rtsp.c rtsp.h tinysvcmdns.c tinysvcmdns.h player.c player.h
libshairport_la_CFLAGS = $(AM_CFLAGS)
libshairport_la_LDFLAGS = 

if WITH_ALSA
libshairport_la_SOURCES += audio_alsa.c
endif

if WITH_AO
libshairport_la_SOURCES += audio_ao.c
endif

if WITH_PULSE
libshairport_la_SOURCES += audio_pulse.c
endif

if WITH_SNDIO
libshairport_la_SOURCES += audio_sndio.c
endif
