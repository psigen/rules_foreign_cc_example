load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")
load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")

################################################
# Import "rules_foreign_cc".

# Group the sources of the library so that CMake rule have access to it
all_content = """filegroup(name = "all", srcs = glob(["**"]), visibility = ["//visibility:public"])"""

git_repository(
    name = "rules_foreign_cc",
    remote = "https://github.com/bazelbuild/rules_foreign_cc.git",
    commit = "5511d9e1fe7219075ea8191298808c654974c6ac",
)

load("@rules_foreign_cc//:workspace_definitions.bzl", "rules_foreign_cc_dependencies")

# Workspace initialization function; includes repositories needed by rules_foreign_cc,
# and creates some utilities for the host operating system
rules_foreign_cc_dependencies()

################################################
# Import build rules for Boost
http_archive(
    name = "boost",
    build_file_content = all_content,
    strip_prefix = "boost_1_68_0",
    sha256 = "da3411ea45622579d419bfda66f45cd0f8c32a181d84adfa936f5688388995cf",
    urls = ["https://dl.bintray.com/boostorg/release/1.68.0/source/boost_1_68_0.tar.gz"],
)
