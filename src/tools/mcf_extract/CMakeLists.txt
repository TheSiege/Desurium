include_directories(
  ${CMAKE_CURRENT_SOURCE_DIR}/code
)

file(GLOB Sources code/*.cpp )

if(UNIX)
  set(LINUX_LIBRARIES dl)
endif()

add_executable(mcf_extract ${Sources})
target_link_libraries(mcf_extract
  mcfcore
  ${OPENSSL_LIBRARIES}
  ${LINUX_LIBRARIES}
)

install(TARGETS mcf_extract
        DESTINATION "${BIN_INSTALL_DIR}")
