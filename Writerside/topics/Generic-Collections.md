# Generic Collections

The .NET Framework has re-implemented all the existing Non-Generic Collection classes such as `ArrayList`, `Hashtable`, 
`SortedList`, `Stack`, and `Queue`., etc. in Generic Collections such as `ArrayList<T>`, `Dictionary<TKey, TValue>`, 
`SortedList<TKey, TValue>`, `Stack<T>`, and `Queue<T>`.

While creating the objects of Generic Collection Classes, you need to explicitly provide the type of
values that you are going to store in the collection.

Here T is nothing but the type of values that we want to store in the collection.

The Generic Collection Classes are implemented under the `System.Collections.Generic` namespace.

The classes which are present in the namespace are as follows:
1. **`Stack<T>`**: It represents a variable size last-in-first-out (LIFO) collection of instances of the
same specified type.
2. **`Queue<T>`**: It represents a first-in, first-out collection of objects. 
3. **`HashSet<T>`**: It represents a set of values. It eliminates duplicate elements.
4. **`SortedList<TKey, TValue>`**: It represents a collection of key/value pairs that are sorted by key, it automatically
adds elements in ascending order of the key.
5. **`List<T>`**: It represents a strongly typed list of objects that can be accessed by index. Provides methods to 
search, sort, and manipulate lists. It grows automatically as you add elements to it.
6. **`Dictionary<TKey, TValue>`**: It represents a collection of keys and values.
7. **`SortedSet<T>`**: It represents a collection of objects that are maintained in sorted order.
8. **`SortedDictionary<TKey, TValue>`**: It represents a collection of key/value pairs that are sorted on the key.
9. **`LinkedList<T>`**: It represents a doubly linked list.

Here the `<T>` refers to the type of values we want to store under them.