# Clojure - Hashmaps
A hashmap is a collection that maps keys to values. They have various names
in other languages; Python refers to them as dictionaries, and Javascript's
objects essentially work like hashmaps.

A hashmap can, like many collections, be constructed in two ways. There is the
constructor function:
```clojure
;; Note that each argument is *prepended* to the hashmap, not appended.
(def a-hashmap (hash-map :a 1 :b 2 :c 3))
a-hashmap
; => {:c 3, :b 2, :a 1}
```
You can also define them using a hashmap literal. This is often more concise
and clear. Using commas to separate key/value pairs in hashmaps is recommended,
as it can make the boundaries more clear.
```clojure
;; This hashmap is actually in the right order, unlike the one above.
(def another-hashmap {:a 1, :b 2, :c 3})
another-hashmap
; => {:a 1, :b 2, :c 3}
```

## Keywords and retrieving values from hashmaps
Hold up. What is this? `:a`? `:b`? `:c`? Those look odd. Those, you see, are
keywords. They're called *key*-words because they're often used as keys in
hashmaps.

Why are they often used as keys? Well, unlike strings, keywords can be used
as functions to extract values from a hashmap; no need for `get` or `nth`!
```clojure
(def string-hashmap {"a" 1, "b" 2, "c" 3})
("a" string-hashmap)
; => ClassCastException java.lang.String cannot be cast to clojure.lang.IFn

(def keyword-hashmap {:a 1, :b 2, :c 3})
(:a keyword-hashmap)
; => 1

;; You can also pass a keyword a default value in case it's not found, just like get.
(:not-in-the-hashmap keyword-hashmap "not found!")
; => "not found!"
```

## Converting other collections to hashmaps
Converting to a hashmap is tricky. To demonstrate, let's try using it like `vec`
or `seq`.
```clojure
(hash-map [:a 1 :b 2 :c 3])
; => IllegalArgumentException No value supplied for key: [:a 1 :b 2 :c 3]
```
The `hash-map` function thinks that we're trying to create a hashmap with
`[:a 1 :b 2 :c 3]` as one of the keys. Watch what happens if we give it the
right number of arguments:
```clojure
(hash-map [:a 1 :b 2 :c 3] "foo")
; => {[:a 1 :b 2 :c 3] "foo"}
```
To convert a sequence to a hashmap, you'll need to use and understand `apply`.
Luckily, this is pretty simple: `apply` essentially destructures a collection
before applying a function to it.
```clojure
;; These two expressions are exactly the same.
(+ 1 2 3)
; => 6
(apply + [1 2 3])
; => 6
```
This is how you would convert a vector to a hashmap:
```clojure
(apply hash-map [:a 1 :b 2 :c 3])
; => {:c 3, :b 2, :a 1}

;; This is the same as:
(hash-map :a 1 :b 2 :c 3)
; => {:c 3, :b 2, :a 1}
```
:rocket: [IDEOne it!](https://ideone.com/k9cOjo)

## Update a hashmap
You can update values inside a hashmap using `assoc`. This allows you to append
new key/value pairs or change old ones.
```clojure
(def outdated-hashmap {:a 1, :b 2, :c 3})

(def newer-hashmap (assoc outdated-hashmap :d 4))
newer-hashmap
; => {:a 1, :b 2, :c 3, :d 4}

(def newest-hashmap (assoc newer-hashmap :a 22))
newest-hashmap
; => {:a 22, :b 2, :c 3, :d 4}

;; Note that outdated-hashmap has not been mutated by any of this.
;; Assoc is pure and functional.
outdated-hashmap
; => {:a 1, :b 2, :c 3}
```

## When to use a hashmap?
A hashmap is useful when you want to give names to your variables. If you're
ever thinking to yourself, *"What if I used an object..."* before you snap out
of it and realise you're using Clojure, try using a hashmap.

They are also useful if you want to associate two different values with each other.
Take, for example, a ROT13 cipher: you could associate `\A` with `\N`, `\B` with
`\M`, etc. (This would be long and boring to write in most languages, but Clojure
has some functions that can generate it for you and make it *fun!*)

| [:point_left: Previous](Clojure-Vectors) | [:book: Home :book:](Clojure) | Next :point_right: |
|:---|:---:|----:|
| [Vectors](Clojure-Vectors) | [Table of Contents](Clojure) | To Be Added |