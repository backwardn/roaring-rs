# RoaringBitmap [![Travis CI Build Status][]][travis]

> This is not yet production ready.

This is a [Rust][] port of the [Roaring bitmap][] data structure, initially
defined as a [Java library][roaring-java] and described in [_Better bitmap
performance with Roaring bitmaps_][roaring-paper].

## Developing

Take note of the [Collections reform RFC][collections-rfc] for the API.  Mostly aiming to
duplicate the [BitvSet][] API.

### TODO

  - [ ] Bounded Iterators ([§ in the RFC][bounded-iterators])
    - [ ] `fn range(&self, min: Bound<&T>, max: Bound<&T>) -> RangedItems<'a, T>;`
  - [X] Set Operations ([§ in the RFC][set-operations])
    - [X] Comparisons
      - [X] `fn is_disjoint(&self, other: &Self) -> bool;`
      - [X] `fn is_subset(&self, other: &Self) -> bool;`
      - [X] `fn is_superset(&self, other: &Self) -> bool;`
    - [X] Combinations
      - [X] Iterated Functions
        - [X] `fn union<'a>(&'a self, other: &'a Self) -> I;`
        - [X] `fn intersection<'a>(&'a self, other: &'a Self) -> I;`
        - [X] `fn difference<'a>(&'a self, other: &'a Self) -> I;`
        - [X] `fn symmetric_difference<'a>(&'a self, other: &'a Self) -> I;`
      - [X] Operator Traits
        - [X] `std::ops::BitOr`
        - [X] `std::ops::BitAnd`
        - [X] `std::ops::Sub`
        - [X] `std::ops::BitXor`
      - [X] Inplace Functions
        - [X] `fn union_with(&mut self, other: &BitvSet)`
        - [X] `fn intersect_with(&mut self, other: &BitvSet)`
        - [X] `fn difference_with(&mut self, other: &BitvSet)`
        - [X] `fn symmetric_difference_with(&mut self, other: &BitvSet)`

[Travis CI Build Status]: https://img.shields.io/travis/Nemo157/roaring-rs.svg?style=flat-square
[travis]: https://travis-ci.org/Nemo157/roaring-rs
[Rust]: https://rust-lang.org
[Roaring bitmap]: http://roaringbitmap.org
[roaring-java]: https://github.com/lemire/RoaringBitmap
[roaring-paper]: http://arxiv.org/pdf/1402.6407v4
[collections-rfc]: https://github.com/rust-lang/rfcs/pull/235
[BitvSet]: http://doc.rust-lang.org/std/collections/bitv_set/struct.BitvSet.html
[bounded-iterators]: https://github.com/aturon/rfcs/blob/collections-conventions/text/0000-collection-conventions.md#bounded-iterators
[set-operations]: https://github.com/aturon/rfcs/blob/collections-conventions/text/0000-collection-conventions.md#set-operations
