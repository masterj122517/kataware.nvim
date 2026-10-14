<div align="center">
  <h1>Kataware</h1>
  <p><em>A comet-lit indigo night for Neovim.</em></p>
  <p>Quiet surfaces. Spectral accents. Deliberate contrast.</p>
</div>

---

Kataware is a dark Neovim colorscheme shaped by the fleeting twilight of <em>Your Name</em> (君の名は。). Its restrained indigo luminance ladder keeps the editor calm, while cyan, violet, gold, green, and red carry meaning without competing for attention.

## Design

- A deep indigo canvas with a controlled luminance ladder
- Semantic accents for syntax, diagnostics, diffs, and focus
- Quiet indigo search backgrounds, with a slightly stronger current and incremental match
- Treesitter and LSP semantic-token coverage
- Carefully matched terminal colors
- Native transparent mode, including floating and plugin windows
- Focused integrations without runtime dependencies

## Installation

### lazy.nvim

```lua
{
  'masterj122517/kataware.nvim',
  lazy = false,
  priority = 1000,
  config = function()
    vim.cmd.colorscheme 'kataware'
  end,
}
```

### packer.nvim

```lua
use {
  'masterj122517/kataware.nvim',
  config = function()
    vim.cmd.colorscheme 'kataware'
  end,
}
```

### vim-plug

```vim
Plug 'masterj122517/kataware.nvim'
colorscheme kataware
```

### Native packages

```sh
git clone https://github.com/masterj122517/kataware.nvim \
  ~/.local/share/nvim/site/pack/kataware/start/kataware.nvim
```

Then load the colorscheme:

```lua
vim.cmd.colorscheme 'kataware'
```

## Transparency

Kataware is opaque by default. Set the option before loading the colorscheme:

```lua
vim.g.kataware_transparent = true
vim.cmd.colorscheme 'kataware'
```

With `lazy.nvim`:

```lua
{
  'masterj122517/kataware.nvim',
  lazy = false,
  priority = 1000,
  config = function()
    vim.g.kataware_transparent = true
    vim.cmd.colorscheme 'kataware'
  end,
}
```

Transparent mode covers the editor canvas, generic floating windows, Telescope, completion menus, WhichKey, sign and fold columns, window bars, and tabline fill. Selected rows, semantic highlights, diagnostics, and statuslines retain deliberate backgrounds for readability.

To switch at runtime, update the option and reload Kataware:

```lua
vim.g.kataware_transparent = not vim.g.kataware_transparent
vim.cmd.colorscheme 'kataware'
```

Optional keymap:

```lua
vim.keymap.set('n', '<leader>ut', function()
  vim.g.kataware_transparent = not vim.g.kataware_transparent
  vim.cmd.colorscheme 'kataware'
end, { desc = 'Toggle Kataware transparency' })
```

## Integrations

Kataware includes focused highlight groups for:

- Treesitter
- LSP diagnostics, references, inlay hints, and semantic tokens
- blink.cmp
- Telescope
- Snacks
- WhichKey
- lazy.nvim
- Oil
- Gitsigns
- todo-comments
- mini.statusline and mini.tabline

Plugins without dedicated groups inherit the core Neovim and floating-window palette.

## Palette

| Role | Color | Hex |
| --- | --- | --- |
| Void | Deep canvas | `#0B1020` |
| Night | Subtle depth | `#10172A` |
| Surface | Floating surface | `#151F38` |
| Surface high | Selection and focus | `#1D2A49` |
| Border | Structural edge | `#2B3B62` |
| Foreground | Primary text | `#D9E2F2` |
| Comet | Cyan focus | `#60D7E8` |
| Blue | Functions and information | `#6CA8FF` |
| Violet | Keywords and structure | `#9B8CFF` |
| Pink | Special forms | `#F08BC3` |
| Gold | Constants and warnings | `#F2C38B` |
| Green | Strings and additions | `#82D2B2` |
| Red | Errors and removals | `#F2778B` |

## Development

Run the behavioral regression test with Neovim itself:

```sh
nvim --headless -u NONE -l tests/transparent.lua
```

The test exercises both opaque and transparent modes through the public colorscheme interface, including Telescope and generic floating-window backgrounds.

## License

Kataware is available under the [MIT License](LICENSE).
