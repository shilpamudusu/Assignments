# Clinical Trial Data Widget Project

## Goal
Build a reusable widget displaying clinical trial data from public APIs.

---

## Evaluation Criteria
1. **Code**: Well-structured, maintainable, and efficient.
2. **UX**: Intuitive interface, easy navigation, and clear data presentation.
3. **Reusability**: Easily integrates into other projects.

---

## Part 1: Core Table Functionality

### Data Source
- **ClinicalTrials.gov API (RESTful)**
  - Endpoint example: `https://clinicaltrials.gov/api/query?cond=asthma&count=true`

### Features

#### Table Columns
1. **Study Title**: Linked to ClinicalTrials.gov details using NCT ID.
   - URL pattern: `https://clinicaltrials.gov/study/NCT[NCTID]`
2. **NCT Number**: Unique trial identifier.
3. **Status**: Trial status (e.g., Recruiting, Completed).
4. **Conditions**: Diseases studied in the trial.
5. **Intervention**: Drug/treatment being tested.
6. **Sponsor**: Organization funding the trial.

#### Interaction
- Filtering and sorting options for:
  - **Status**
  - **Date Posted** (e.g., 2021-2023)
  - **Phase** (e.g., Phase 2)
    - _Missing feature: Add this for improvement_

#### UX Enhancements
- Sticky column headers: The "Study Title" column remains fixed during horizontal scrolling.
- Explore alternative views to enhance data visualization and interaction beyond basic table replication.

### Technical Details
- Use RESTful endpoints to fetch data based on specific diseases (e.g., asthma, hydrogenitis operativa).
- Emphasize performance and user-friendliness in API queries and table rendering.

---

## Part 2: Enrichment with Open Targets Data (Future Scope)

### Data Source
- **Open Targets Platform (GraphQL API)**

### Additional Columns
1. **Target**: Gene/protein the drug interacts with.
2. **Modality**: Drug type (e.g., small molecule).
3. **Mechanism of Action (MOA)**: Description of how the drug works.

### Features
- Use the drug name retrieved from ClinicalTrials.gov to query Open Targets API.
- Enhance the existing table by integrating these data points into new columns.

### Technical Details
- Construct GraphQL queries to fetch the necessary data.
- Maintain performance and integration simplicity with minimal disruption to core functionality.

---

## Folder Structure in GitHub Repository
1. Create a `docs` folder at the root level.
2. Inside the `docs` folder, add individual markdown files for each problem/feature:
   - **Core Table Functionality**: `core_table.md`
   - **Phase Filtering Improvement**: `phase_filtering.md`
   - **Open Targets Integration**: `open_targets_integration.md`

### Markdown File Structure
Each file should include:
1. **Problem Statement**: Clearly describe the feature or issue.
2. **Solution Details**: Explain how the feature is implemented or improved.
3. **Technical Challenges**: Highlight difficulties and how they were addressed.
4. **Future Enhancements**: Suggest potential improvements.

