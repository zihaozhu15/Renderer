# Renderer

[English](./Readme.md) | [简体中文](./Readme.zh.md)

## Environment

- Operating System: `Windows 10`
- Compiler: `MSVC(Visual Studio 2019)`
- `OpenGL 3.3` or higher
- `CMake 3.18` or higher

## Compilation

1. Open the folder where `./code` is located -> Right Click -> Open with `Visual Studio`
2. Project -> Generate CMake Cache
3. Build -> Rebuild All
4. Select Startup Item


## Write new rendering algorithm

This project uses a simple plugin registration system.

1. Open the `./code/components` folder
2. Copy the `RenderExample` folder and rename it to your preferred name
3. Modify the `CMakeLists.txt` file in the copied folder
   ```CMake
   ...
   # Change "RenderExample" to your preferred name, ensuring it does not duplicate other folder names
   set(MY_COMPONENT_NAME "MyCustomRenderer")
   ...
   ```
4. Modify `./code/components/CMakeLists.txt`

   ```CMake

   ...
   # Add
   add_subdirectory("./MyFolder")
   ```

5. Inherit from the class `NRenderer::RenderComponent`, and override the `void render(...)`
   ```C++
   class Adapter : public NRenderer::RenderComponent {
       virtual void render(NRenderer::SharedScene spScene) {
           ....
       }
   };
   ```
6. Register
   ```C++
    // Parameter 1 -> Plugin name (Do not use non-ASCII characters)
    // Parameter 2 -> Plugin description
    // Parameter 3 -> The registered class name
    REGISTER_RENDERER(Render, RenderTest, Adapter);
   ```
7. Regenerate the CMake cache and recompile the plugin

## Usage

### Import Scene File

![](./doc/image/rdm_4.png)

### Modify Material Information

![](./doc/image/rdm_5.png)

### Modify Scene Parameters

![](doc/image/rdm_6.png)

### Select Rendering Method and Render

![](./doc/image/rdm_7.png)

### Switch Rendering Results / Fast Preview

![](./doc/image/rdm_8.png)

## Example Algorithms

### Ray Cast

![](doc/image/rdm_9.png)

### Simple Path Tracer

![](./doc/image/rdm_10.png)

### Path Tracing 

![](./doc/image/rdm_11.png)

### Path Tracing


![](./doc/image/rdm_12.png)

### Path Tracing (Enviroment Map)

![](./doc/image/rdm_13.png)

### Photon Mapping

![](./doc/image/23.png)
![](./doc/image/5.png)
