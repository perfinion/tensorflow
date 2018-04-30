# Description:
#   libjpeg-turbo is a drop in replacement for jpeglib optimized with SIMD.

licenses(["notice"])  # custom notice-style license, see LICENSE.md

genrule(
    name = "copy-jpeg-license",
    outs = ["LICENSE.md"],
    cmd = "bzcat /usr/share/doc/libjpeg-turbo-*/LICENSE.md.bz2 > $@",
    visibility = ["//visibility:public"],
)

genrule(
    name = "configure",
    outs = ["jconfig.h"],
    cmd = "cp /usr/include/x86_64-pc-linux-gnu/jconfig.h $@",
)

cc_library(
    name = "jpeg",
    hdrs = [
        "jerror.h",
        "jmorecfg.h",
        "jpeglib.h",
	"jconfig.h",
    ],
    linkopts = ["-ljpeg"],
    visibility = ["//visibility:public"],
)
