# Image-to-3D Agent Skill

This repository acts as a global CLI wrapper, an MCP server, and an [Agent Skill](https://skills.sh/) for converting 2D images to 3D meshes using Hunyuan3D-2.1.

## Default Backend
- **Local:** `http://localhost:23555/I23D/` (when running backend locally)
- **Remote:** `https://mc.agaii.org/I23D/` (when using remote GPU server)

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

- `I23D_API_URL` - Override the default API endpoint (default: `http://localhost:23555/I23D`)

## API Endpoints

The backend exposes the following endpoints:
- `POST /I23D/api/send` - Start async generation
- `GET /I23D/api/status/{uid}` - Check generation status
- `GET /I23D/api/health` - Health check
