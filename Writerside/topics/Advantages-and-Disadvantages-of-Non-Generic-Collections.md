# Advantages and Disadvantages of Non-Generic Collections

## Advantages of Non-Generic Collections
- They can store any type without restriction.
- Useful when dealing with mixed-type data.
- They were the standard before generics existed, so lots of older libraries use them.
- Sometimes convenient when type information is unknown at compile time.

## Disadvantages of Non-Generic Collections
- Require boxing/unboxing for value types, which hurts performance.
- No compile-time type safety, mistakes show up at runtime instead.
- More prone to invalid casts and subtle bugs.
- Generally slower than generic collections.
- Lack the flexibility and clarity that generic type parameters provide.
- Not recommended for modern development unless working with legacy code.