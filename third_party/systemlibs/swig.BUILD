licenses(["restricted"])  # GPLv3

filegroup(
    name = "LICENSE",
    visibility = ["//visibility:public"],
)

filegroup(
    name = "templates",
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
    visibility = ["//visibility:public"],
)
