load("@bazel_skylib//:bzl_library.bzl", "bzl_library")

licenses(["notice"])

bzl_library(
    name = "actions",
    srcs = ["actions.bzl"],
    visibility = ["//swift:__subpackages__"],
    deps = [
        ":features",
        ":toolchain_config",
        "@bazel_skylib//lib:partial",
        "@bazel_skylib//lib:types",
    ],
)

bzl_library(
    name = "attrs",
    srcs = ["attrs.bzl"],
    visibility = [
        "//proto:__subpackages__",
        "//swift:__subpackages__",
    ],
    deps = [
        ":providers",
        "@bazel_skylib//lib:dicts",
    ],
)

bzl_library(
    name = "autolinking",
    srcs = ["autolinking.bzl"],
    visibility = ["//swift:__subpackages__"],
    deps = [
        ":actions",
        ":toolchain_config",
    ],
)

bzl_library(
    name = "compiling",
    srcs = ["compiling.bzl"],
    visibility = [
        "//proto:__subpackages__",
        "//swift:__subpackages__",
    ],
    deps = [
        ":actions",
        ":autolinking",
        ":debugging",
        ":derived_files",
        ":developer_dirs",
        ":explicit_module_map_file",
        ":feature_names",
        ":features",
        ":providers",
        ":toolchain_config",
        ":utils",
        ":vfsoverlay",
        "//swift/toolchains/config:compile_module_interface_config",
        "@bazel_skylib//lib:collections",
        "@bazel_skylib//lib:partial",
        "@bazel_skylib//lib:paths",
        "@bazel_skylib//lib:types",
    ],
)

bzl_library(
    name = "debugging",
    srcs = ["debugging.bzl"],
    visibility = ["//swift:__subpackages__"],
    deps = [
        ":actions",
        ":derived_files",
        ":toolchain_config",
    ],
)

bzl_library(
    name = "derived_files",
    srcs = ["derived_files.bzl"],
    visibility = ["//swift:__subpackages__"],
    deps = [
        ":utils",
        "@bazel_skylib//lib:paths",
    ],
)

bzl_library(
    name = "developer_dirs",
    srcs = ["developer_dirs.bzl"],
    visibility = ["//swift:__subpackages__"],
    deps = ["@bazel_skylib//lib:paths"],
)

bzl_library(
    name = "features",
    srcs = ["features.bzl"],
    visibility = ["//swift:__subpackages__"],
    deps = [
        ":feature_names",
        ":package_specs",
        "@bazel_skylib//lib:collections",
        "@bazel_skylib//lib:new_sets",
    ],
)

bzl_library(
    name = "linking",
    srcs = ["linking.bzl"],
    visibility = [
        "//proto:__subpackages__",
        "//swift:__subpackages__",
    ],
    deps = [
        ":derived_files",
        "@bazel_skylib//lib:collections",
        "@bazel_skylib//lib:partial",
        "@bazel_tools//tools/build_defs/cc:action_names.bzl",
    ],
)

bzl_library(
    name = "module_maps",
    srcs = ["module_maps.bzl"],
    visibility = ["//swift:__subpackages__"],
    deps = ["@bazel_skylib//lib:paths"],
)

bzl_library(
    name = "providers",
    srcs = ["providers.bzl"],
    visibility = ["//swift:__subpackages__"],
    deps = [
        "@bazel_skylib//lib:sets",
        "@bazel_skylib//lib:types",
    ],
)

bzl_library(
    name = "swift_autoconfiguration",
    srcs = ["swift_autoconfiguration.bzl"],
    visibility = ["//swift:__subpackages__"],
    deps = ["@build_bazel_rules_swift//swift/internal:feature_names"],
)

bzl_library(
    name = "swift_feature_allowlist",
    srcs = ["swift_feature_allowlist.bzl"],
    visibility = ["//swift:__subpackages__"],
    deps = [
        ":providers",
    ],
)

bzl_library(
    name = "swift_clang_module_aspect",
    srcs = ["swift_clang_module_aspect.bzl"],
    visibility = [
        "//proto:__subpackages__",
        "//swift:__subpackages__",
    ],
    deps = [
        ":attrs",
        ":compiling",
        ":derived_files",
        ":feature_names",
        ":features",
        ":module_maps",
        ":providers",
        ":utils",
    ],
)

bzl_library(
    name = "swift_common",
    srcs = ["swift_common.bzl"],
    visibility = ["//swift:__subpackages__"],
    deps = [
        ":attrs",
        ":compiling",
        ":features",
        ":linking",
        ":providers",
        ":swift_clang_module_aspect",
    ],
)

bzl_library(
    name = "swift_import",
    srcs = ["swift_import.bzl"],
    visibility = ["//swift:__subpackages__"],
    deps = [
        ":attrs",
        ":compiling",
        ":providers",
        ":swift_common",
        ":utils",
        "@bazel_skylib//lib:dicts",
    ],
)

bzl_library(
    name = "swift_interop_hint",
    srcs = ["swift_interop_hint.bzl"],
    visibility = ["//swift:__subpackages__"],
    deps = [":swift_common"],
)

bzl_library(
    name = "swift_library",
    srcs = ["swift_library.bzl"],
    visibility = ["//swift:__subpackages__"],
    deps = [
        ":attrs",
        ":build_settings",
        ":compiling",
        ":feature_names",
        ":linking",
        ":providers",
        ":swift_common",
        ":utils",
        "@bazel_skylib//lib:dicts",
        "@bazel_skylib//lib:sets",
        "@bazel_skylib//rules:common_settings",
    ],
)

