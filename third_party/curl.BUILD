# Description:
#   curl is a tool for talking to web servers.

licenses(["notice"])  # MIT/X derivative license

exports_files(["COPYING"])

cc_library(
    name = "curl",
    hdrs = [
        "curl.h",
        "curlbuild.h",
        "curlrules.h",
        "curlver.h",
        "easy.h",
        "mprintf.h",
        "multi.h",
        "stdcheaders.h",
        "typecheck-gcc.h",
    ],
    includes = ["include"],
    visibility = ["//visibility:public"],
)

