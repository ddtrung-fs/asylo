#
# Copyright 2018 Asylo authors
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#

licenses(["notice"])  # Apache v2.0

# Description:
#   This package contains C++ components provided for users of the enclave gRPC
#   stack, including:
#     * Channel and server credentials objects
#     * Assertion generator and verifier interfaces
#     * Null assertion libraries
package(default_visibility = ["//asylo:__subpackages__"])

exports_files(["LICENSE"])

load("//asylo/bazel:asylo.bzl", "cc_test")

# gRPC channel and server credentials objects.
cc_library(
    name = "grpc++_security_enclave",
    srcs = [
        "enclave_channel_credentials.cc",
        "enclave_server_credentials.cc",
    ],
    hdrs = [
        "enclave_channel_credentials.h",
        "enclave_credentials_options.h",
        "enclave_server_credentials.h",
    ],
    visibility = ["//visibility:public"],
    deps = [
        "//asylo/grpc/auth/core:grpc_security_enclave",
        "//asylo/grpc/auth/util:enclave_assertion_util",
        "//asylo/grpc/auth/util:safe_string",
        "//asylo/identity:identity_proto_cc",
        "@com_github_grpc_grpc//:grpc++",
    ],
)

cc_library(
    name = "enclave_auth_context",
    srcs = ["enclave_auth_context.cc"],
    hdrs = ["enclave_auth_context.h"],
    visibility = ["//visibility:public"],
    deps = [
        "//asylo/grpc/auth/core:grpc_security_enclave",
        "//asylo/grpc/auth/core:handshake_proto_cc",
        "//asylo/identity:identity_proto_cc",
        "//asylo/util:status",
        "@com_github_grpc_grpc//:grpc++",
        "@com_github_grpc_grpc//:grpc_secure",
        "@com_google_absl//absl/strings",
        "@com_google_protobuf//:protobuf_lite",
    ],
)

cc_test(
    name = "enclave_auth_context_test",
    srcs = ["enclave_auth_context_test.cc"],
    tags = ["regression"],
    deps = [
        ":enclave_auth_context",
        "//asylo/grpc/auth/core:grpc_security_enclave",
        "//asylo/grpc/auth/core:handshake_proto_cc",
        "//asylo/test/util:status_matchers",
        "//asylo/test/util:test_main",
        "@com_github_grpc_grpc//:grpc++",
        "@com_github_grpc_grpc//:grpc_secure",
        "@com_google_absl//absl/memory",
        "@com_google_googletest//:gtest",
        "@com_google_protobuf//:protobuf",
        "@com_google_protobuf//:protobuf_lite",
    ],
)
