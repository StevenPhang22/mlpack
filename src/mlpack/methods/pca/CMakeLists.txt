# Define the files we need to compile
# Anything not in this list will not be compiled into mlpack.
set(SOURCES
  pca.hpp
  pca_impl.hpp
)

add_subdirectory(decomposition_policies)

# Add directory name to sources.
set(DIR_SRCS)
foreach(file ${SOURCES})
  set(DIR_SRCS ${DIR_SRCS} ${CMAKE_CURRENT_SOURCE_DIR}/${file})
endforeach()
# Append sources (with directory name) to list of all mlpack sources (used at
# the parent scope).
set(MLPACK_SRCS ${MLPACK_SRCS} ${DIR_SRCS} PARENT_SCOPE)

add_category(pca "transformations")
add_cli_executable(pca)
add_python_binding(pca)
add_julia_binding(pca)
add_go_binding(pca)
add_r_binding(pca)
add_markdown_docs(pca "cli;python;julia;go;r" "")
