# vk_sdl
Vulkan Dev Starter Pack with SDL3, CMake, C23 and more!
 - https://www.youtube.com/watch?v=WLjuV9_fQfw
 - https://github.com/ilyas-taouaou/vk_sdl

# Information:
 SDL3 current unstable. Note that this is just a test build.

 This is for testing the Vulkan. Current testing the C lang build.

 But it can be work for c++.

# CPM.cmake:
```
file(
  DOWNLOAD
  https://github.com/cpm-cmake/CPM.cmake/releases/download/v0.39.0/CPM.cmake
  ${CMAKE_CURRENT_BINARY_DIR}/cmake/CPM.cmake
  EXPECTED_HASH SHA256=66639bcac9dd2907b2918de466783554c1334446b9874e90d38e3778d404c2ef
)
```
  This is package manager.

  Note that few packages does not have cmake or just helper repo.

# Required Tool Programs:
  Install scoop for easy package manager.

 - pkg-config
 - python 3.12
 - nasm (SDL_Image)
 - perl (SDL_Image)

 Those are required for SDL_"Name" and vulkan libs.

## nasm:
 - For sdl_image
## python:
 - For vulkan (I might be wrong.)

 Those are need for SDL to work with other packages.

# Packages github:
 - libsdl-org/SDL (pass) prerelease-3.1.2
 - libsdl-org/SDL_image (fail) main #322b5a4ca424a8d6311bd33888953e30f8fdbe61
 - libsdl-org/SDL_ttf main #5af466a319fec351004279fe64a77bc8fe51b3f5
 - libsdl-org/SDL_mixer main (fail) #2f939d24d98bc2730bd2ad2aebfee4d9f8b4cf19
 - libsdl-org/SDL_net main (not tested) #0f95bd87075951f83acce9b5b2632d298120db22
 - 
 - google/googletest #v1.14.x
 - KhronosGroup/Vulkan-Headers #vulkan-sdk-1.3.283.0
 - KhronosGroup/SPIRV-Headers #vulkan-sdk-1.3.283.0
 - KhronosGroup/SPIRV-Tools #vulkan-sdk-1.3.283.0
 - KhronosGroup/glslang #vulkan-sdk-1.3.283.0
 - zeux/volk #vulkan-sdk-1.3.283.0
 - 
 - GPUOpen-LibrariesAndSDKs/VulkanMemoryAllocator main #eaf8fc27eeadf6f21b11183651b829e897f01957
 - recp/cglm main #a93a9ef9a2282f5aba0c0bb2a4b5eaa35902fa80
 - assimp/assimp main #10df90ec144179f97803a382e4f07c0570665864
 - cimgui/cimgui main #67cf8c96b77e6729e720a376757964ff2d2e78c0
 - 
 - lsalzman/enet main 4ce1625b8ae22a4e0030f07d80360e25ae558a1e
 - 
 
 Note simple compile check fail build.
# Fail build:
 - SDL_image (required some toolchain) path SDL2 is default
 - SDL_mixer (required some toolchain)

# Refs:
 - https://stackoverflow.com/questions/33380020/errorcould-not-find-pkgconfig-missing-pkg-config-executable
 - https://www.reddit.com/r/cmake/comments/otxfb4/cmake_finds_the_python_interpreter_yet_says_it/

# Packages and Programs Windows:

```
pkg-config
python
```
## Note: 
 - If you have security program. You will get python error.