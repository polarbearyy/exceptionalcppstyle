# exceptionalcppstyle
# Reading Herb Sutter Exceptional C++ Style: 40 New Engineering Puzzles, Programming Problems, and Solutions

## Remember the difference between size/resize and capacity/reserve.
## Be const correct. In particular, use const_iterator when you are not modifying the contents of a container.
## Prefer comparing iterators with !=, not <.
## Get in the habit of using the prefix forms of -- and ++ by default, unless you really need the old value.

## Practice reuse: Prefer reusing existing algorithms, particularly standard algorithms (e.g., for_each), instead of crafting your own loops.

// use std::copy
copy(v.begin(), v.end(), ostream_iterator<int>(cout, "\n"));

// more generic
template<class Container, class OutputIterator>
OutputIterator copy(const Container& c, OutputIterator result) {
 return std::copy(c.begin(), c.end(), result);
}

## Never use sprintf
