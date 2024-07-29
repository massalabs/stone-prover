exports_files([
    "blake2-impl.h",
    "blake2.h",
])

cc_library(
    name = "blake2s",
    srcs = select({
        "@platforms//cpu:x86_64": [
            "blake2s.c",
        ],
        "//conditions:default": [
            "blake2s-ref.c",
        ],
    }),
    hdrs = select({
        "@platforms//cpu:x86_64": [
            "blake2.h",
            "blake2-config.h",
            "blake2-impl.h",
            "blake2s-load-sse2.h",
            "blake2s-round.h",
        ],
        "//conditions:default": [
            "blake2.h",
            "blake2-impl.h",
        ]
    }),
    visibility = ["//visibility:public"],
    tags = ["external_prover"],
    deps = [
    ],
)

package(default_visibility = ["//visibility:public"])

cc_library(
    name = "blake2",
    srcs = [
    ],
    hdrs = select({
        "@platforms//cpu:x86_64" :[
            "blake2.h",
            "blake2-config.h",
            "blake2-impl.h",
            "blake2b-load-sse2.h",
            "blake2b-load-sse41.h",
            "blake2b-round.h",
            "blake2s-load-sse2.h",
            "blake2s-load-sse41.h",
            "blake2s-load-xop.h",
            "blake2s-round.h",
        ],
        "//conditions:default": [
            "blake2.h",
            "blake2-impl.h",
        ]
    }),
    visibility = ["//visibility:public"],
    deps = [
    ],
)
