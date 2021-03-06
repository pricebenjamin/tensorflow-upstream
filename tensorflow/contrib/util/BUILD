# Description:
#   contains parts of TensorFlow that are experimental or unstable and which are not supported.

licenses(["notice"])  # Apache 2.0

exports_files(["LICENSE"])

package(default_visibility = ["//tensorflow:__subpackages__"])

load("//tensorflow:tensorflow.bzl", "tf_cc_binary")
load("//tensorflow:tensorflow.bzl", "tf_cc_test")

# Convertor of a frozen graph definition into the memmapped format.
cc_library(
    name = "convert_graphdef_memmapped_format_lib",
    srcs = ["convert_graphdef_memmapped_format_lib.cc"],
    hdrs = ["convert_graphdef_memmapped_format_lib.h"],
    deps = [
        "//tensorflow/core:array_ops_op_lib",
        "//tensorflow/core:framework",
        "//tensorflow/core:framework_internal",
        "//tensorflow/core:functional_ops_op_lib",
        "//tensorflow/core:lib",
        "//tensorflow/core:nn_ops_op_lib",
        "//tensorflow/core:no_op_op_lib",
        "//tensorflow/core:protos_all_cc",
        "//tensorflow/core:sendrecv_ops_op_lib",
        "//tensorflow/core:tensorflow",
        "//tensorflow/core/kernels:immutable_constant_op",
    ],
)

tf_cc_binary(
    name = "convert_graphdef_memmapped_format",
    srcs = ["convert_graphdef_memmapped_format.cc"],
    deps = [
        ":convert_graphdef_memmapped_format_lib",
        "//tensorflow/core:framework_internal",
        "//tensorflow/core:lib",
    ],
)

tf_cc_test(
    name = "convert_graphdef_memmapped_format_test",
    srcs = ["convert_graphdef_memmapped_format_test.cc"],
    linkopts = select({
        "//tensorflow:darwin": ["-headerpad_max_install_names"],
        "//conditions:default": [],
    }),
    deps = [
        ":convert_graphdef_memmapped_format_lib",
        "//tensorflow/cc:cc_ops",
        "//tensorflow/core:core_cpu",
        "//tensorflow/core:framework",
        "//tensorflow/core:lib",
        "//tensorflow/core:tensor_testutil",
        "//tensorflow/core:test",
        "//tensorflow/core:test_main",
    ],
)

tf_cc_binary(
    name = "inspect_checkpoint",
    srcs = ["inspect_checkpoint.cc"],
    deps = [
        "//tensorflow/core:framework",
        "//tensorflow/core:lib",
        "//tensorflow/core:tensorflow",
    ],
)

py_library(
    name = "util_py",
    srcs = glob(["**/*.py"]),
    srcs_version = "PY2AND3",
    deps = [
        "//tensorflow/python:framework",
        "//tensorflow/python:platform",
        "//tensorflow/python:tensor_util",
        "//tensorflow/python:util",
    ],
)
