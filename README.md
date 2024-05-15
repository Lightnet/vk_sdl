# vk_sdl
Vulkan Dev Starter Pack with SDL3, CMake, C23 and more!
 - https://www.youtube.com/watch?v=WLjuV9_fQfw
 - https://github.com/ilyas-taouaou/vk_sdl

# Information:
 SDL3 current unstable. 
 
 Note some default support packages are not working yet.

 Vulkan not stable. There are api changes.

 This is for C build and not C++.

# CPM.cmake:
```
file(
        DOWNLOAD
        https://github.com/cpm-cmake/CPM.cmake/releases/download/v0.39.0/CPM.cmake
        ${CMAKE_CURRENT_BINARY_DIR}/cmake/CPM.cmake
        EXPECTED_HASH SHA256=66639bcac9dd2907b2918de466783554c1334446b9874e90d38e3778d404c2ef
)
```

# Packages github:
 - libsdl-org/SDL (pass) prerelease-3.1.2
 - libsdl-org/SDL_image main (Fail) #a34ccf16f961e6d5a480045eb650fc3dddb4bfaa
 - libsdl-org/SDL_ttf main #5af466a319fec351004279fe64a77bc8fe51b3f5
 - libsdl-org/SDL_mixer main #2f939d24d98bc2730bd2ad2aebfee4d9f8b4cf19
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
 - lsalzman/enet (fail) v1.3.18
 - 
 
 Note simple compile check fail build.

# Refs:
 - https://stackoverflow.com/questions/33380020/errorcould-not-find-pkgconfig-missing-pkg-config-executable
 - https://www.reddit.com/r/cmake/comments/otxfb4/cmake_finds_the_python_interpreter_yet_says_it/

# packages for windows:
install scoop for easy package manager.
```
pkg-config
python
```
Note if you have security program. You will get python error.