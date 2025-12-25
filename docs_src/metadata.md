# Repository Metadata

## Overview

The `METADATA.json` file in the root of this repository provides structured information about the XLS project. This file serves as a machine-readable reference for project characteristics, technology stack, features, and community information.

## Purpose

The metadata file is designed to:

- Provide a centralized source of truth for project information
- Enable automated tooling and documentation generation
- Facilitate project discovery and understanding
- Support integration with package managers and registries
- Document the project's technology stack and dependencies

## Structure

The metadata file is organized into the following sections:

### Project Information

Basic project details including name, description, version, and keywords.

```json
{
  "project": {
    "name": "XLS",
    "full_name": "XLS: Accelerated HW Synthesis",
    "description": "...",
    "version": "0.0.1",
    "status": "experimental"
  }
}
```

### Repository

Source control and collaboration information:

- Repository URLs (upstream, fork, issues, discussions)
- Version control type

### License

License type and references:

- SPDX license identifier
- License URL and description

### Documentation

Links to all major documentation resources:

- Homepage
- Quick start guide
- Tutorials
- API reference
- Contributing guidelines
- Style guides
- Colab notebooks

### Technology Stack

Details about the languages, tools, and dependencies:

- Primary programming languages (C++, Python, DSLX)
- Build system (Bazel)
- Key dependencies (LLVM, Z3, etc.)
- Supported output formats

### Features

Project capabilities and supported platforms:

- Core capabilities (synthesis, optimization, code generation)
- Supported platforms (Linux, Docker)
- Experimental features

### Project Structure

Description of major components and directories:

- `dslx/` - Domain-specific language frontend
- `ir/` - Intermediate representation
- `codegen/` - Code generation
- `jit/` - Just-in-time compiler
- And more...

### Community

Community resources and guidelines:

- Communication channels
- Code of conduct
- Contributor License Agreement (CLA) information

### Development

Development practices and guidelines:

- Style guides for different languages
- CI/CD configuration
- Code review process

### Distribution

Information about binary releases and packages:

- GitHub releases
- Conda packages
- Docker images

### Related Projects

Links to related tools and dependencies:

- Upstream project
- Visualization tools
- Synthesis backends
- Process Design Kits (PDKs)

## Usage

The metadata file can be:

1. **Parsed programmatically** - Use any JSON parser to extract information
2. **Used by tooling** - Integrate with build systems, documentation generators, or package managers
3. **Referenced in documentation** - Maintain consistency across documentation by referencing the metadata
4. **Validated** - Ensure information stays up-to-date through automated checks

## Example: Reading Metadata

### Python

```python
import json

with open('METADATA.json', 'r') as f:
    metadata = json.load(f)
    
print(f"Project: {metadata['project']['name']}")
print(f"License: {metadata['license']['type']}")
print(f"Languages: {', '.join(metadata['technology_stack']['primary_languages'])}")
```

### JavaScript/Node.js

```javascript
const fs = require('fs');
const metadata = JSON.parse(fs.readFileSync('METADATA.json', 'utf8'));

console.log(`Project: ${metadata.project.name}`);
console.log(`License: ${metadata.license.type}`);
console.log(`Languages: ${metadata.technology_stack.primary_languages.join(', ')}`);
```

### Command Line (jq)

```bash
# Get project name
jq '.project.name' METADATA.json

# Get all primary languages
jq '.technology_stack.primary_languages[]' METADATA.json

# Get documentation homepage
jq '.documentation.homepage' METADATA.json
```

## Maintenance

The metadata file should be updated when:

- Project version changes
- New major features are added
- Dependencies are updated
- Documentation URLs change
- New community resources are added

When making updates:

1. Ensure the JSON remains valid
2. Update the `metadata.generated` field with the current date
3. Increment the `metadata.version` if the schema changes
4. Test that automated tools still work correctly

## Schema Version

Current metadata schema version: `1.0.0`

The schema follows semantic versioning:
- **Major**: Breaking changes to the structure
- **Minor**: Backward-compatible additions
- **Patch**: Corrections and clarifications

## Contributing

If you notice outdated information in the metadata file, please:

1. Open an issue describing what needs to be updated
2. Submit a pull request with the corrections
3. Ensure the JSON remains valid after your changes

See [CONTRIBUTING.md](../CONTRIBUTING.md) for general contribution guidelines.
