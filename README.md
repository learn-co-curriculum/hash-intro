## Hash Intro

### Objectives 

- What hashes are good for

### What is a hash 

A hash is a data structure that supports key-based lookup.  This means that given a key, it retrieves a value.  If there is no key, then you know that nothing has been stored at that number.    

```javascript
let hash = {foo: 'bar'}
hash['foo']
	// bar
	
hash['other']
	// undefined

```
### Why Hashes 

##### The problem with arrays 

Arrays are very good at looking up elements at a specific index.  So for example, if we want to find the element in the third slot we can access that array.  Now, this works quite well if you have an array of student gpas in descending order and you are asked, 'What is the third highest gpa in a high school class'.  We can answer this question in linear time.

```javascript 
let gpas = [3.9, 3.2, 2.1, 1.3]
gpas[2]
// 2.1
```

However, what when we want to see if a person with a given name is in a high school class.  Now, we can no longer answer the question in linear time.  Instead, we would have to look through some of the elements, perhaps by employing binary search.  This takes O(log n) time, as binary search has us cut the sorted array in half with each attempt until we find the matching elements.  So is O(log n) the fastest way for us to see if an element is in an array.

```javascript 
let students = ['Alex', 'Ian', 'Johann', 'Leigh', 'Sam', 'Steven']
binarySearch(students, 'Leigh')
// true
```

##### A Better Way

Well, maybe on second thought, there is a way.  Maybe the way to determine if an element is in an array is to pre-assign a name to a given slot.  For example, if the name Bob is in an array, it must be in the second slot.  The name Fred must be in the fifth slot.  Now, as you may notice a coupled of things.

1. First, with a large high school class, there will be too many names to simply remember precisely the index for each name.  Instead, we likely need some **formula** to know precisely where to find a given name.
2.  Second, once we present this key to our formula, and it tells us the index to examine, note that we could store whatever we want in the index.  For example, say that someone with the name Bob is always found in the third slot of the array.  We can store his gpa, or his telephone number, or whatever we want there.  That means that there bob is there, and he has the associated data that's in the slot.  To represent nothing there is no bob, we simply have nothing in the slot.  The cost of this is O(1), as once we know exactly where to look, finding the right element is not dependent on the number of elements in the collection.

That my friends, is a hash: key value pairs, and a formula to tell us given a key, where to find the associated data.  We'll explore these same concepts in more detail in the next section.

### Summary

Arrays provide a lot of use to us.  However, where they really shine is with ordered elements.  There is a slight quibble with arrays, which is that finding whether an element is in an array has us resort to binary search which occurs in O(log n) time.  Hashes allow us to see if something is in our collection of O(1) time, and we can look up an element by a key that maps to a precise location.  