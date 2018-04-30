# Description:
#   Six provides simple utilities for wrapping over differences between Python 2
#   and Python 3.

licenses(["notice"])  # MIT

genrule(
    name = "copy-six-license",
    outs = ["LICENSE"],
    cmd = "bzcat /usr/share/doc/six-*/README.rst.bz2 > $@",
    visibility = ["//visibility:public"],
)

py_library(
    name = "six",
    srcs = ["six.py"],
    srcs_version = "PY2AND3",
    visibility = ["//visibility:public"],
)
