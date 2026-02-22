---
name: image-to-3d
description: Converts 2D images into 3D models (.glb/.obj) using Hunyuan3D-2.1. Use this skill when the user explicitly asks to generate or create a 3D asset from a picture.
license: MIT
metadata:
  author: CatfishW
  version: "1.0.0"
---

# Image to 3D Agent Skill

This skill allows you (the AI agent) to convert 2D images into 3D meshes with PBR textures. It hosted 3D generation service is powered by Hunyuan3D-2.1.

## When to use
Use this skill when the user explicitly asks to generate, create, or build a 3D asset, model, or mesh from a 2D image or picture.

## How to Execute

You have two ways to interact with this skill. Since the code is located in the same directory as this file, you can run the the scripts directly:

### Option 1: CLI Wrapper (Terminal)
You can execute the Node.js CLI script directly:
```bash
# Generate a 3D model with background removal and textures (default)
node ./bin/cli.js /path/to/input.png -o /path/to/output.glb

# Disable background removal and textures (faster)
node ./bin/cli.js /path/to/input.png -o /path/to/output.glb --no-bg --no-texture
```
*Note: The CLI connects to a remote GPU backend at `https://mc.agaii.org/I23D/`. Generation takes 1-3 minutes. Do not interrupt it.*

### Option 2: Model Context Protocol (MCP) Server
If your agent framework supports MCP, you can connect to the server by executing:
```bash
node ./mcp.js
```
This will expose the following tools to you over stdio:
1. `check_server_status`: Verify the remote backend is reachable.
2. `generate_3d_model`: Takes an `imagePath` and an `outputPath`. Returns success or semantic error messages.

## Important Rules & Constraints
1. **Remote Backend:** This skill connects to a remote GPU inference server at `https://mc.agaii.org/I23D/`. No local setup required.
2. **Patience:** 3D generation is computationally heavy. Expect 60 seconds to 3 minutes per model.
3. **Format:** Only `.glb` (glTF binary) format is officially supported for the output.
4. **Input Constraints:** The image should ideally feature a single, clear subject in the center. While the tool attempts background removal automatically, highly cluttered images might fail.
