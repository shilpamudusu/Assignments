
# Gene Essentiality – Cancer DepMap Documentation

## Overview
The goal of this project is to build a web page that shows the gene essentiality map for a given gene target. The essentiality map will provide insights into the gene's importance for cell survival, especially in the context of cancer, by utilizing data from the Cancer Dependency Map (DepMap). Users will be able to input a gene’s EnsemblID (ENSG) to fetch the corresponding essentiality data.

## Components and Prerequisites

### Components
The application will consist of the following major components:
- **Gene Input Field**: A form input that accepts the EnsemblID (e.g., ENSG00000012048 for BRCA1).
- **Gene Essentiality Map**: A visualization displaying the gene essentiality map based on the provided EnsemblID. The map will show the dependency of the gene across different cancer cell lines.
- **GraphQL API Integration**: A backend service that fetches the gene essentiality data from the DepMap GraphQL endpoint.
- **Tooltip**: Display additional information about each data point when hovering over the map.
- **Error Handling**: Display appropriate messages if the input is invalid or no data is returned for the given gene.

### Prerequisites
- **Node.js** and **npm** installed for managing the project.
- **React** and **Next.js** for front-end development.
- **GraphQL** for data fetching from the DepMap API.
- **Tailwind CSS** for styling the application.
- **ShadCN components** for reusable UI components.

### API Integration
You will use a GraphQL API to fetch the gene essentiality data. The sample JavaScript code to invoke the API is provided below, which should be adapted to meet the project’s needs. It should make a query based on the provided EnsemblID and return the data needed to render the essentiality map.
## Gene IDs

You should test the application with the following genes and their corresponding EnsemblIDs:

* BRCA1: ENSG00000012048
* BRCA2: ENSG00000139618
* TP53: ENSG00000141510
* EGFR: ENSG00000146648

## Developer Instructions

### How Developers Use Components

* **Gene Input Field:** 
    * Developers will need to ensure the input field is capable of accepting a valid EnsemblID. 
    * This component should be reusable across different parts of the application.
* **Gene Essentiality Map:** 
    * Developers will need to integrate the GraphQL query with a visualization library (such as D3.js or Plotly) to render the essentiality map based on the data retrieved.
* **Tooltip:** 
    * Implement tooltips to show additional details about each data point in the map when users hover over it.

### Creating New Components

If a developer wants to create a new component, they should:

1. Identify the functionality and data required for the component.
2. Create the component in a reusable manner with clear props and states.
3. Ensure proper integration with other parts of the application, such as the GraphQL API and styling system.

### Storing and Managing Annotations

* Annotations will be managed on the front-end. 
* Developers can modify or add annotations as needed based on user interactions with the gene essentiality map. 
* The annotations will be stored temporarily in the browser state, but long-term storage could be added if necessary.

## Using the Components in React and Next.js

* **React:** 
    * The components will be implemented as functional components in React. 
    * The state management will be done using React hooks like `useState` and `useEffect` for handling API calls and rendering data.
* **Next.js:** 
    * The page will be part of a Next.js application. 
    * Developers should ensure that the page is optimized for server-side rendering (SSR) or static site generation (SSG), depending on the use case. 
    * The page will fetch data via the API and render it dynamically.

## Deployment Considerations

* Ensure the GraphQL API is accessible and properly integrated into the deployment environment.
* The application should be deployed with a scalable cloud solution, such as Vercel or Netlify, which works well with Next.js.

## Extension Possibilities

* **Export Functionality:** 
    * Future work can include implementing export options to allow users to download the essentiality data in CSV or other formats.
* **Multi-Gene Support:** 
    * The app can be extended to allow users to input multiple EnsemblIDs at once and display maps for each gene.
* **Advanced Filtering:** 
    * Developers can add filtering options to the map, enabling users to filter by cell line type, dependency score range, or other relevant factors.

## Testing

The app should be tested with the following genes:

* BRCA1 (ENSG00000012048)
* BRCA2 (ENSG00000139618)
* TP53 (ENSG00000141510)
* EGFR (ENSG00000146648)

Each test should ensure the following:

* The gene essentiality map renders correctly.
* The tooltip displays relevant data when hovering over the plot.
* Errors are handled gracefully, especially when an invalid EnsemblID is entered.

## SME Review

Once the initial documentation and design are complete, it should be shared with subject matter experts (SMEs) to verify that:

* The project scope aligns with research goals.
* The chosen approach for data visualization and API integration is suitable. 

## Roles of the Team members

### Abhijeet (UI/UX Developer)

- Responsibilities:
* Design and implement the user interface (UI) of the application.
* Create a visually appealing and user-friendly experience.
* Develop the Gene Input Field component, ensuring it's reusable and handles valid Ensembl IDs.
* Work closely with Yashraj to integrate UI elements with the application's functionalities.
* Ensure the UI is responsive and adapts well to different screen sizes.
* Conduct usability testing and gather user feedback to refine the UI.

### Yashraj (UI/UX, Backend/Functionality Developer)

- Responsibilities:
* Develop the core functionalities of the application, including:
* Integration with the GraphQL API to fetch gene essentiality data.
* Implementation of the Gene Essentiality Map component, including data visualization and tooltip functionality.
* Handle data fetching, processing, and state management.
* Implement error handling and graceful degradation.
* Work with Abhijeet to ensure smooth integration of UI elements with the application's logic.
* Test the application thoroughly with the specified genes and edge cases.

### Shilpa (Documentation & Implementation)

- Responsibilities:
* Maintain comprehensive documentation throughout the development process.
* Document design decisions, code structure, and API interactions.
* Create user manuals and tutorials to guide users on how to use the application.
* Assist with the implementation of the application, particularly in areas related to data management and API interactions.
* Ensure code quality and adherence to best practices.
* Collaborate with Abhijeet and Yashraj to resolve any technical issues or roadblocks.

### Collaboration:

* Regular team meetings to discuss progress, address challenges, and ensure alignment.
* Code reviews to ensure code quality and maintainability.
* Shared responsibility for testing and debugging.
* This structure provides a clear division of labor and fosters effective collaboration among the team members.

Example API query:
```javascript
query Depmap ($ensemblId: String!) {
  target(ensemblId: $ensemblId) {
    id
    depMapEssentiality {
      tissueName
      screens{
        depmapId
        cellLineName
        diseaseFromSource
        geneEffect
        expression
      }
    }
  }
}

{
  "ensemblId": "ENSG00000012048"
}
