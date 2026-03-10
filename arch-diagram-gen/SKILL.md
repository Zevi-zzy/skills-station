---
name: "arch-diagram-gen"
description: "Convert technical architecture, module, or workflow descriptions into professional, responsive HTML architecture diagrams. Invoke when the user asks to generate architecture diagrams, visualize system designs, or flowcharts."
---

# Architecture Diagram Generator

This skill converts complex technical architectures, workflows, or functional modules into visually clear, professional, and responsive single-file HTML pages.

## When to Invoke

1.  When the user requests to generate an "architecture diagram," "functional architecture," or "technical architecture."
2.  When the user provides an ASCII flowchart or text description and asks for visual representation.
3.  When a professional visual chart is needed for system design documents.

## Visual Style Guidelines

The generated HTML must adhere to the following specifications:

### 1. Color System
- **Primary**: `#2c3e50` (Dark Blue-Grey, Headers/Borders)
- **Secondary**: `#34495e` (Secondary Text/Borders)
- **Background**: `#f4f6f7` (Page Background)
- **Card/Box**: `#ffffff` (Pure White Background)
- **Accent**: `#3498db` (Bright Blue, Highlights)
- **Success**: `#16a085` (Core Functions)

### 2. Layout Logic
- **Layered Structure**: Always divide the architecture into logical layers (e.g., UI Layer, Business Layer, Data Layer) and use arrows to indicate data flow.
- **Grid Layout**: Prioritize `display: grid` or `flex` for internal modules to ensure adaptive layout.
- **Responsive**: Must include mobile adaptation (e.g., adjusting column count via `@media`).

## Execution Steps

1.  **Parse Layers**: Identify Input Layer, Core Processing Layer, Infrastructure Layer, etc.
2.  **Extract Features**: Organize sub-functions under each layer.
3.  **Map Terminology**: Use professional technical terms (English or Chinese as requested).
4.  **Generate Code**: Output complete single-file code containing CSS and HTML.

## Example Template

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        :root { --primary-color: #2c3e50; --bg-color: #f4f6f7; }
        body { font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif; background: var(--bg-color); margin: 0; padding: 20px; }
        .container { max-width: 1200px; margin: 0 auto; }
        .layer { background: white; border-radius: 8px; box-shadow: 0 4px 6px rgba(0,0,0,0.1); padding: 20px; margin-bottom: 20px; border-left: 5px solid var(--primary-color); }
        .layer-title { font-weight: bold; margin-bottom: 15px; color: var(--primary-color); display: block; }
        .grid { display: grid; grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); gap: 15px; }
        .module { background: #f8f9fa; border: 1px solid #e0e0e0; padding: 15px; border-radius: 6px; text-align: center; }
        .arrow-down { text-align: center; font-size: 24px; color: #bdc3c7; margin: 10px 0; }
    </style>
</head>
<body>
    <div class="container">
        <!-- Content -->
    </div>
</body>
</html>
```
