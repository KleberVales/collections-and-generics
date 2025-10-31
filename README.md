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

 ### Common Collection Methods

 These methods are defined in the Collection interface (except where noted) and are implemented by classes like ArrayList and HashSet:

 - add(E element) → boolean: Inserts an element. Returns true if successful (always true for List, but false for Set if the element is a duplicate).
- remove(Object object) → boolean: Removes a single matching element. Returns true if a match was found and removed.
- isEmpty() → boolean / size() → int: Check if the collection is empty and get the number of elements.
- clear() → void: Removes all elements from the collection.
- contains(Object object) → boolean: Checks if a value is in the collection (uses equals() for comparison).
- removeIf(Predicate) → boolean: Removes all elements that match a given condition (e.g., list.removeIf(s -> s.startsWith("A"))).
- forEach(Consumer) → void: Iterates over each element (e.g., cats.forEach(System.out::println)).

### Iteration & Equality

- Iteration: Can be done with forEach, an enhanced for loop, or an Iterator.
- Equality (equals()): The implementation is specific to the collection type.
   - List equality depends on both the elements and their order.
   - Set equality depends only on the elements, not their order.
   - Different collection types (e.g., a List and a Set) are never equal, even if they contain the same elements.

 ### Key Pitfall: Unboxing null

 - You can add null to a collection like ArrayList<Integer>.
- However, if you try to retrieve that null and assign it to a primitive int, it will cause a NullPointerException because Java cannot unbox null to a primitive value.

## Using the List Interface

A List is an ordered collection that allows duplicate entries. Elements are accessed by a zero-based integer index.

### Key List Implementations









