cmake_minimum_required(VERSION 3.26)
project(vk_sdl C CXX)

set(CMAKE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_PDB_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/bin)
set(CMAKE_ARCHIVE_OUTPUT_DIRECTORY ${CMAKE_BINARY_DIR}/libs)

LINK_DIRECTORIES(${CMAKE_BINARY_DIR}/libs)

file(
    DOWNLOAD
    https://github.com/cpm-cmake/CPM.cmake/releases/download/v0.39.0/CPM.cmake
    ${CMAKE_CURRENT_BINARY_DIR}/cmake/CPM.cmake
    EXPECTED_HASH SHA256=66639bcac9dd2907b2918de466783554c1334446b9874e90d38e3778d404c2ef
)
include(${CMAKE_CURRENT_BINARY_DIR}/cmake/CPM.cmake)

#CPMAddPackage("gh:libsdl-org/SDL#6cf84e2")
# CPMAddPackage("gh:libsdl-org/SDL_image#7744158")
# CPMAddPackage("gh:libsdl-org/SDL_ttf#f9b636f")
# CPMAddPackage("gh:libsdl-org/SDL_mixer#8ab0d03")

CPMAddPackage("gh:libsdl-org/SDL#prerelease-3.1.2")
#CPMAddPackage("gh:libsdl-org/SDL_image#322b5a4ca424a8d6311bd33888953e30f8fdbe61") #fail for external aom package
CPMAddPackage("gh:libsdl-org/SDL_ttf#5af466a319fec351004279fe64a77bc8fe51b3f5")
#CPMAddPackage("gh:libsdl-org/SDL_mixer#dd8fd8547b935521d8a0bf2b4701fd1949e2f999") #fail SDL2 missing error
#CPMAddPackage("gh:libsdl-org/SDL_net#0f95bd87075951f83acce9b5b2632d298120db22")
#needed for KhronosGroup/glslang
CPMAddPackage("gh:google/googletest#v1.14.x")
# 1.3.283.0
CPMAddPackage("gh:KhronosGroup/Vulkan-Headers#vulkan-sdk-1.3.283.0")
CPMAddPackage("gh:KhronosGroup/SPIRV-Headers#vulkan-sdk-1.3.283.0")
CPMAddPackage("gh:KhronosGroup/SPIRV-Tools#vulkan-sdk-1.3.283.0")
CPMAddPackage("gh:KhronosGroup/glslang#vulkan-sdk-1.3.283.0")
# volk is a meta-loader for Vulkan
CPMAddPackage("gh:zeux/volk#vulkan-sdk-1.3.283.0")
# Easy to integrate Vulkan memory allocation library.
CPMAddPackage("gh:GPUOpen-LibrariesAndSDKs/VulkanMemoryAllocator#eaf8fc27eeadf6f21b11183651b829e897f01957")
# OpenGL Mathematics (glm) for C
CPMAddPackage("gh:recp/cglm#a93a9ef9a2282f5aba0c0bb2a4b5eaa35902fa80")
# Open Asset Import Library is a library to load various 3d file formats into a shared, in-memory format.
CPMAddPackage("gh:assimp/assimp#10df90ec144179f97803a382e4f07c0570665864")
# cimgui
CPMAddPackage("gh:cimgui/cimgui#67cf8c96b77e6729e720a376757964ff2d2e78c0")

# CPMAddPackage(
#     NAME enet
#     URL https://github.com/lsalzman/enet/archive/4ce1625b8ae22a4e0030f07d80360e25ae558a1e.zip
#     #GITHUB_REPOSITORY lsalzman/enet
#     #GIT_TAG 2a85cd6
#     #GIT_TAG v1.3.18
#     #GIT_TAG 4ce1625b8ae22a4e0030f07d80360e25ae558a1e
#     #VERSION 4ce1625b8ae22a4e0030f07d80360e25ae558a1e
#     DOWNLOAD_ONLY True
# )
CPMAddPackage("gh:lsalzman/enet#4ce1625b8ae22a4e0030f07d80360e25ae558a1e")


MESSAGE(STATUS "enet_ADDED: ${enet_ADDED}")
MESSAGE(STATUS "enet_SOURCE_DIR: ${enet_SOURCE_DIR}")
if (enet_ADDED)

  #add_library(enet)
  #include folder
  include_directories(
    "${enet_SOURCE_DIR}/include"
  )
  #include folder ???
  # target_include_directories(enet PUBLIC "${enet_SOURCE_DIR}/include")
  # target_sources(enet PRIVATE
  #   ${enet_SOURCE_DIR}/callbacks.c
  #   ${enet_SOURCE_DIR}/compress.c
  #   ${enet_SOURCE_DIR}/host.c
  #   ${enet_SOURCE_DIR}/list.c
  #   ${enet_SOURCE_DIR}/packet.c
  #   ${enet_SOURCE_DIR}/peer.c
  #   ${enet_SOURCE_DIR}/protocol.c
  #   ${enet_SOURCE_DIR}/unix.c
  #   ${enet_SOURCE_DIR}/win32.c
  # )
  set(enet_SOURCE_FILES
    ${enet_SOURCE_DIR}/callbacks.c
    ${enet_SOURCE_DIR}/compress.c
    ${enet_SOURCE_DIR}/host.c
    ${enet_SOURCE_DIR}/list.c
    ${enet_SOURCE_DIR}/packet.c
    ${enet_SOURCE_DIR}/peer.c
    ${enet_SOURCE_DIR}/protocol.c
    ${enet_SOURCE_DIR}/unix.c
    ${enet_SOURCE_DIR}/win32.c
  )

endif ()

add_library(${PROJECT_NAME} INTERFACE)
#target_link_libraries(${PROJECT_NAME} PRIVATE SDL3::SDL3)
target_link_libraries(${PROJECT_NAME} INTERFACE
Vulkan::Headers
SPIRV-Headers::SPIRV-Headers
volk::volk_headers
glslang
GPUOpen::VulkanMemoryAllocator
SDL3::SDL3
#SDL3_image::SDL3_image
#SDL3_mixer::SDL3_mixer
SDL3_ttf::SDL3_ttf
cglm
assimp::assimp
cimgui
enet
)

if (PROJECT_IS_TOP_LEVEL)
    add_executable(${PROJECT_NAME}_test test/main.c test/deps.cpp ${enet_SOURCE_FILES})
    #add_executable(${PROJECT_NAME}_test test/test.c)
    target_link_libraries(${PROJECT_NAME}_test PRIVATE ${PROJECT_NAME})
endif ()