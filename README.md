# Sample go Bazel project

This is currently an experimental project to work with go and bazel(isk)


## Usage with Bazel

To install Bazel itself:

* [Install Bazel's dependencies](https://docs.bazel.build/install.html)
* [Install Bazelisk](https://github.com/bazelbuild/bazelisk/releases) (optional, but recommended)

## Available bazel commands

### hello world

A sample go library / binary to get to know bazel.

Run with `bazelisk run //golang/hello_world:hello_world`.

### Buildifier

A formatting tool for BUILD.bazel files.
Run with: `bazelisk run buildifier_format`

### Intellij Format

An allround code formatter which currently uses [tulip-codescheme.xml](https://github.com/TulipSolutions/tulip-bazel-tools/blob/master/rules_intellij_formatter/tulip-code-scheme.xml) which can also be loaded in intellij `File` -> `Code Style`.

Run with `bazelisk run intellij_format` to format code or `bazelisk run intellij_check` if you only want to check for formatting errors.

It is also possible to overide the schema by adding `code_scheme` in the BUILD.bazel file for more instructions see [README.md](https://github.com/TulipSolutions/tulip-bazel-tools/tree/master/rules_intellij_formatter#custom-code-schema-file-xml).

```
intellij_formatter(
    name = "intellij_format",
    code_scheme = "//mypkg/mydir:mycodescheme.xml",
)
```
### Go fmt

A go code formatting tool.

Run with: `bazelisk run gofmt_format`

### Gazelle Build file generator

Gazelle is a build file generator for more information see [bazel-gazelle](https://github.com/bazelbuild/bazel-gazelle)

Run with: `bazelisk run gazelle`

### Addlicense

A tool that adds license headers to the top of your code.

Run with: `bazelisk run addlicense_format` to add headers or `bazelisk run addlicense_check` to check if there are any headers missing.
