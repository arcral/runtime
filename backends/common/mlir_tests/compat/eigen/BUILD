load("@tf_runtime//mlir_tests:lit.bzl", "glob_lit_tests")

licenses(["notice"])

package(default_visibility = ["@tf_runtime//:__subpackages__"])

exports_files([
    "conv2d.bias.benchmarks.mlir",
    "matmul.benchmarks.mlir",
    "max_pooling.benchmarks.mlir",
])

glob_lit_tests(
    data = [
        "test_data/batch_norm_f32.btf",
        "test_data/batch_norm_grad_f32.btf",
        "test_data/conv2d_batch_norm_f32.btf",
        "test_data/conv2d_bias_f32.btf",
        "test_data/conv2d_grad_filter_f32.btf",
        "test_data/conv2d_grad_input_f32.btf",
        "test_data/matmul_f32.btf",
        "test_data/matmul_i32.btf",
        "test_data/max_pooling_f32.btf",
        ":test_utilities",
    ],
    #=== GOOGLE_PIPER: tf_runtime/mlir_tests:run_lit.sh ===#
    exclude = glob(["*.benchmarks.mlir"]),
    test_file_exts = [
        "mlir",
    ],
)

# Bundle together all of the test utilities that are used by tests.
filegroup(
    name = "test_utilities",
    testonly = True,
    data = [
        "@llvm-project//llvm:FileCheck",
        #=== GOOGLE_PIPER: llvm-project/mlir:run_lit.sh ===#
        "@tf_runtime//tools:bef_executor",
        "@tf_runtime//tools:tfrt_opt",
        "@tf_runtime//tools:tfrt_translate",
    ],
)
