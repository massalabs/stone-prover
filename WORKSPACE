load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

git_repository(
    name = "com_github_gflags_gflags",
    commit = "986e8eed00ded8168ef4eaa6f925dc6be50b40fa",
    patches = ["//src/third_party:gflags.patch"],
    remote = "https://github.com/gflags/gflags.git",
    shallow_since = "1641684284 +0000",
)

git_repository(
    name = "com_github_glog_glog",
    commit = "96a2f23dca4cc7180821ca5f32e526314395d26a",
    patches = ["//src/third_party:glog.patch"],
    remote = "https://github.com/google/glog.git",
    shallow_since = "1553223106 +0900",
    # tag = "v0.4.0",
)

git_repository(
    name = "com_github_gtest_gtest",
    # commit = "703bd9caab50b139428cea1aaff9974ebee5742e",
    remote = "https://github.com/google/googletest.git",
    # shallow_since = "1570114335 -0400",
    tag = "v1.15.0",
)

http_archive(
    name = "toolchains_llvm",
    sha256 = "e91c4361f99011a54814e1afbe5c436e0d329871146a3cd58c23a2b4afb50737",
    strip_prefix = "toolchains_llvm-1.0.0",
    canonical_id = "1.0.0",
    url = "https://github.com/bazel-contrib/toolchains_llvm/releases/download/1.0.0/toolchains_llvm-1.0.0.tar.gz",
)

load("@toolchains_llvm//toolchain:deps.bzl", "bazel_toolchain_dependencies")

bazel_toolchain_dependencies()

load("@toolchains_llvm//toolchain:rules.bzl", "llvm_toolchain")

llvm_toolchain(
    name = "llvm_toolchain",
    compile_flags = {
        "": [
            "-DUSE_REGISTER_HINT",
            "-fno-omit-frame-pointer",
            "-fno-strict-aliasing",
            "-fPIC",
            "-Isrc",
            "-maes",
            "-mpclmul",
            "-Wall",
            "-Wextra",
            "-Wno-mismatched-tags",
            "-DBACKWARD_HAS_DW=0",
        ],
    },
    cxx_flags = {
        "": [
            "-std=c++17",
            "-fconstexpr-steps=20000000",
        ],
    },
    link_flags = {
        "": [
            "-fuse-ld=gold",
            "-Wl,-no-as-needed",
            "-Wl,-z,relro,-z,now",
            "-B/usr/bin",
            "-lstdc++",
            "-lm",
        ],
    },
    llvm_version = "17.0.6",
    opt_compile_flags = {
        "": [
            "-g0",
            "-O3",
            "-D_FORTIFY_SOURCE=1",
            "-DNDEBUG",
            "-ffunction-sections",
            "-fdata-sections",
        ],
    },
    stdlib = {"": "stdc++"},
)

load("@llvm_toolchain//:toolchains.bzl", "llvm_register_toolchains")

llvm_register_toolchains()
