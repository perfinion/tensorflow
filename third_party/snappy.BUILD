package(default_visibility = ["//visibility:public"])

licenses(["notice"])  # BSD 3-Clause

cc_library(
    name = "snappy",
    hdrs = ["snappy.h",
        "snappy-c.h",
        "snappy-sinksource.h",
        "snappy-stubs-public.h"
    ],
    linkopts = ["-lsnappy"],
)

genrule(
    name = "copy-snappy-license",
    outs = ["COPYING"],
    cmd = "bzcat /usr/share/doc/snappy-1.1.7/README.md.bz2 > $@",
    visibility = ["//visibility:public"],
)

genrule(
    name = "snappy_stubs_public_h",
    srcs = ["snappy-stubs-public.h.in"],
    outs = ["snappy-stubs-public.h"],
    cmd = ("sed " +
           "-e 's/$${\\(.*\\)_01}/\\1/g' " +
           "-e 's/$${SNAPPY_MAJOR}/1/g' " +
           "-e 's/$${SNAPPY_MINOR}/1/g' " +
           "-e 's/$${SNAPPY_PATCHLEVEL}/4/g' " +
           "$< >$@"),
)
