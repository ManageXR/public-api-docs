# ManageXR API Docs via [Mintlify](https://mintlify.com/)

Learn how to set up the ManageXR public API documentation repo on your machine and best practices for updating our external API docs.

## Getting Started

Install the [Mintlify CLI](https://www.npmjs.com/package/mintlify) to preview the documentation changes locally. Use the same level of Node as the mighty-api repo (e.g., 20.11.1). To install mintlify tools, use the following command:

```
npm i -g mintlify
```

Run the following command at the root of your documentation (where `docs.json` is):

```
mintlify dev
```

To view it on a port other than 3000, use a flag (e.g.,):

```
mintlify dev --port 3333
```

### Troubleshooting

- **Mintlify dev isn't running** - Run `mintlify install` to re-install dependencies.
- **Page loads as a 404** - Make sure you are running in a folder with `docs.json`.

## Adding Endpoints to the API Reference

The API Reference contains all of the information about the ManageXR Public API. To add a new endpoint, make the following changes:

1. **Update `openapi.yaml`** to include info about the endpoint. Format according to OpenAPI 3.1.0 specifications.
2. **Create an MDX file** within `api-reference/endpoint`. Include a title and an OpenAPI URL. See existing examples in the directory. It is important that the OpenAPI URL matches the `openapi.yaml` specification for the endpoint. Mintlify also has options to [generate these automatically](https://mintlify.com/docs/api-playground/openapi/setup#autogenerate-files-recommended).
3. **Update `docs.json`** to include the endpoint MDX page in the documentation. Place the file in the appropriate group (e.g., if it is an endpoint for devices, put it in the "Devices" group). If it is an endpoint for a group that does not exist, create a new group. Eventually, we will have groups for Devices, Organizations, Configurations, Library (which will include VR Content, Files, Wifi), Users, etc.

Save and run the Mintlify repo locally to validate changes.

### Reviewing & Publishing Changes

Changes are deployed automatically to docs.managexr.com once merged into the main branch.

- Submit a PR for doc changes along with your API PR.
- Do not merge doc changes until after the API release.

## YAML Formatter in VSCode

To format YAML files in Visual Studio Code:

### 1. Install the YAML Extension

- Press `Ctrl+P` (Windows/Linux) or `Cmd+P` (Mac) and type:
  ```
  ext install redhat.vscode-yaml
  ```
- Press **Enter** to install.
- Now you can format using the default format hotkey
  - **Windows/Linux**: `Shift+Alt+F`
  - **Mac**: `Shift+Option+F`

### 2. Enable Auto Formatting on Save (Optional)

- Open **Settings** (`Ctrl+,` or `Cmd+,`).
- Search for **"format on save"** and enable **Editor: Format On Save**.

Alternatively, add the following to `settings.json`:

```json
"[yaml]": {
  "editor.defaultFormatter": "redhat.vscode-yaml"
}
```

## Tips and Tricks

- Search [Mintlify help docs](https://mintlify.com/docs/development).
- The `essentials` directory contains helpful examples of markdown in action.
- To use multiple lines in an OpenAPI description, use the `|` character. Use `CMD+F |` in `openapi.yaml` for examples.
