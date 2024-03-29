# hoshi
A data serialisation library.

Work in progress.

### Representing schemas
A schema describes the content of a single unit (message).

It looks like this:

    {
        "version": <version>,
        "encoding": <encoding>,
        "meta": <metadata>
    }

`<metadata>` is a JSON object which may carry arbitrary data.

For now, the only valid `<version>` is `"0"` and the only valid `<encoding>`
is `"json"`. More encodings may be added in the future.

### Representing data types

| Datum           | JSON                              |
| --------------- | --------------------------------- |
| basic type      | `{ "kind": "type-basic", "sub": "<basic type name>"` |
| literal type    | `{ "kind": "type-literal", "value": <any JSON value> }` |
| union type      | `{ "kind": "type-union", "alts": [ <type> ... <type> ] }` |
| map type        | `{ "kind": "type-map", "key": <type>, "value": <type> }` |
| list type       | `{ "kind": "type-list", "value": <type> }` |
| tuple type      | `{ "kind": "type-tuple", "fields": <list of types> }` |
| struct type     | `{ "kind": "type-struct", "fields": <map from field names to types> }` |

Types may also have a `"meta"` field which is a JSON object containing
metadata.

Valid basic type names: `void`, `null`, `bool`, `int`, `float`, `string`

## API documentation

See the readmes in the respective language directories.
