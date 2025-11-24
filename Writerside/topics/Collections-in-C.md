# Collections in C#

Collections are groups of records that can be treated as one unit.

The Collections in C# are a set of predefined classes that are present in the 
**System.Collections** namespace that provides greater capabilities and functionalities than the traditional arrays.

**Collections are C# built in data structures**.

## General Categories of Collections
Collections are classified into 4 types:
1. Index Based Collections
    - Array
    - List
    - ArrayList
2. Key Value Pair Collections
    - Hashtable
    - SortedList
    - Dictionary
3. Prioritized Collections
    - Stack
    - Queue
4. Specialized Collections
    - String Collections
    - Hybrid Collections

## Types of Collections in C#
There are three ways to work with collections in C#.

- **Non-Generic Collections** - live under `System.Collections` namespace.
- **Generic Collections** - live under `System.Collections.Generic` namespace.
- **Concurrent Collections** - live under `System.Collection.Concurrent` namespace.

### Non-Generic Collections
The Non-Generic Collection Classes come with C# 1.0 and are defined under the `System.Collections` namespace.

They store items as `object` and hence can handle any type of data, but not in a type-safe manner.

It has the following classes:
- ArrayList
- Stack
- Queue
- Hashtable
- SortedList

### Generic Collections
The Generic Collection Classes come with C# 2.0 and are defined under the `System.Collection.Generic` namespace.

They are type-safe, faster, avoid boxing, modern and standard.

They include:
- List<T>
- Stack<T>
- Queue<T>
- HashSett<T>
- Dictionary<TKey, TValue>
- SortedList<TKey, TValue>
- SortedSet<T>
- SortedDictionary<TKey, TValue>
- LinkedList<T>

### Concurrent Collections
Provides various threads-safe collection classes that are used in place of the corresponding types 
in the `System.Collections` and `System.Collections.Generic` namespaces, when multiple threads 
are accessing the collection simultaneously.

It provides classes for thread-safe operations, so that multiple threads will not create problems when accessing
the collection items.

It has the following classes:
- BlockingCollection<T>
- ConcurrentBag<T>
- ConcurrentStack<T>
- ConcurrentQueue<T>
- ConcurrentDictionary<TKey, TValue>