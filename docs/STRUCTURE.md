# Repository Structure

This repository contains the **Microsoft AI Decision Tree** - a comprehensive guide for navigating Microsoft's AI technology portfolio.

## Directory Organization

```
microsoft-ai-decision-tree/
├── README.md              # Main decision tree guide (primary documentation)
├── images/                # Visual assets and diagrams
│   └── ai-gateway-flow.gif
├── docs/                  # Auxiliary documentation
│   └── STRUCTURE.md       # This file
└── .gitignore            # Git ignore rules
```

## File Descriptions

### Root Level

- **README.md**: The primary documentation containing the complete Microsoft AI Decision Tree framework. This includes:
  - Technology definitions
  - Ecosystem architecture (5 layers)
  - Decision framework (BXT + 6 critical questions)
  - Architecture patterns
  - Triaging intake process
  - Visual decision flow diagrams (Mermaid)

### Images Folder

- **ai-gateway-flow.gif**: Azure API Management (AI Gateway) flow diagram illustrating centralized governance capabilities for AI workloads

### Docs Folder

- **STRUCTURE.md**: This file - documents the repository organization
- Future auxiliary documentation can be added here as needed

## Usage

Start with the [README.md](../README.md) in the root directory. This is the primary decision tree guide that helps you:

1. Understand Microsoft's AI technology portfolio
2. Apply the Business-Experience-Technology (BXT) framework
3. Navigate 6 critical questions for technology selection
4. Choose between M365 Copilot, Copilot Studio, M365 Agents SDK, Azure AI Foundry, and Azure AI Agent Service

## Contributing

When adding new content:

- **Images/Diagrams**: Add to `/images/` folder
- **Auxiliary Documentation**: Add to `/docs/` folder
- **Main Decision Tree Updates**: Edit `README.md`
- Use relative paths when referencing images: `images/filename.ext`

## Image References

All images are referenced using relative paths from the root README.md:

```markdown
![Description](images/image-name.ext)
```

This ensures compatibility across GitHub, local viewing, and documentation sites.

## Version Control

This repository uses Git for version control. Key practices:

- Commit atomic changes with descriptive messages
- Document major framework updates in commit messages
- Tag releases when significant methodology changes occur

## Sources

All content in this repository is based on official Microsoft documentation and best practices. See README.md for detailed source citations and confidence levels.
