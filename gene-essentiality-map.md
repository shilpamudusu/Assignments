# Gene Essentiality – Cancer DepMap Documentation

## Overview
The goal of this project is to build a web page that shows the gene essentiality map for a given gene target. The essentiality map will provide insights into the gene's importance for cell survival, especially in the context of cancer, by utilizing data from the Cancer Dependency Map (DepMap). Users will be able to input a gene's EnsemblID (ENSG) to fetch the corresponding essentiality data.

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
- **ShadCN components** for reusable and good looking UI components.

### API Integration
You will use a GraphQL API to fetch the gene essentiality data. The sample JavaScript code to invoke the API is provided below, which should be adapted to meet the project's needs. It should make a query based on the provided EnsemblID and return the data needed to render the essentiality map.


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

```

## Gene IDs

You can test the application with the following genes and their corresponding EnsemblIDs:

* BRCA1: ENSG00000012048
* BRCA2: ENSG00000139618
* TP53: ENSG00000141510
* EGFR: ENSG00000146648

## Developer Instructions

### How Developers Use Components

* **Gene Input Field:** 
    * Developers will need to ensure the input field is capable of accepting a valid EnsemblID.
    * `GeneEssentialityChart` component should be passed Props regarding EnsemblID, loading state and error and more desirably `theFormComponent` should be able to properly pass on these props to `GeneEssentialityChart`. 
    * `GeneEssentialityChart` will pass on information regarding these states to the form to show relevent UI hints regarding errors and loading states.

Example:
```js
"use client"

import { useState } from "react"
import { GeneSearchForm } from "./Form"
import { GeneEssentialityChart } from "./GeneEssentialityMap"


export default function MainGeneMap() {
const [ensemblId, setEnsemblId] = useState("")
const [loading, setLoading] = useState(false)
const [error, setError] = useState("")

return (
    <div className="space-y-4">
    <GeneSearchForm
        setEnsemblId={setEnsemblId}
        loading={loading}
        error={error}
    />
    <GeneEssentialityChart
        ensemblId={ensemblId}
        setLoading={setLoading}
        setError={setError}
    />
    </div>
)
}
```


## How to download Npm Package
currently if you directly download the package from `https://npmboot.svc.aganitha.ai/` npm repo it does not have all the required dependencies so it will not work properly.

The current work around for this is to download all the dependencies and required packages from the global npm repo and then change your repo to `https://npmboot.svc.aganitha.ai/` and download the component.

##### step 1 - Set repo to the main NPM repo

```sh
npm config set registry https://registry.npmjs.org/
```

##### step 2 - Download the gene-essentiality-chart component from npm

```sh
npm i gene-essentiality-chart
```

```use --force flag if there is version clash```

##### step 3 - Set the repo back to aganitha

```sh
npm config set registry https://npmboot.svc.aganitha.ai/
```


```use --force flag if there is version clash```
##### step 4 - Now install the component back from the aganitha repo

```sh
npm install @aganitha/gene-essentiality-chart@1.0.0
```

##### step 5 - Now from the package.json/npm you can remove the `gene-essentiality-chart` npm package (the one we installed from the main NPM repo)
We initially installed this package from the main NPM repository to ensure all necessary dependencies were obtained. Now that this purpose has been fulfilled, feel free to remove it.


##### step 6 - import the package

```js
import {GeneEssentialityChart} from '@aganitha/gene-essentiality-chart'
```

```
Note : This component requires the user to install tailwind or else the component might not look as intended.
```

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

### Abhijeet (UI/UX Design)

Responsibilities:
* Design and implement the user interface (UI) of the application.
* Create a visually appealing and user-friendly experience.
* Develop the Gene Input Field component, ensuring it's reusable and handles valid Ensembl IDs.
* Work closely with Yashraj to integrate UI elements with the application's functionalities.
* Ensure the UI is responsive and adapts well to different screen sizes.
* Conduct usability testing and gather user feedback to refine the UI.

### Yashraj (UI/UX, Functionality Developer)

Responsibilities:
* Develop the core functionalities of the application, including:
* Integration with the GraphQL API to fetch gene essentiality data.
* Implementation of the Gene Essentiality Map component, including data visualization and tooltip functionality.
* Handle data fetching, processing, and state management.
* Implement error handling and graceful degradation.
* Work with Abhijeet to ensure smooth integration of UI elements with the application's logic.
* Test the application thoroughly with the specified genes and edge cases.

### Shilpa (Documentation & Implementation)

Responsibilities:
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