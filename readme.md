# js-jsonl

[![npm version](https://img.shields.io/npm/v/js-jsonl)](https://npmjs.com/package/js-jsonl)

## Installation

```shell
npm install js-jsonl
```

## Usage

```typescript
import { jsonl } from 'js-jsonl';

const jsonlString = `
  ["Name", "Session", "Score", "Completed"]
  ["Gilbert", "2013", 24, true]
  ["Alexa", "2013", 29, true]
  ["May", "2012B", 14, false]
  ["Deloise", "2012A", 19, true]
`;

const jsonlParsed = [
  ["Name", "Session", "Score", "Completed"],
  ["Gilbert", "2013", 24, true],
  ["Alexa", "2013", 29, true],
  ["May", "2012B", 14, false],
  ["Deloise", "2012A", 19, true]
];

expect(jsonl.parse(jsonlString)).toEqual(jsonlParsed);
expect(jsonl.stringify(jsonlParsed)).toEqual(jsonlString);

// Also works with TypeScript!

const fooBar = jsonl.parse<{ foo: 'bar' }>("{foo: 'bar'}");
const fooBarString = jsonl.stringify(fooBar)
const fooBarParsed: { foo: 'bar' } = jsonl.parse(fooBarString); // no type error!
```

You can also use the `JsonlInfer<T>` helper to extract the JSONL type:

```typescript
import { jsonl } from 'js-jsonl';
import type { JsonlInfer } from 'js-jsonl';

const fooBar = jsonl.parse<{ foo: string }>("{foo: 'bar'}\n{foo: 'baz'}");
type FooBarParsed = JsonlInfer<typeof fooBar> // { foo: string }
```

