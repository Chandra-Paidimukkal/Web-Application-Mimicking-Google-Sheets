# Google Sheets Clone

A web application that mimics the user interface and core functionalities of Google Sheets, with a focus on mathematical and data quality functions, data entry, and key UI interactions.

## Features

### Spreadsheet Interface
- Google Sheets-like UI with toolbar, formula bar, and cell structure
- Drag functionality for cell content and formulas
- Cell dependencies that update when related cells change
- Support for basic cell formatting (bold, italics, alignment)
- Ability to add, delete, and resize rows and columns

### Mathematical Functions
- SUM: Calculates the sum of a range of cells
- AVERAGE: Calculates the average of a range of cells
- MAX: Returns the maximum value from a range of cells
- MIN: Returns the minimum value from a range of cells
- COUNT: Counts the number of cells containing numerical values in a range

### Data Quality Functions
- TRIM: Removes leading and trailing whitespace from a cell
- UPPER: Converts the text in a cell to uppercase
- LOWER: Converts the text in a cell to lowercase
- REMOVE_DUPLICATES: Removes duplicate rows from a selected range
- FIND_AND_REPLACE: Allows users to find and replace specific text within a range of cells

### Data Entry and Validation
- Support for various data types (numbers, text)
- Basic data validation for numeric cells

## Tech Stack and Data Structures

### Tech Stack
- **React**: For building the user interface components
- **TypeScript**: For type safety and better developer experience
- **Zustand**: For state management
- **Immer**: For immutable state updates
- **Tailwind CSS**: For styling
- **Lucide React**: For icons

### Data Structures

#### Cell Model
The core data structure is the `Cell` type, which contains:
- `value`: The displayed value (string, number, or null)
- `formula`: The formula string if the cell contains a formula
- `style`: Formatting options like bold, italic, color, etc.
- `dependencies`: List of cell IDs that this cell depends on

#### Sheet Data
The sheet data is stored as an object map where:
- Keys are cell IDs (e.g., "A1", "B2")
- Values are Cell objects

This approach allows for:
- Efficient cell lookup by ID
- Sparse storage (only storing cells with content)
- Easy serialization for potential save/load functionality

#### Selection Model
The selection state tracks:
- `start`: The cell where selection began
- `end`: The cell where selection ended
- `active`: The currently active cell within the selection

#### Formula Evaluation
Formulas are evaluated using a recursive approach:
1. Parse the formula to extract function name and range
2. Retrieve cell values from the specified range
3. Apply the appropriate function to the values
4. Update dependent cells when source cells change

## Why This Approach?

1. **Component-Based Architecture**: React components provide a clean separation of concerns and reusable UI elements.

2. **Immutable State Management**: Using Zustand with Immer ensures predictable state updates and enables features like undo/redo.

3. **Cell-Based Data Model**: The cell-based data structure mirrors how spreadsheets work conceptually, making it easier to implement spreadsheet-specific features.

4. **Formula Dependency Tracking**: By explicitly tracking cell dependencies, we can efficiently update only the cells affected by a change.

5. **Separation of Display and Data**: Keeping the formula and displayed value separate allows for proper recalculation when dependencies change.

## Usage

1. Click on cells to select them
2. Double-click or press Enter to edit a cell
3. Type values or formulas (starting with =)
4. Use the toolbar for formatting
5. Use the Functions menu to insert mathematical or data quality functions
6. Use Find and Replace to search and replace text in selected cells

LINK: https://cheerful-seahorse-5f987f.netlify.app/

Screenshots:
![Screenshot 2025-03-01 214221](https://github.com/user-attachments/assets/9e520122-bc3c-4810-bb19-7fe3983acb8b)
![Screenshot 2025-03-01 214239](https://github.com/user-attachments/assets/a256e579-6d25-4027-8e29-77a529abd378)



## Future Enhancements

- Support for more complex formulas and cell referencing
- Save and load functionality
- Data visualization capabilities (charts, graphs)
- More advanced formatting options
- Collaborative editing
