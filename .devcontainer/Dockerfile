# SPDX-License-Identifier: MIT
# © 2026 Hannes Stauss (scalarion@nimblescape.com)
# Licensed under the MIT License. See LICENSE in the repository root for details.

# devcontainer-classroom-web: the base image with the HTML validator and
# classroom VS Code settings. Everything else comes from devcontainer-base
# (core, go, node, deno, prettier). The settings are in devcontainer.json.
#
# The layer tool devcon of devcontainer-core installs every layer.
# Layers and their arguments: https://github.com/majikmate/devcontainer-core/blob/main/docs/layers.md
FROM ghcr.io/majikmate/devcontainer-base:2

# html-validate: VS Code extension HTML-validate (offline HTML5 validator) and
# the global configuration /.htmlvalidate.json, which fits Prettier
RUN devcon install html-validate
