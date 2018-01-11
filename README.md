# exceptionalcppstyle
# Reading Herb Sutter Exceptional C++ Style: 40 New Engineering Puzzles, Programming Problems, and Solutions

## Chapter 1: vectors
* Remember the difference between size/resize and capacity/reserve.
* Be const correct. In particular, use const_iterator when you are not modifying the contents of a container.
* Prefer comparing iterators with !=, not <.
* Get in the habit of using the prefix forms of -- and ++ by default, unless you really need the old value.
* Practice reuse: Prefer reusing existing algorithms, particularly standard algorithms (e.g., for_each), instead of crafting your own loops.
```C++
// use std::copy
copy(v.begin(), v.end(), ostream_iterator<int>(cout, "\n"));

// more generic
template<class Container, class OutputIterator>
OutputIterator copy(const Container& c, OutputIterator result) {
 return std::copy(c.begin(), c.end(), result);
}
```
## Chapter 2: sprintf
* Never use sprintf
## Chapter 3: string formatters:
* If all you're doing is converting a value to a string (or, for that matter, to anything else!): Prefer using boost::lexical_cast by default.
* For simple formatting, or where you need wide string support or templatability: Prefer using stringstream or strstream; the code will be more verbose and harder to grasp than it would be with snprintf, but for simple formatting it won't be too bad.
* For more complex formatting, and where you don't need wide string support or templatability: Prefer using snprintf. Just because it's C doesn't mean it's off limits to C++ programmers!
* Only if actual performance measurements show that any of the better alternatives is really a bottleneck at a specific point in your code: In those isolated cases only, instead consider using whichever one of the faster alternatives strstream or snprintf makes sense.
* Never use sprintf.

## Chapter 6: flavors of genericity
* pointers into an array are always iterators, but iterators are not always pointers.

## Chapter 7: why not specialize function templates
* Two types of templates: class templates and function templates
* class templates don't overide
* function templates allow override
* primary temlates: unspecialized templates
