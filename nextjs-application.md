# Component Library Documentation

## Introduction
The Component Library provides a modular and extensible framework for visualizing and annotating data in web applications. It aims to enhance collaboration between AI tools and human users by enabling interactive data exploration and annotation.

---

## Architecture Overview
The architecture of the Component Library is based on these key principles:

1. **Modularity**: Each component is self-contained and can be used independently or in combination with others.
2. **Extensibility**: New components can be added without modifying existing code.
3. **Configurability**: Components can be configured via JSON metadata to adapt to various use cases.

---

## Components

### Authentication Components
The library includes authentication components to manage user access and sessions:

1. **Username and Password Authentication**: Standard login mechanism.
2. **OTP Authentication**: One-time password authentication via email for enhanced security.

### Generic Component System
This system allows developers to create and manage visual components:

#### Supported Data Types
- CSV
- JSON
- Text
- Graphs

#### Display Types
1. **Table**: Displays data in a tabular format.
2. **Card List**: Displays data as a list of cards.
3. **Graph/Chart**: Visualizes data as graphs or charts.
4. **Composite Widgets**: Combine multiple components into a single widget for complex visualizations.

### Annotation Support
The library includes annotation features to allow users to:

1. Comment on specific data points or visualizations.
2. Add tags or notes to annotations.
3. Edit or delete existing annotations.
4. Store annotations persistently on the server.

---

## Usage

### Installation
Install the Component Library using the following command:

```bash
npm install component-library
```

### Configuration
To configure the library, set up the following:

1. **Authentication**: Configure the authentication method (username/password or OTP) in the application settings.
2. **Data Sources**: Define the data sources that the components will consume.
3. **Component Registration**: Register components in your application using the provided API.

### Example Usage
Here’s an example of how to use the library in a React application:

```javascript
import React from 'react';
import { TableComponent, CardListComponent, AuthComponent } from 'component-library';

const App = () => {
    return (
        <div>
            <AuthComponent />
            <TableComponent data={tableData} />
            <CardListComponent data={cardData} />
        </div>
    );
};

export default App;
```

---

## Guidelines for Adding New Components
When contributing new components to the library, follow these guidelines:

1. **Modularity**: Ensure the component is modular and reusable.
2. **Documentation**: Provide clear documentation, including usage examples.
3. **Testing**: Write unit tests to cover the component’s functionality.
4. **Code Standards**: Follow the existing code style and conventions used in the library.
5. **Performance**: Optimize for performance and compatibility with other components.

---

## Folder Structure in GitHub Repository

1. **docs Folder**: Create a `docs` folder at the root level of your repository.
2. **Markdown Files**: Add individual markdown files for each major component or feature.
   - Example: `authentication_components.md`, `generic_component_system.md`, `annotation_support.md`

### Markdown File Structure
Each file should include:
1. **Feature Overview**: Describe the feature or component.
2. **Implementation Details**: Provide technical details and configurations.
3. **Usage Examples**: Include code snippets or examples.
4. **Future Enhancements**: Suggest potential improvements or expansions.