bzl_library(
    name = "swift_library_group",
    srcs = ["swift_library_group.bzl"],
    visibility = ["//swift:__subpackages__"],
    deps = [
        ":attrs",
        ":providers",
        ":swift_clang_module_aspect",
        ":swift_common",
        ":utils",
        "@bazel_skylib//lib:dicts",
    ],
)

bzl_library(
    name = "swift_module_alias",
    srcs = ["swift_module_alias.bzl"],
    visibility = ["//swift:__subpackages__"],
    deps = [
        ":compiling",
        ":derived_files",
        ":linking",
        ":providers",
        ":swift_common",
        ":utils",
        "@bazel_skylib//lib:dicts",
    ],
)

bzl_library(
    name = "swift_package_configuration",
    srcs = ["swift_package_configuration.bzl"],
    visibility = ["//swift:__subpackages__"],
    deps = [
        ":package_specs",
        ":providers",
    ],
)

bzl_library(
    name = "swift_toolchain",
    srcs = ["swift_toolchain.bzl"],
    visibility = ["//swift:__subpackages__"],
    deps = [
        ":actions",
        ":attrs",
        ":autolinking",
        ":compiling",
        ":debugging",
        ":feature_names",
        ":features",
        ":providers",
        ":toolchain_config",
        ":utils",
        "@bazel_skylib//lib:dicts",
        "@bazel_skylib//lib:partial",
        "@bazel_tools//tools/cpp:toolchain_utils.bzl",
    ],
)

bzl_library(
    name = "swift_usage_aspect",
    srcs = ["swift_usage_aspect.bzl"],
    visibility = ["//swift:__subpackages__"],
    deps = [":providers"],
)

bzl_library(
    name = "toolchain_config",
    srcs = ["toolchain_config.bzl"],
    visibility = ["//swift:__subpackages__"],
    deps = [
        "@bazel_skylib//lib:partial",
        "@bazel_skylib//lib:paths",
        "@bazel_skylib//lib:types",
    ],
)

bzl_library(
    name = "utils",
    srcs = ["utils.bzl"],
    visibility = [
        "//proto:__subpackages__",
        "//swift:__subpackages__",
    ],
    deps = ["@bazel_skylib//lib:paths"],
)

bzl_library(
    name = "xcode_swift_toolchain",
    srcs = ["xcode_swift_toolchain.bzl"],
    visibility = ["//swift:__subpackages__"],
    deps = [
        ":actions",
        ":attrs",
        ":compiling",
        ":feature_names",
        ":features",
        ":providers",
        ":toolchain_config",
        ":utils",
        "@bazel_skylib//lib:collections",
        "@bazel_skylib//lib:dicts",
        "@bazel_skylib//lib:partial",
        "@bazel_skylib//lib:paths",
        "@bazel_skylib//rules:common_settings",
        "@bazel_tools//tools/cpp:toolchain_utils.bzl",
    ],
)

# Indirection needed to prevent using `objc_library` outside of macOS
alias(
    name = "swizzle_absolute_xcttestsourcelocation",
    actual = select({
        "@build_bazel_apple_support//configs:apple": (
            "@build_bazel_apple_support//lib:swizzle_absolute_xcttestsourcelocation"
        ),
        "//conditions:default": ":dummy_swizzle_absolute_xcttestsourcelocation",
    }),
    visibility = ["//visibility:public"],
)

cc_library(
    name = "dummy_swizzle_absolute_xcttestsourcelocation",
)

# Consumed by Bazel integration tests.
filegroup(
    name = "for_bazel_tests",
    testonly = 1,
    srcs = glob(["**"]) + [
        # We should be depending on a filegroup here that represents this file
        # and its dependencies, but it doesn't exist yet.
        "@bazel_tools//tools/cpp:toolchain_utils.bzl",
        "@bazel_tools//tools/build_defs/cc:action_names_test_files",
    ],
    visibility = [
        "//swift:__pkg__",
    ],
)

bzl_library(
    name = "swift_binary_test_rules",
    srcs = ["swift_binary_test_rules.bzl"],
    visibility = ["//swift:__subpackages__"],
    deps = [
        ":compiling",
        ":derived_files",
        ":env_expansion",
        ":feature_names",
        ":linking",
        ":providers",
        ":swift_common",
        ":utils",
        "@bazel_skylib//lib:dicts",
    ],
)

bzl_library(
    name = "build_settings",
    srcs = ["build_settings.bzl"],
    visibility = ["//swift:__subpackages__"],
    deps = ["@bazel_skylib//rules:common_settings"],
)

bzl_library(
    name = "env_expansion",
    srcs = ["env_expansion.bzl"],
    visibility = ["//swift:__subpackages__"],
)

bzl_library(
    name = "explicit_module_map_file",
    srcs = ["explicit_module_map_file.bzl"],
    visibility = ["//swift:__subpackages__"],
)

bzl_library(
    name = "feature_names",
    srcs = ["feature_names.bzl"],
    visibility = ["//swift:__subpackages__"],
)

bzl_library(
    name = "package_specs",
    srcs = ["package_specs.bzl"],
    visibility = ["//swift:__subpackages__"],
)

bzl_library(
    name = "target_triples",
    srcs = ["target_triples.bzl"],
    visibility = ["//swift:__subpackages__"],
)

bzl_library(
    name = "vfsoverlay",
    srcs = ["vfsoverlay.bzl"],
    visibility = ["//swift:__subpackages__"],
)
