cc_library(
    name = "backward-cpp",
    hdrs = [
        "backward.hpp",
    ],
    visibility = ["//visibility:public"],
    linkopts = select({
        "@platforms//cpu:x86_64": [
            "-ldw"
        ],
        "//conditions:default": []
    }),
)
