# Serverless, fast, lightweight 3D UMAP viewer for 10x Single-Cell datasets 

demo: https://pvalissery.github.io/UMAP_gen/

The primary goal of this tool is to provide a fast, lightweight way to visualize high-dimensional datasets quickly, avoiding the need for server costs or a high-end computer.

### The Data
The underlying single-cell transcriptomic data was sourced from the Malaria Cell Atlas ([Real et al., *Science*, 2024; DOI: 10.1126/science.adj4088](https://www.science.org/doi/10.1126/science.adj4088?referrer=https%3A%2F%2Fwww.malariacellatlas.org%2F)). The raw 10x Genomics matrices were aggregated and processed offline using a custom Python pipeline to extract the core UMAP coordinates and clustering metadata. Happy to share those if interested. 

### The Process
If you are using a low-end computer, most graphing programs notoriously choke if you try to render 45,000 standard DOM elements at once. Also, If you plug a raw single-cell dataset into a basic SVG charting library, your tab is going to crash. To get around the browser bottlenecks, all the heavy computational lifting is completely decoupled from the frontend. The custom Python script does the dirty work offline: parsing the massive raw datasets from the paper, calculating the 3D embeddings, stripping out the noise, and packaging the essentials into a lean JSON payload. 

The web side is just HTML and Javascript. It fetches that JSON and hands it straight to Plotly's WebGL engine. Your local GPU takes over the rendering, giving you hardware-accelerated 3D rotation and instant metadata toggling. This tool removes the need for a high end computer to visualize the data.
