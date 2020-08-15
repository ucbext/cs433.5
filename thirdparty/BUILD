package(default_visibility = ["//visibility:public"])

sh_library(
    name = "bashunit",
    srcs = ["shell/unittest.bash"],
    data = ["shell/testenv.sh"],
)

py_binary(
    name = "format-python",
    srcs = glob(["format/yapf/**/*.py"]),
    imports = ["format/yapf"],
    main = "__main__.py",
)
