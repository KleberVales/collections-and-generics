# collections-and-generics

## Using Common Collection APIs
This text covers the core interfaces of the Java Collections Framework, the use of generics, and common methods for managing and iterating over collections.

### Core Collection Interfaces

There are four main interfaces for storing groups of objects:

- List: An ordered collection that allows duplicates. Elements are accessed by an index.
- Set: A collection that does not allow duplicates.
- Queue: Orders elements for processing in a specific order.
- Map: Stores key/value pairs. No duplicate keys are allowed. (Note: Map is part of the framework but does not implement the Collection interface).

<img width="1070" height="461" alt="Captura de tela 2025-10-31 102920" src="https://github.com/user-attachments/assets/eb2a3c7a-4969-432f-93d3-366b4cad363e" />

### Using Generics

- Purpose: Generics (e.g., List<String>) provide type safety, eliminating the need for explicit casts and preventing ClassCastException at runtime by catching type errors at compile time.
- Shortening Code:
   - Diamond Operator (<>): Lets you omit the type on the right side (e.g., new ArrayList<>()).
   - var: Infers the type from the right side (e.g., var list = new ArrayList<Integer>()).
   - Warning: Using both var and <> together (e.g., var list = new ArrayList<>()) results in a generic type of Object, which is rarely useful.



