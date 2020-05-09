#### Non-static methods
Methods are a special case of function in Rust because of the self argument, which doesn't have a declared type.
```$xslt
fn foo(self, arg2: Type2) -> ReturnType {
    // body
}
```

There are 3 primary forms that `self` can take: `self`, `&mut self` and `&self`. 
These 3 forms represent the three primary forms of ownership in Rust.

* `self` - Value
* `&mut self` - mutable reference
* `&self` - shared reference. 

#### `self`
1. A value represents _true_ ownership. You can do whatever you want ot with  a value:
move it, destroy it, mutate it, or loan it out via a reference.
2. When you pass something by value, it's moved to the new location. the new location now owns the value, and the old location can no longer access it.
3. For this reason most methods don't want `self` -- it would be pretty lame if trying to work with a list made it go away!

#### `&mut self` 
_alias: &mut, mut ref...._
1. A mutable reference represents temporary exclusive access to a value that you don't actually own.
2. You're allowed to do absolutely anything you want to a value you have `mut ref` to as long you leave it in a valid state when you are done.
3. The only thing you can't do with an `&mut` is move the value out with no replacement.
`&mut self` is great for methods that want to mutate `self`.

#### `&self`
_alias: ref_ 

1. A shared reference represents temporary _shared access_ to a value that you don't own.
2. Because you have a shared access, you'are not allowed to mutate anything.
3. `&` is great for methods that only want to observe `self`.

_analogy: Think of `&` as putting the value out on display in a museum._
