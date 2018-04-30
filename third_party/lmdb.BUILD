# Description:
#   LMDB is the Lightning Memory-mapped Database.

licenses(["notice"])  # OpenLDAP Public License

#exports_files(["LICENSE"])

cc_library(
    name = "lmdb",
    hdrs = [
        "lmdb.h",
        "midl.h",
    ],
    linkopts = ["-llmdb"],
    visibility = ["//visibility:public"],
)

genrule(
    name = "copy-lmdb-license",
    outs = ["LICENSE"],
    cmd = "touch $@",
    visibility = ["//visibility:public"],
)
