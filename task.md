# Task Checklist: Facts-Only Mutual Fund FAQ Assistant

## System Architecture Design
- [x] Create modular, end-to-end system architecture document `architecture_design.md`
- [x] Integrate Groq API and strictly define Anti-Gravity principles
- [x] Include both technical and simplified system diagrams

## Phase 0: Resource Identification & Scoping
- [x] Identify valid official data sources (AMC, AMFI, SEBI)
- [x] Create `sources_config.json` (created as `phase0_resource_collection_and_organization/resources/resource_registry.json`)
- [x] Define strict scope boundaries (No blogs, no news sites)

## Phase 1: Data Collection, Cleaning & Storage
- [ ] Implement `DocumentScraper` to fetch PDFs/HTML
- [ ] Implement `TextExtractor` and `DataCleaner`
- [ ] Create structured JSON corpus with metadata (source URL, doc type)

## Phase 2: Chunking & Vector Storage
- [ ] Implement `SemanticChunker` (one-fact-per-chunk strategy)
- [ ] Generate embeddings and store in Vector DB (preserving metadata)

## Phase 3: Retrieval Layer
- [ ] Implement `QueryRouter` for intent classification (Factual vs Advisory)
- [ ] Implement strict `RefusalLogic` for advisory queries
- [ ] Implement `HybridRetriever` (Vector + Keyword search)

## Phase 4: LLM Integration (Groq API)
- [ ] Set up Groq API client with strict system prompts
- [ ] Implement citation injection logic
- [ ] Enforce output guardrails (Max 3 sentences, facts only)

## Phase 5: UI Layer
- [ ] Design minimal UI components (Welcome, Disclaimer, Input)
- [ ] Implement citation display

## Phase 6: Deployment
- [ ] Build Streamlit application `app.py`
- [ ] Connect all layers (Retrieval -> Generation -> UI)
- [ ] Verify stateless operation and safety checks
