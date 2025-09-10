# Deck.gl Community Fork Workflow

This document outlines the process for maintaining and publishing a forked version of `@deck.gl-community/editable-layers` with custom modifications.

## Repository Structure

- **Fork Repository**: `https://github.com/TerraClear/deck.gl-community`
- **Package Location**: `modules/editable-layers/`
- **Main File**: `modules/editable-layers/src/editable-layers/editable-geojson-layer.ts`

## Making Changes

1. **Navigate to the source file**:

   ```bash
   cd modules/editable-layers/src/layers/
   ```

2. **Edit the TypeScript file**:
   - Make changes to `editable-geojson-layer.ts`
   - Ensure changes are made to the `.ts` file, not the compiled `.js` version

## Building and Publishing

3. **Build from root directory**:

   ```bash
   cd ../../../../  # Go to repo root
   npm run build
   ```

4. **Update version number in package.json**:

   ```bash
   cd modules/editable-layers/
   # Edit package.json and increment version
   # Example: 9.1.0-beta.5-custom.1 → 9.1.0-beta.5-custom.2
   ```

5. **Commit changes with version update**:

   ```bash
   cd ../../  # Back to repo root
   git add .
   git commit --no-verify -m "Fix: Dragging newly created points - bump to v9.1.0-beta.5-custom.X"
   git push
   ```

6. **Publish the package**:
   ```bash
   cd modules/editable-layers/
   npm publish
   ```

## Using in Projects

8. **Update your project's package.json**:

   ```json
   {
     "dependencies": {
       "@terraclear/editable-layers": "^9.1.0-beta.5-custom.X"
     }
   }
   ```

9. **Install in your project**:
   ```bash
   npm install
   ```

## Important Notes

- Always build from the **root directory** of the deck.gl-community repo
- The `--no-verify` flag skips pre-commit hooks if needed
- Use semantic versioning with the `-custom.X` suffix to track your changes
- Make sure you're authenticated with GitHub package registry:
  ```bash
  npm login --scope=@terraclear --registry=https://npm.pkg.github.com
  ```

## Version History

- `9.1.0-beta.5-custom.1`: Initial fork with drag improvements
- `9.1.0-beta.5-custom.2`: [Description of changes]

## Troubleshooting

- If build fails, ensure you're in the root directory
- If publish fails, check authentication and version number increment
- If installation fails in projects, verify the package name and version
