#
# Makefile for GAPS pkgs
#


# 
# Library file names
#

ifndef ARCH
  ARCH=$(shell uname -m)
endif
LIB_DIR=../lib/$(ARCH)
LIB=$(LIB_DIR)/libgaps.a
PKG_LIBS= \
  $(LIB_DIR)/libGSV.a \
  $(LIB_DIR)/libRGBD.a \
  $(LIB_DIR)/libR3Surfels.a \
  $(LIB_DIR)/libR3Graphics.a \
  $(LIB_DIR)/libR3Utils.a \
  $(LIB_DIR)/libR3Shapes.a \
  $(LIB_DIR)/libR2Shapes.a \
  $(LIB_DIR)/libRNMath.a \
  $(LIB_DIR)/libRNBasics.a \
  $(LIB_DIR)/libfglut.a \
  $(LIB_DIR)/libjpeg.a \
  $(LIB_DIR)/libpng.a


# 
# Make targets
#

opt:
	$(MAKE) target "TARGET=$@"
	rm -f $(LIB)
	$(AR) ur $(LIB) $(PKG_LIBS)

debug:
	$(MAKE) target "TARGET=$@"
	rm -f $(LIB)
	$(AR) ur $(LIB) $(PKG_LIBS)

mesa:
	$(MAKE) target "TARGET=$@"

clean:
	$(MAKE) target "TARGET=$@"

release:
	mkdir -p ../release/pkgs
	cp Makefile ../release/pkgs
	$(MAKE) target "TARGET=$@"

target:
	cd RNBasics; $(MAKE) $(TARGET)
	cd RNMath; $(MAKE) $(TARGET)
	cd R2Shapes; $(MAKE) $(TARGET)
	cd R3Shapes; $(MAKE) $(TARGET)
	cd R3Utils; $(MAKE) $(TARGET)
	cd R3Graphics; $(MAKE) $(TARGET)
	cd R3Surfels; $(MAKE) $(TARGET)
	cd RGBD; $(MAKE) $(TARGET)
	cd GSV; $(MAKE) $(TARGET)
ifeq (,$(findstring wasm,$(ARCH)))
	# None of these are needed by
	# Emscripten since it provides its
	# own equivalent libraries.
	cd fglut; $(MAKE) $(TARGET)
	cd jpeg; $(MAKE) $(TARGET)
	cd png; $(MAKE) $(TARGET)
endif





