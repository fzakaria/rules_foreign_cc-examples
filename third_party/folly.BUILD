load("@rules_foreign_cc//foreign_cc:defs.bzl", "cmake")

filegroup(
    name = "all_srcs",
    srcs = glob(["**"]),
    visibility = ["//visibility:public"],
)


cmake(
    name = "folly",
    cache_entries = {
        "CMAKE_C_FLAGS": "-fPIC",
        "BOOST_ROOT": "$$EXT_BUILD_DEPS", 
        "Boost_USE_STATIC_LIBS": "ON",
        "Boost_CONTEXT_LIBRARY_RELEASE": "$$EXT_BUILD_DEPS/lib/libboost.context.a",
        "Boost_THREAD_LIBRARY_RELEASE": "$$EXT_BUILD_DEPS/lib/libboost.thread.a",
        "Boost_SYSTEM_LIBRARY_RELEASE": "$$EXT_BUILD_DEPS/lib/libboost.system.a",
        "Boost_FILESYSTEM_LIBRARY_RELEASE": "$$EXT_BUILD_DEPS/lib/libboost.filesystem.a",
        "Boost_REGEX_LIBRARY_RELEASE": "$$EXT_BUILD_DEPS/lib/libboost.regex.a",
        "Boost_PROGRAM_OPTIONS_LIBRARY_RELEASE": "$$EXT_BUILD_DEPS/lib/libboost.program_options.a",
        # 
        "DOUBLE_CONVERSION_INCLUDE_DIR": "$$EXT_BUILD_DEPS/include",
        "DOUBLE_CONVERSION_LIBRARY": "$$EXT_BUILD_DEPS/lib/libdouble-conversion.a",
        #
        "LIBEVENT_INCLUDE_DIR": "$$EXT_BUILD_DEPS/include",
        "LIBEVENT_LIB": "$$EXT_BUILD_DEPS/lib/libevent_core.a",
        
    },
    generate_args = [
        "-DBUILD_SHARED_LIBS=OFF",
        "-Wno-dev",
    ],
    lib_source = ":all_srcs",
    out_static_libs = ["libfolly.a"],
    deps = [
        "@boost.smart_ptr",
        "@boost.filesystem",
        "@boost.system",
        "@boost.regex",
        "@boost.thread",
        "@boost.context",
        "@boost.program_options",
        "@double-conversion",
        "@fast_float",
        "@libevent//:event",
        "@openssl//:crypto",
    ],
)