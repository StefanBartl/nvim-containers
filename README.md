# nvim-containers.nvim

Manage your containers (Podman, Docker, and more) directly from Neovim – with clean architecture, pluggable backends, and a TUI-native experience.

**⚠️ Alpha Version** – Breaking changes can and will happen.

---

## Features (Planned & In Progress)

- ✅ List running and stopped containers
- ✅ View logs of any container in a buffer
- ✅ Execute a shell inside a container
- 🛠️ Start/stop/remove containers
- 🛠️ Image management (list, pull, remove)
- 🛠️ Volume inspection
- 🧠 Hexagonal architecture (engine-agnostic)
- 🧩 Easily extendable (Podman, Docker, nerdctl, etc.)
- 📦 Designed for plugin managers (e.g. lazy.nvim)
- 🚫 No external Lua dependencies

---

## Installation

### lazy.nvim

```lua
{
  "StefanBartl/nvim-containers.nvim",
  config = function()
    require("containers").setup({
      engine = "podman", -- or "docker", "nerdctl"
    })
  end,
  cmd = { "ContainerList", "ContainerLogs", "ContainerExec", "ContainerStart", "ContainerStop", "ContainerKill"  }
}
```

---

## Usage

| Command | Description |
|--------|-------------|
| `:ContainerList` | List all containers (running/stopped) |
| `:ContainerLogs <id>` | Show logs for a container |
| `:ContainerExec <id>` | Execute shell inside container |
| `:ContainerStart <id>` | (Planned) Start container |
| `:ContainerStop <id>` | (Planned) Stop container |

More commands will be added soon.

---

## Supported Engines

| Engine | Status | Notes |
|--------|--------|-------|
| **Podman** | ✅ Supported | Uses `podman ps -a --format json` etc. |
| **Docker** | 🛠️ In Progress | Drop-in adapter planned |
| **nerdctl** | 🔜 Planned | |
| **containerd** | 🔜 Research phase | |

All adapters implement the same interface defined under `core/ports/container_engine.lua`.

---

## Development & Contribution

Clone this repo and symlink or add to your Neovim runtime path for local development.

### File layout
- Add new engines under `adapters/<engine>/container_engine.lua`
- Add new use cases under `core/usecases/`
- Add new commands under `plugin/containers.lua`

Pull Requests and Issues are very welcome!

---

## License

[MIT License](./LICENSE)

---

## Disclaimer

This is **alpha software**. Expect changes, rough edges, and bugs.
Your feedback will help shape the future of container management in Neovim.

---

