# Stacks
Stacks are first in, last out linear data structures where objects are stored either in linear memory, or are accessed linearly (ex. linked lists). Due to stacks being as fundamental as they are, they are one of the most important data structures of computer science, and being able to pop off the next element, push new ones onto the stack, and peek at the next element makes them very easy to use (Bhargava, 2016). A potential use case for stacks (other than the typical breadth first search) is to track browser history. As websites are visited by the user, the are pushed onto the stack, and then popped off when they are gone back to.

# Queues
Queues work very similarly to stacks, but are first in, first out linear data structures where where objects are stored either in linear memory or are accessed linearly (ex. linked lists). They share the fundamental actions of peek, pop, and push except pop instead pops the oldest element in the list (Bhargava, 2016). A potential use case for queues (other than the typical depth first search) is a printer job queue, where jobs are sequential and will print in the order they are added in.

# Lists
Lists are similar to arrays in how they store data with some minor differences. Lists are dynamic, allowing the developer to dynamically add more elements to the list than what was originally allocated. Lists also come with additional metadata such as length and capacity. The reason for needing this metadata is that when a list expands to accommodate more data, it doubles in capacity to hold more length due to the backing data structure for lists being an array. To be able to expand without accidentally overwriting other system memory, a new larger array must be allocated and be given the old data (Bhargava, 2016).

# Tuples
Tuples are similar to arrays where they allow for linear data to be accessed (usually 1-2 elements), and work as a convenient multi-return datatype. The issue with tuples however is that to change one value within the tuple means to replace the entire tuple value (Adali 2015). A use case for this would be returning data and a descriptor from a function to better improve error handling.

# Lexicographical Ordering
“Two strings are lexicographically equal if they are the same length and contain the same characters in the same positions” (Central Connecticut State University). This is to say that there can be no omitted or added characters, and they must all be in identical positions for two strings to evaluate to be equal. A use for this would be to sort a list of strings and improve searching performance from a linear search to even something slightly more advanced like a binary search.

# Range
The range keyword varies between programming languages, but in Python the range keyword is used to create an inclusive sequence of numbers, and even allows for stepping if specified (Parlante, 2020). For example, using range(10) returns a range type from 0 to 10 inclusive. This is helpful when iterating over the list of vacation spots from the list example, and the index is needed to neatly format the output like the following “1. Aruba, 2. Brazil”.

# Set
Sets come from mathematics where there are a series of items and none repeat (Kell, 2010). This is means that if there is a randomly generated set of numbers, none will ever repeat. Sets in Python act similarly to lists, with the exception of the add function optionally adding the entry instead of guaranteeing it. Sets could be used to upgrade the vacation list as it prevents duplicate locations as the cost of come computation.

# Dictionaries
Dictionaries are a complex data type that use multiple basic data structures to enable high speed performance and ease of use. Dictionaries, also known as hash maps, allow the programmer to set a key to the value of some data, and later give the key to the dictionary to retrieve the data. This is accomplished by using a hashing function to sort data into a list of linked list to provide quick access portions of the dictionary, while having high insertion and deletion performance (Bhargava, 2016). An example of this being helpful having a series of points on a map the user can interact with. The hash map allows for quickly looking up that specific point, and adjusting data within it.