---
arguments:
- name: key
  type: key
- name: path
  optional: true
  type: string
complexity: O(1) when path is evaluated to a single value, O(N) when path is evaluated
  to multiple values, where N is the size of the key
description: Returns the type of the JSON value at path
group: json
hidden: false
linkTitle: JSON.TYPE
module: JSON
since: 1.0.0
stack_path: docs/data-types/json
summary: Returns the type of the JSON value at path
syntax_fmt: JSON.TYPE key [path]
syntax_str: '[path]'
title: JSON.TYPE
---
Report the type of JSON value at `path`

[Examples](#examples)

## Required arguments

<details open><summary><code>key</code></summary> 

is key to parse.
</details>

## Optional arguments

<details open><summary><code>path</code></summary> 

is JSONPath to specify. Default is root `$`. Returns null if the `key` or `path` do not exist.

</details>

## Return

JSON.TYPE returns an array of string replies for each path, specified as the value's type.
For more information about replies, see [Redis serialization protocol specification](/docs/reference/protocol-spec).

## Examples

{{< highlight bash >}}
redis> JSON.SET doc $ '{"a":2, "nested": {"a": true}, "foo": "bar"}'
OK
redis> JSON.TYPE doc $..foo
1) "string"
redis> JSON.TYPE doc $..a
1) "integer"
2) "boolean"
redis> JSON.TYPE doc $..dummy
{{< / highlight >}}

## See also

[`JSON.SET`](/commands/json.set) | [`JSON.ARRLEN`](/commands/json.arrlen) 

## Related topics

* [RedisJSON](/docs/stack/json)
* [Index and search JSON documents](/docs/stack/search/indexing_json)