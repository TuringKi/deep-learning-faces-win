SET(SRC_LIST   
cu_dnn_ops.cu
cu_gpu_rand.cu
cu_matrix_ops.cu
cu_util.cu
mlp.cu
cu_conv.cu
cu_jitters.cu
)  
set(CUDA_NVCC_FLAGS -Xcompiler  -use_fast_math -DNDEBUG -ftz=true -prec-div=false -prec-sqrt=false  -gencode=arch=compute_20,code="sm_20,compute_20" --ptxas-options=-v  -G -g -O0 )
CUDA_ADD_library(cudatool STATIC ${SRC_LIST})  

target_link_libraries(cudatool glew64 freeglut curand cublas)

SET(EXECUTABLE_OUTPUT_PATH ${PROJECT_BINARY_DIR}/bin)  