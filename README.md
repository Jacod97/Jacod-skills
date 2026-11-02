# Jacod-skills

This repository brings together my preferred approaches to documentation, design, and development as reusable agent skills. Each skill includes practical guidelines and validation criteria, with templates and diagram styles where needed.    
Skill instructions are primarily written in Korean. Translate and adapt them to your preferred language as needed

## Available Skills

All currently available skills belong to the `writing` category.

| Skill | Purpose | Output |
| --- | --- | --- |
| [write-docs](skills/writing/write-docs/SKILL.md) | Write research logs, paper and concept reviews, reference documents, and research plans | HTML, LaTeX and PDF, or explanatory documents, depending on document type |
| [write-readme](skills/writing/write-readme/SKILL.md) | Introduce applications, libraries, CLIs, research repositories, and resource collections, with usage instructions | English `README.md` |
| [draw-diagram](skills/writing/draw-diagram/SKILL.md) | Illustrate model and module structures, training stages, and processing workflows | TikZ, SVG, or PNG diagrams for documents |

## Skill Selection

- **Research documentation — `write-docs`**: Research logs record experiments and results. Reviews explain papers and technical concepts. Reference documents organize datasets, libraries, codebases, and tools for later lookup. Research plans define objectives, methods, and proposed experiments. The workflow includes outline agreement before drafting.
- **Repository introduction and usage — `write-readme`**: Organizes purpose, capabilities, setup, and examples around the repository type. Source inspection verifies public behavior and commands. Output uses English and a factual documentation style.
- **Structure and process diagrams — `draw-diagram`**: Structure diagrams show components and relationships; flow diagrams show stages and branches. Output uses TikZ for LaTeX, SVG for HTML, and linked image files for Markdown.

## Getting Started

1. Download this repository to a workspace accessible to the agent.
2. Select a skill from the list above.
3. Provide the path to its `SKILL.md`, the task objective, source material, and output location. Keep the referenced rules and templates accessible.

The examples below assume the repository root is the working directory. Adjust skill paths when working in another project.

### Project README

```text
Read and apply skills/writing/write-readme/SKILL.md.
Write an English README.md for first-time users of this repository.
Include the available skills and usage examples.
```

### Research Log

```text
Read and apply skills/writing/write-docs/SKILL.md.
Create a research log from the supplied experiment settings and results.
First propose an outline focused on comparison conditions and observations.
Save the output as HTML under reports/.
```

### Pipeline Diagram

```text
Read and apply skills/writing/draw-diagram/SKILL.md.
Draw a flow diagram covering data collection, preprocessing, model training,
and evaluation. Produce an SVG for a README and save it under figures/.
Confirm the elements and connections before drawing.
```

For environments with skill registration, register the **entire skill folder** using the environment's supported method. Copying only `SKILL.md` omits referenced rules and templates. Make `draw-diagram` available alongside document or README skills when new diagrams are required.

## Requirements

Applying these skills requires an AI agent with access to read and edit local files. Generation and verification tools depend on the output.

| Task | Requirements |
| --- | --- |
| README writing | Target repository, actual setup or usage examples, and a Markdown viewer |
| HTML research logs | Experiment settings and results, plus a browser for reviewing output |
| LaTeX documents and PDFs | XeLaTeX, required packages, and fonts. The default Korean layout uses `xetexko`, Noto Serif CJK KR, Noto Sans CJK KR, and DejaVu Sans Mono |
| Diagram generation and review | A browser and Playwright for SVG and HTML review; XeLaTeX for TikZ; `pdftocairo` when converting PDF to SVG |

Detailed output requirements are defined in the [LaTeX document rules](skills/writing/write-docs/references/modules/latex.md) and [diagram tool selection guide](skills/writing/draw-diagram/SKILL.md).
