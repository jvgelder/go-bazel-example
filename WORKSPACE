# RENAME to fit your workspace name
workspace(name = "com_go_bazel_example")

load("@bazel_tools//tools/build_defs/repo:http.bzl", "http_archive")
load("@bazel_tools//tools/build_defs/repo:git.bzl", "git_repository")

# We depend on tulip bazel tools for intellij format and addlicense
TULIP_BAZEL_COMMIT = "8a4051f7283540e89b4707a20012bbd8d3804eec"

http_archive(
    name = "nl_tulipsolutions_bazel_tools",
    sha256 = "93ba3c766ab8e56bf0279a5a43fb62774d6063fa74fa2d4b552d3ed6d2179ed3",
    strip_prefix = "tulip-bazel-tools-%s" % TULIP_BAZEL_COMMIT,
    url = "https://github.com/TulipSolutions/tulip-bazel-tools/archive/%s.zip" % TULIP_BAZEL_COMMIT,
)

# install go deps defined by tulip_bazel_tools
load("@nl_tulipsolutions_bazel_tools//:go-deps.bzl", "tulip_bazel_tools_go_dependencies")

tulip_bazel_tools_go_dependencies()

load("@nl_tulipsolutions_bazel_tools//:go-setup.bzl", "tulip_bazel_tools_go_setup")

tulip_bazel_tools_go_setup()

# Check Bazel version when invoked by Bazel directly instead of Bazelisk; verify it's at minimum the version Bazelisk
# would choose to use via .bazelversion file.
load("//bazel/rules_bazel_version:deps.bzl", "bazel_version_dependencies")

bazel_version_dependencies()

load("//bazel/rules_bazel_version:def.bzl", "bazel_version")

bazel_version(name = "example_bazel_version")

load("@example_bazel_version//:check.bzl", "check_bazel_version")

check_bazel_version()

load("@io_bazel_rules_go//go:deps.bzl", "go_register_toolchains", "go_rules_dependencies")

go_rules_dependencies()

go_register_toolchains()

## Formatters
load("@nl_tulipsolutions_bazel_tools//:go-deps.bzl", "tulip_bazel_tools_go_dependencies")

tulip_bazel_tools_go_dependencies()

load("@nl_tulipsolutions_bazel_tools//:go-setup.bzl", "tulip_bazel_tools_go_setup")

tulip_bazel_tools_go_setup()

load("@com_github_bazelbuild_buildtools//buildifier:deps.bzl", "buildifier_dependencies")

buildifier_dependencies()

load("@nl_tulipsolutions_bazel_tools//rules_intellij_formatter:deps.bzl", "intellij_formatter_dependencies")

intellij_formatter_dependencies()

# Be aware depends on go deps from tulip_bazel_tools_go_setup
load("@bazel_gazelle//:deps.bzl", "gazelle_dependencies", "go_repository")

gazelle_dependencies()

load("@nl_tulipsolutions_bazel_tools//rules_addlicense:deps.bzl", "addlicense_dependencies")

addlicense_dependencies()
