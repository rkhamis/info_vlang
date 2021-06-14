### Sum types

A sum type instance can hold a value of several different types. Use the `type`
keyword to declare a sum type:

```v
struct Moon {}

struct Mars {}

struct Venus {}

type World = Mars | Moon | Venus

sum := World(Moon{})
assert sum.type_name() == 'Moon'
println(sum)
```
The built-in method `type_name` returns the name of the currently held
type.

With sum types you could build recursive structures and write concise but powerful code on them.
```v
// V's binary tree
struct Empty {}

struct Node {
	value f64
	left  Tree
	right Tree
}

type Tree = Empty | Node

// sum up all node values
fn sum(tree Tree) f64 {
	return match tree {
		Empty { 0 }
		Node { tree.value + sum(tree.left) + sum(tree.right) }
	}
}

fn main() {
	left := Node{0.2, Empty{}, Empty{}}
	right := Node{0.3, Empty{}, Node{0.4, Empty{}, Empty{}}}
	tree := Node{0.5, left, right}
	println(sum(tree)) // 0.2 + 0.3 + 0.4 + 0.5 = 1.4
}
```

Further reading:
- [Dynamic Casts](dynamic_casts)