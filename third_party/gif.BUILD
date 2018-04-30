licenses(["notice"])  # MIT

#    #hdrs = ["gif_lib.h"],
cc_library(
    name = "gif",
    hdrs = [],
    linkopts = ["-lgif"],
    visibility = ["//visibility:public"],
)

genrule(
    name = "copy-gif-license",
    outs = ["COPYING"],
    cmd = "bzcat /usr/share/doc/giflib-*/AUTHORS.bz2 > $@",
    visibility = ["//visibility:public"],
)
