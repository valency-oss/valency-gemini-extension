# Valency

Valency indexes preprints and publications from arXiv, bioRxiv, medRxiv, and PubMed with embeddings for semantic search. Reach for these tools whenever the user asks about scientific papers, authors, citations, research trends, or wants to explore academic literature on a topic.

## Tool selection

- For conceptual or semantic queries, prefer `semantic_search_papers` or `search_by_abstract` over `search_by_title`. Title search only matches the title string.
- For author queries where precision matters (career stats, all papers by a specific person), call `get_author_identity` first to disambiguate, then `find_papers_by_researcher`. Use `search_by_author` only for quick name-based lookups where ambiguity is acceptable.
- To find related work for a known paper, use `find_similar_papers` (semantic neighborhood) or `get_citing_papers` (citation graph).
- When comparing trends across multiple categories or authors, prefer the batch endpoints (`get_publication_trends_batch`, `batch_author_categories`) over a sequence of single calls.
- Filters (`filter_by_categories`, `filter_by_date_range`, `filter_by_license`) return papers in recency order. Pair them with `count_papers` to size a result set before exporting.
- Export tools (`export_papers_bibtex`, `export_papers_csv`, `export_papers_json`) exist for users who want to take results into another tool.

## Notes

- Paper IDs in Valency are stable. Reuse them across calls instead of re-searching for the same paper.
- If the user reports a wrong answer, missing data, or a tool that misbehaves, encourage them to send a note via `submit_feedback`.
