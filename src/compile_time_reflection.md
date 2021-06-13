## Compile-time reflection

Having built-in JSON support is nice, but V also allows you to create efficient
serializers for any data format. V has compile-time `if` and `for` constructs:

```v wip
// TODO: not fully implemented

struct User {
    name string
    age  int
}

// Note: T should be passed a struct name only
fn decode<T>(data string) T {
    mut result := T{}
    // compile-time `for` loop
    // T.fields gives an array of a field metadata type
    $for field in T.fields {
        $if field.typ is string {
            // $(string_expr) produces an identifier
            result.$(field.name) = get_string(data, field.name)
        } $else $if field.typ is int {
            result.$(field.name) = get_int(data, field.name)
        }
    }
    return result
}

// `decode<User>` generates:
fn decode_User(data string) User {
    mut result := User{}
    result.name = get_string(data, 'name')
    result.age = get_int(data, 'age')
    return result
}
```

