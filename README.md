# CPM.list

## Image processing

### HappySeaFox/sail

```cmake
CPMAddPackage(
  GITHUB_REPOSITORY HappySeaFox/sail
  VERSION 0.9.0-pre20
  OPTIONS
    "SAIL_BUILD_APPS OFF"
    "SAIL_BUILD_EXAMPLES OFF"
    "SAIL_BUILD_TESTS OFF"
    "SAIL_COMBINE_CODECS ON"
    "SAIL_THIRD_PARTY_CODECS_PATH OFF"
)
if (sail_ADDED)
  target_compile_definitions(sail-c++ INTERFACE SAIL_BUILD=1)
  target_include_directories(sail-c++ PUBLIC $<BUILD_INTERFACE:${sail_BINARY_DIR}/include>)
endif()
```

## GUI

### mitsuba-renderer/nanogui

```cmake
CPMAddPackage(
  GITHUB_REPOSITORY mitsuba-renderer/nanogui
  GIT_TAG master
  OPTIONS
    "NANOGUI_BUILD_EXAMPLES OFF"
    "NANOGUI_BUILD_PYTHON OFF"
    "NANOGUI_BUILD_SHARED ${BUILD_SHARED_LIBS}"
)
```

### cnjinhao/nana

```cmake
CPMAddPackage(
  GITHUB_REPOSITORY cnjinhao/nana
  GIT_TAG develop-1.8
  GIT_SHALLOW True
)
if (nana_ADDED)
  find_package(X11 REQUIRED COMPONENTS Xft Xcursor)
  target_link_libraries(nana PUBLIC ${X11_Xcursor_LIB})
endif()
```

## Serialization

### fraillt/bitsery

```cmake
CPMAddPackage(
  GITHUB_REPOSITORY fraillt/bitsery
  VERSION 5.2.2
  DOWNLOAD_ONLY True
)
if(bitsery_ADDED)
  add_library(bitsery INTERFACE IMPORTED)
  target_include_directories(bitsery INTERFACE "${bitsery_SOURCE_DIR}/include")
endif()
```

## Tests

### catchorg/Catch2

```cmake
CPMAddPackage("gh:catchorg/Catch2@2.13.7")
if (Catch2_ADDED)
  list(APPEND CMAKE_MODULE_PATH "${Catch2_SOURCE_DIR}/contrib")
endif()
```
