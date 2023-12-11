# ci-template.nvim

<p align="center">
<a href="https://github.com/neovim/neovim/releases/v0.7.0"><img alt="Neovim" src="https://img.shields.io/badge/Neovim-v0.7+-57A143?logo=neovim&logoColor=57A143" /></a>
<a href="https://luarocks.org/modules/linrongbin16/linrongbin16-ci-template.nvim"><img alt="luarocks" src="https://custom-icon-badges.demolab.com/luarocks/v/linrongbin16/linrongbin16-ci-template.nvim?label=LuaRocks&labelColor=063B70&logo=tag&logoColor=fff&color=008B8B" /></a>
<a href="https://github.com/linrongbin16/ci-template.nvim/actions/workflows/ci.yml"><img alt="ci.yml" src="https://img.shields.io/github/actions/workflow/status/linrongbin16/ci-template.nvim/ci.yml?label=GitHub%20CI&labelColor=181717&logo=github&logoColor=fff" /></a>
<a href="https://app.codecov.io/github/linrongbin16/ci-template.nvim"><img alt="codecov" src="https://img.shields.io/codecov/c/github/linrongbin16/ci-template.nvim?logo=codecov&logoColor=F01F7A&label=Codecov" /></a>
</p>

<p align="center"><i>
CI template for Neovim plugin project.
</i></p>

## Table of Contents

- [Requirements](#requirements)
- [Actions](#actions)
- [Documents](#documents)
- [Usage](#usage)
  - [Initialize](#initialize)
  - [Development](#development)

## Requirements

- [CodeCov](https://about.codecov.io/) token: upload CodeCov report.
- [LuaRocks](https://luarocks.org/) API token: upload LuaRocks package.

## Actions

It runs the following actions:

For PR branch:

1. conventional PR commits check
2. luacheck
3. LuaLs annotations typecheck
4. stylua code format
5. download and install json.lua as an embed json library (for low-version Neovim).
6. run vusted (busted) unit tests for 3 version of Neovim: minimal required (0.7+), stable and nightly.

Additionally for main branch:

1. release-please
2. upload luarocks package (only for created tags)

## Documents

It provides 4 badges for README.md:

1. Minimal required Neovim version.
1. LuaRocks package version.
1. GitHub CI running status.
1. Code coverage.

## Usage

### Initialize

1. Copy this project (exclude the `.git`) to your Neovim plugin project.
   - **Note**: I'm not sure if you can completely remove the `CHANGELOG.md` file from git history if create new project via the **_Use this template_** button.
2. Remove the [CHANGELOG.md](https://github.com/linrongbin16/ci-template.nvim/blob/8ba994d7a64c52bb3a4a046068a510f54219aacd/CHANGELOG.md?plain=1#L1) (it's only for **_this_** project, you don't want it).
3. Replace the word `linrongbin16` with your name in below files:
   - `README.md`: [badges](https://github.com/linrongbin16/ci-template.nvim/blob/9313f7927b133abe342ee4fa1758fb438c6a9c57/README.md?plain=1#L4-L7).
   - `LICENSE`: [copyright](https://github.com/linrongbin16/ci-template.nvim/blob/9313f7927b133abe342ee4fa1758fb438c6a9c57/LICENSE?plain=1#L3).
   - `ci.yml`: [luarocks](https://github.com/linrongbin16/ci-template.nvim/blob/d4a39cecc5384884d2c1d9d205d3503ab266ec21/.github/workflows/ci.yml?plain=1#L122).
4. Replace the word `ci-template` with your plugin name in below files:
   - `ci.yml`: [luarocks](https://github.com/linrongbin16/ci-template.nvim/blob/d4a39cecc5384884d2c1d9d205d3503ab266ec21/.github/workflows/ci.yml?plain=1#L122).
   - `.luacov`: [modules](https://github.com/linrongbin16/ci-template.nvim/blob/792fcc25184f0ac3f20c2037ed6a4ae48f4c28d3/.luacov?plain=1#L2-L3).
   - [ci-template.lua](https://github.com/linrongbin16/ci-template.nvim/blob/203b21999ccd1e43a7e3d5d26e690ff75aeee403/lua/ci-template.lua?plain=1#L1): replace the file name with your plugin name.
   - [ci_template_spec.lua](https://github.com/linrongbin16/ci-template.nvim/blob/203b21999ccd1e43a7e3d5d26e690ff75aeee403/test/ci_template_spec.lua?plain=1#L1): replace the file name with relate lua module name.
5. Reset the version with your project version in below files:
   - `version.txt`: [version number](https://github.com/linrongbin16/ci-template.nvim/blob/792fcc25184f0ac3f20c2037ed6a4ae48f4c28d3/version.txt?plain=1#L1).
6. Update the indent size (by default 2) with your project configs in below files:
   - `.editorconfig`: [indent_size](https://github.com/linrongbin16/ci-template.nvim/blob/7de9e40f84d53d9d07d3206e4979347a942cbd30/.editorconfig?plain=1#L7).
   - `.stylua.toml`: [indent_size](https://github.com/linrongbin16/ci-template.nvim/blob/792fcc25184f0ac3f20c2037ed6a4ae48f4c28d3/.stylua.toml?plain=1#L4).

### Development

Setup the plugin development environment with:

- [lua-language-server](https://github.com/LuaLS/lua-language-server).
- [stylua](https://github.com/JohnnyMorganz/StyLua).
- [luacheck](https://github.com/lunarmodules/luacheck).
- [luarocks](https://luarocks.org/).
- [vusted](https://github.com/notomo/vusted).
