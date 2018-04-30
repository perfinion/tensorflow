licenses(["notice"])  # BSD

exports_files(["LICENCE"])

genrule(
    name = "copy-pcre-license",
    outs = ["LICENSE"],
    cmd = "bzcat /usr/share/doc/libpcre-*/LICENCE.bz2 > $@",
    visibility = ["//visibility:public"],
)

cc_library(
    name = "pcre",
    hdrs = [
        "pcre.h",
        "pcreposix.h",
    ],
    linkopts = ["-lpcre"],
    visibility = ["//visibility:public"],
)
