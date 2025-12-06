# Mapping EU Universities & Research Groups on AI in Education

This repository contains the full pipeline for a bibliometric study of **AI-in-Education research with EU involvement** using the OpenAlex database.  
The project identifies core venues, key topics, institutions, and researchers, and compares the broader AI-in-Education ecosystem with a high-quality “core” subset of publications.

---

## Project Objectives

1. **Map the field**  
   Identify works on AI-based solutions for education (2020–present) with at least one EU affiliation, using OpenAlex.

2. **Build two analytical layers**  
   - **ALL** – broad set of AI-in-Education works (maximising coverage).  
   - **STRICT** – high-quality subset filtered via Scopus/SJR (Q1–Q3) to approximate the core literature.

3. **Characterise the landscape**  
   - Publication trends and Open Access patterns.  
   - Main concepts and topics (learning analytics, intelligent tutoring, etc.).  
   - Leading venues and institutions.

4. **Identify the core of the field**  
   - Implement Van Eck & Waltman’s method for **core sources** and **core publications**.  
   - Compare **core vs non-core** works in terms of impact, themes, and collaboration.

5. **Cluster authors and institutions**  
   - Use feature-based clustering on the STRICT layer to identify typical “roles” (e.g., global leaders, collaborative hubs, local actors).  
   - Relate these clusters to their contribution to the core literature.

6. **Highlight key researchers**  
   - Flag “key authors” based on productivity and impact since 2020.  
   - Provide VOSviewer-ready files for co-authorship and topic maps.

The final outcome is a reproducible Python pipeline plus a written report summarising methods, results, and interpretations.

---

## Repository Structure

Each numbered folder contains one main Python script or notebook that corresponds to a step in the pipeline.

- `1_collect_data/`  
  Query OpenAlex for AI-in-Education works with EU affiliations, save raw **ALL** dataset, and perform basic cleaning.

- `2_enriching_issn_strict/`  
  Enrich works with Scopus and SCImago (SJR) information via ISSNs, derive flags such as `in_scopus_flag` and `sjr_quartile`, and construct the **STRICT** layer.

- `3_VOS_network/`  
  Build co-occurrence and collaboration networks (concepts, topics, authors, institutions) and export VOSviewer-ready node/edge tables and topic maps.

- `4_clustering/`  
  Aggregate features for authors and institutions (works, citations, OA share, collaboration, etc.), run k-means clustering, and visualise clusters (PCA, heatmaps).

- `5_core_noncore/`  
  Implement the core-source/core-publication methodology, label works and venues as **core** or **non-core**, and explore basic differences between these groups.

- `6_comparing_all_strict/`  
  Compare the ALL vs STRICT layers: publication trends, OA patterns, concepts, topics, venues, and institutional profiles.

- `7_comparing_core_noncore/`  
  Detailed comparison of core vs non-core works and sources: citation impact, thematic structure, collaboration patterns, and their significance.

- `8_key_authors/`  
  Identify and describe key researchers (e.g., ≥N papers since 2020), link them to clusters, and prepare tables/maps for the final report.

- `final_report.pdf`   
  The written project report summarising the full pipeline, main findings, visualisations (including VOSviewer maps), and interpretations.

---

## Brief Usage Notes

1. Run the folders in numerical order (`1_collect_data` → `8_key_authors`) to reproduce the full analysis.
2. Scripts assume a Python environment with standard data-science libraries (`pandas`, `numpy`, `requests`, `scikit-learn`, `matplotlib`, etc.).
3. VOSviewer (desktop) is used for visualising the exported network files from `3_VOS_network/`.

---

If you use this code or results, please cite the final report (`final_report.pdf`) and the original OpenAlex and SCImago/Scopus data sources.
