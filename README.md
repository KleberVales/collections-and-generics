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

- ArrayList: Like a resizable array. Excellent for frequent reading/accessing by index (constant time). Adding/removing elements (except at the end) is slower.
- LinkedList: Implements both List and Deque. Excellent for frequent adding/removing from the beginning or end (constant time). Accessing by an arbitrary index is slower (linear time).

### Creating Lists

1. Factory Methods (Often Immutable):

- Arrays.asList(array): Returns a fixed-size list backed by the original array. Changes to the list or array are reflected in the other.
- List.of(...) / List.copyOf(collection): Return immutable lists. Cannot be modified (adding, removing, or replacing elements throws an exception).

2. Constructors:

- new ArrayList<>() / new LinkedList<>(): Creates an empty list.
- new ArrayList<>(collection): Creates a list containing a copy of the specified collection.
- new ArrayList<>(int capacity): Creates an ArrayList with a specific initial capacity.

### Essential List Methods (Beyond Collection Interface)

These methods work with indexes:

Method | Description
-- | --
add(int index, E element) | Inserts element at a specific index.
get(int index) | Returns the element at the specified index.
set(int index, E e) | Replaces the element at an index, returns the original.
remove(int index) | Removes the element at a specific index.
indexOf(Object o) | Returns the first index of the element, or -1 if not found.
lastIndexOf(Object o) | Returns the last index of the element, or -1 if not found.
replaceAll(UnaryOperator op) | Replaces each element with the result of the operator.
sort(Comparator c) | Sorts the list according to the Comparator.

### Important Nuances

- Overloaded remove(): Be careful with the two remove methods.
   - remove(Integer) searches for and removes the object.
   - remove(int) removes the element at that index.
- Converting to Array:
   - list.toArray() returns an Object[].
   - list.toArray(new String[0]) is the correct way to get a typed array (e.g., String[]). The new array is independent of the original list.
- Immutability: Lists created with List.of() and List.copyOf() cannot be changed. Arrays.asList() creates a fixed-size list that cannot change size but can have its elements modified.

## Using the Set Interface

A Set is a collection that does not allow duplicate entries. It is used when you need to ensure uniqueness but are not necessarily concerned with the order of elements.

### Key Set Implementations

- HashSet:
   - Stores elements in a hash table using their hashCode().
   - No guaranteed order for iteration (elements appear in an arbitrary order).
   - Offers the best performance for add/remove/lookup operations.
- LinkedHashSet:
   - A HashSet that also maintains a doubly-linked list across its elements.
   - Iterates in insertion-order (the order in which elements were added).
   - Also includes methods to add/remove from the ends, allowing order manipulation.


















