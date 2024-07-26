exports_files([
    "f251.h",
    "poseidon.h",
])

cc_library(
    name = "poseidon",
    srcs = select({
        "@platforms//cpu:x86_64" :[
            "f251_asm.s",
            "f251.c",
            "poseidon.c",
            "poseidon_rc.c",
        ],
        "//conditions:default": [
            "f251.c",
            "poseidon.c",
            "poseidon_rc.c",
        ]
    }),
    hdrs = [
        "f251.h",
        "poseidon.h",
        "poseidon_rc.h",
    ],
    copts = select({
        "@platforms//cpu:x86_64" :[
            "-DASSEMBLY"
        ],
        "//conditions:default": [
        ]
    }),
    visibility = ["//visibility:public"],
    tags = ["external_prover"],
)
