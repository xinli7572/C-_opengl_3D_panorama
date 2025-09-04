
# 🎥 OpenGL Fisheye Image to Panorama Viewer

https://github.com/user-attachments/assets/9279a246-a038-47ab-ac65-9703b7ede418

A simple OpenGL-based tool that maps fisheye camera images onto a spherical surface for interactive panoramic viewing — foundational for building real-time 360° surveillance systems.

---

## 🌐 Project Overview

This project demonstrates how to:
- Load a fisheye image (from a camera or file),
- Map the image onto the inner surface of a 3D sphere,
- Allow the user to look around freely using mouse control,
- Simulate a 360-degree panoramic viewer in OpenGL.

This forms the core idea for developing **real-time panoramic monitoring systems** using fisheye cameras.

---

## 🖥️ Preview

> _Imagine looking from the inside of a textured sphere — the fisheye image is projected on the inner surface, and you control the view direction using your mouse._

---

## 📦 Dependencies & Installation

Install the following packages on Ubuntu:

```bash
sudo apt-get update
sudo apt-get install build-essential libgl1-mesa-dev
sudo apt-get install libglew-dev libsdl2-dev libsdl2-image-dev libglm-dev libfreetype6-dev
sudo apt-get install libglfw3-dev libglfw3
sudo apt-get install libsoil-dev libassimp-dev libxinerama-dev libxcursor-dev libxi-dev
sudo apt-get install freeglut3-dev xorg-dev
```

## 📁 Project Structure
```
.
├── main.cpp               # Main OpenGL logic
├── vertex_shader.vs       # Vertex shader (optional)
├── fragment_shader.fs     # Fragment shader (optional)
├── shaders/               # Directory for shader files (if needed)
├── resources/
│   └── fisheye.jpg        # Sample fisheye image
├── CMakeLists.txt         # Optional: For CMake-based builds
└── README.md              # You're reading this!
```

## 🧠 Key Concepts Explained
## 🎯 Camera Orientation
```
glm::vec3 cameraPos   = glm::vec3(0.0f, 0.0f, 0.0f);  // Camera at the center of the sphere
glm::vec3 cameraFront = glm::vec3(1.0f, 0.0f, 0.0f);  // Looking along positive X-axis
glm::vec3 cameraUp    = glm::vec3(0.0f, 0.0f, -1.0f); // Negative Z is up
```

## 🌐 Sphere Vertex Generation

```
for (int y = 0; y <= Y_SEGMENTS; ++y)
{
    for (int x = 0; x <= X_SEGMENTS; ++x)
    {
        float xSegment = (float)x / X_SEGMENTS;
        float ySegment = (float)y / Y_SEGMENTS;

        float xPos = cos(xSegment * 2.0f * PI) * sin(ySegment * PI);
        float yPos = cos(ySegment * PI);
        float zPos = sin(xSegment * 2.0f * PI) * sin(ySegment * PI);

        vertices.push_back(xPos);
        vertices.push_back(yPos);
        vertices.push_back(zPos);

        vertices.push_back((-yPos + 1) / 2);
        vertices.push_back((zPos + 1) / 2);
    }
}
```

The sphere is subdivided into X_SEGMENTS * Y_SEGMENTS faces.

Texture coordinates are mapped from 3D positions to 2D using a custom projection.

## 🖱️ Mouse-Based Camera Control

```
float yaw, pitch;
front.x = cos(glm::radians(yaw));
front.y = sin(glm::radians(yaw));
front.z = cos(glm::radians(pitch));
cameraFront = glm::normalize(front);
```

## 🧪 How to Run

Compile using your favorite compiler or CMake.

Ensure image path is correct in your code:
```
loadTexture("/path/to/fisheye.jpg");
```

Run the application:
```
./panorama_viewer
```

Move your mouse to look around.

## 📸 Example Output
```
A 360-degree wrapped environment simulating a dome view, with the fisheye image correctly texture-mapped onto a sphere.
```
## ✅ TODO (Optional Enhancements)

 Live camera feed using OpenCV

 Fisheye distortion correction

 Touch or keyboard input for navigation

 CMake build system support

 GUI for switching between images or cameras

## 🧠 License

This project is for educational and research purposes. MIT-style license applies for personal use.

