# Research Review workspace

The app now includes a dedicated **Review** workspace in the top navigation.

## Workflow
1. Search for papers in Discover, or save papers to the Library.
2. Open Review from the top navigation and select a paper, or use **Review paper** on a search result.
3. The app processes the selected PDF using the existing paper-processing pipeline.
4. When processing is complete, choose **Generate full review**.
5. The research agent produces a structured review covering the executive summary, problem, goals, novelty, workflow, methods, data/experiments, results, benefits, limitations, baselines, reproducibility, future work, key facts and a balanced verdict.

The review prompt instructs the agent not to invent missing information and to label unavailable details as “Not specified in the paper”. AI findings should still be checked against the source paper.
