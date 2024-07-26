cc_library(
    name = "Keccak1600F",
    visibility = ['//visibility:public'],
    srcs = select({
        "@platforms//cpu:x86_64" : ["KeccakP-1600-AVX2.s"],
        "@platforms//cpu:arm64" : ["KeccakP-1600-armv8a-neon.s"],
    }),
    copts = ["-Wno-unused-command-line-argument"],
    tags = ["external_prover"],
)
