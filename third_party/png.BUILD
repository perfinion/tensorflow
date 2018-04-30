licenses(["notice"])  # BSD/MIT-like license

genrule(
    name = "copy-png-license",
    outs = ["LICENSE"],
    cmd = "bzcat /usr/share/doc/libpng-*/README.bz2 > $@",
    visibility = ["//visibility:public"],
)

cc_library(
    name = "png",
    hdrs = [
        "png.h",
        "pngconf.h",
    ],
    linkopts = ["-lpng"],
    visibility = ["//visibility:public"],
)
