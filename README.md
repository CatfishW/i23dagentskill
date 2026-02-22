# Image-to-3D Agent Skill

This repository acts as a global CLI wrapper, an MCP server, and an [Agent Skill](https://skills.sh/) for converting 2D images to 3D meshes using Hunyuan3D-2.1.

**Backend API:** `https://mc.agaii.org/I23D/` (remote GPU inference - no local setup required)

## Installation for Agents (OpenCode, Cursor, etc.)

Install this skill directly into your agent's ecosystem:
```bash
npx skills add CatfishW/i23dagentskill
```

## Global CLI Installation

To use this from any terminal:
```bash
npm install -g git+https://github.com/CatfishW/i23dagentskill.git

# Then run:
i23dagentskill my-image.png -o output.glb
```

## Running as an MCP Server
```bash
npx -y github:CatfishW/i23dagentskill run mcp
```

## Environment Variables

- `I23D_API_URL` - Override the default API endpoint (default: `https://mc.agaii.org/I23D/`)
