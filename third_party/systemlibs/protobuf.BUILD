load("@rules_proto//proto:defs.bzl", "proto_library")
load(
    "@com_google_protobuf//:protobuf.bzl",
    "cc_proto_library",
    "proto_gen",
    "py_proto_library",
)

licenses(["notice"])

filegroup(
    name = "LICENSE",
    visibility = ["//visibility:public"],
)

# Map of all well known protos.
# name => (include path, imports)
WELL_KNOWN_PROTO_MAP = {
    "any" : ("google/protobuf/any.proto", []),
    "api" : ("google/protobuf/api.proto", ["source_context", "type"]),
    "compiler_plugin" : ("google/protobuf/compiler/plugin.proto", ["descriptor"]),
    "descriptor" : ("google/protobuf/descriptor.proto", []),
    "duration" : ("google/protobuf/duration.proto", []),
    "empty" : ("google/protobuf/empty.proto", []),
    "field_mask" : ("google/protobuf/field_mask.proto", []),
    "source_context" : ("google/protobuf/source_context.proto", []),
    "struct" : ("google/protobuf/struct.proto", []),
    "timestamp" : ("google/protobuf/timestamp.proto", []),
    "type" : ("google/protobuf/type.proto", ["any", "source_context"]),
    "wrappers" : ("google/protobuf/wrappers.proto", []),
}

HEADERS = [
    "google/protobuf/any.pb.h",
    "google/protobuf/any.proto",
    "google/protobuf/api.proto",
    "google/protobuf/arena.h",
    "google/protobuf/compiler/importer.h",
    "google/protobuf/compiler/plugin.proto",
    "google/protobuf/descriptor.h",
    "google/protobuf/descriptor.pb.h",
    "google/protobuf/descriptor.proto",
    "google/protobuf/duration.pb.h",
    "google/protobuf/duration.proto",
    "google/protobuf/dynamic_message.h",
    "google/protobuf/empty.pb.h",
    "google/protobuf/empty.proto",
    "google/protobuf/field_mask.pb.h",
    "google/protobuf/field_mask.proto",
    "google/protobuf/io/coded_stream.h",
    "google/protobuf/io/zero_copy_stream.h",
    "google/protobuf/io/zero_copy_stream_impl_lite.h",
    "google/protobuf/map.h",
    "google/protobuf/repeated_field.h",
    "google/protobuf/source_context.proto",
    "google/protobuf/struct.proto",
    "google/protobuf/text_format.h",
    "google/protobuf/timestamp.pb.h",
    "google/protobuf/timestamp.proto",
    "google/protobuf/type.proto",
    "google/protobuf/util/json_util.h",
    "google/protobuf/util/type_resolver_util.h",
    "google/protobuf/wrappers.pb.h",
    "google/protobuf/wrappers.proto",
]

genrule(
    name = "link_headers",
    outs = HEADERS,
    cmd = """
      for i in $(OUTS); do
        f=$${i#$(@D)/}
        mkdir -p $(@D)/$${f%/*}
        ln -sf $(INCLUDEDIR)/$$f $(@D)/$$f
      done
    """,
)

cc_library(
    name = "protobuf",
    hdrs = HEADERS,
    linkopts = ["-lprotobuf"],
    visibility = ["//visibility:public"],
)

cc_library(
    name = "protobuf_headers",
    hdrs = HEADERS,
    linkopts = ["-lprotobuf"],
    visibility = ["//visibility:public"],
)

cc_library(
    name = "protoc_lib",
    linkopts = ["-lprotoc"],
    visibility = ["//visibility:public"],
)

genrule(
    name = "protoc",
    outs = ["protoc.bin"],
    cmd = "ln -s $$(which protoc) $@",
    executable = 1,
    visibility = ["//visibility:public"],
)

cc_proto_library(
    name = "cc_wkt_protos",
    hdrs = HEADERS,
    internal_bootstrap_hack = 1,
    protoc = ":protoc",
    visibility = ["//visibility:public"],
)

proto_gen(
    name = "protobuf_python_genproto",
    includes = ["."],
    protoc = "@com_google_protobuf//:protoc",
    visibility = ["//visibility:public"],
)

py_library(
    name = "protobuf_python",
    data = [":link_headers"],
    srcs_version = "PY2AND3",
    visibility = ["//visibility:public"],
)

[proto_library(
    name = proto[0] + "_proto",
    srcs = [proto[1][0]],
    deps = [dep + "_proto" for dep in proto[1][1]],
    visibility = ["//visibility:public"],
    ) for proto in WELL_KNOWN_PROTO_MAP.items()]
