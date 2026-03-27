# SDF font atlas generation tool

Forked from [astiopin/sdf_atlas](https://github.com/astiopin/sdf_atlas).

Main changes:
- <s>GLEW</s> ➡️ [GLAD](https://github.com/Dav1dde/glad/)
- Atlas description in (now valid) `.json` file instead of `.js`

---

Atlas generation tool for the [font rendering demo](https://github.com/astiopin/webgl_fonts).

The algorithm described [here](https://astiopin.github.io/2019/01/06/sdf-on-gpu.html).

Mostly for educational purposes since the algorithm is performant enough for generating font atlases at runtime.

# How to Use

1. Clone the repository:
   ```bash
   git clone https://github.com/fegemo/sdf-atlas.git
   ```
1. Install the dependency (GLFW):
   - On Ubuntu:
     ```bash
     sudo apt install libglfw3 libglfw3-dev
     ```
   - On Windows, [download](https://www.glfw.org/download) and follow the 
     instructions
1. Build it using Make:
   ```bash
   make
   ```
   - A `bin/sdf_atlas` executable should have been generated
1. Run it on the command line:
   ```bash
   ./bin/sdf_atlas -f font_file.ttf [options]
   Options:
       -h              this help
       -o 'filename'   output file name (without extension)
       -tw 'size'      atlas image width in pixels, default 1024
       -th 'size'      atlas image height in pixels (optional)
       -ur 'ranges'    unicode ranges 'start1:end1,start:end2,single_codepoint' without spaces,
                       default: 31:126,0xffff
       -bs 'size'      SDF distance in pixels, default 16
       -rh 'size'      row height in pixels (without SDF border), default 96
   Example:
       sdf_atlas -f Roboto-Regular.ttf -o roboto -tw 2048 -ur 31:255
   ```