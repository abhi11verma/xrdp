EXTRA_DEFINES =
EXTRA_INCLUDES =
EXTRA_LIBS =
EXTRA_FLAGS =

if XRDP_DEBUG
EXTRA_DEFINES += -DXRDP_DEBUG
else
EXTRA_DEFINES += -DXRDP_NODEBUG
endif

if XRDP_NEUTRINORDP
EXTRA_DEFINES += -DXRDP_NEUTRINORDP
EXTRA_LIBS += $(FREERDP_LIBS)
endif

if XRDP_TJPEG
EXTRA_DEFINES += -DXRDP_JPEG -DXRDP_TJPEG
EXTRA_INCLUDES += @TurboJpegIncDir@
EXTRA_FLAGS += @TurboJpegLibDir@
EXTRA_LIBS += -lturbojpeg
else
if XRDP_JPEG
EXTRA_DEFINES += -DXRDP_JPEG
EXTRA_LIBS += -ljpeg
endif
endif

AM_CPPFLAGS = \
  -DXRDP_CFG_PATH=\"${sysconfdir}/xrdp\" \
  -DXRDP_SBIN_PATH=\"${sbindir}\" \
  -DXRDP_SHARE_PATH=\"${datadir}/xrdp\" \
  -DXRDP_PID_PATH=\"${localstatedir}/run\" \
  $(EXTRA_DEFINES) \
  -I$(top_srcdir)/common \
  $(EXTRA_INCLUDES)

module_LTLIBRARIES = \
  libxrdp.la

libxrdp_la_SOURCES = \
  libxrdp.c \
  libxrdp.h \
  libxrdpinc.h \
  xrdp_bitmap32_compress.c \
  xrdp_bitmap_compress.c \
  xrdp_caps.c \
  xrdp_channel.c \
  xrdp_fastpath.c \
  xrdp_iso.c \
  xrdp_jpeg_compress.c \
  xrdp_mcs.c \
  xrdp_mppc_enc.c \
  xrdp_orders.c \
  xrdp_orders_rail.c \
  xrdp_orders_rail.h \
  xrdp_rdp.c \
  xrdp_sec.c

libxrdp_la_LDFLAGS = \
  $(EXTRA_FLAGS)

libxrdp_la_LIBADD = \
  $(top_builddir)/common/libcommon.la \
  $(EXTRA_LIBS)
