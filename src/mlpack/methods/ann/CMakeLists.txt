# Define the files we need to compile
# Anything not in this list will not be compiled into mlpack.
set(SOURCES
  ffn.hpp
  ffn_impl.hpp
  rnn.hpp
  rnn_impl.hpp
)

add_subdirectory(visitor)
add_subdirectory(activation_functions)
add_subdirectory(init_rules)
add_subdirectory(layer)
add_subdirectory(convolution_rules)
add_subdirectory(augmented)

# Add directory name to sources.
set(DIR_SRCS)
foreach(file ${SOURCES})
  set(DIR_SRCS ${DIR_SRCS} ${CMAKE_CURRENT_SOURCE_DIR}/${file})
endforeach()
# Append sources (with directory name) to list of all mlpack sources (used at
# the parent scope).
set(MLPACK_SRCS ${MLPACK_SRCS} ${DIR_SRCS} PARENT_SCOPE)
