licenses(["restricted"])  # GPLv3

genrule(
    name = "copy-swig-license",
    outs = ["LICENSE"],
    cmd = "bzcat /usr/share/doc/swig-*/README.bz2 > $@",
    visibility = ["//visibility:public"],
)

filegroup(
    name = "templates",
    licenses = ["notice"],  # simple notice license for Lib/
    path = "Lib",
    visibility = ["//visibility:public"],
)

genrule(
    name = "cpswiglink",
    outs = ["swiglink"],
    cmd = "cp /usr/bin/swig $@",
)

sh_binary(
    name = "swig",
    srcs = ["swiglink"],
    deps = ["cpswiglink"],
    visibility = ["//visibility:public"],
)
