```javascript
const assert = require('assert')
const satisfies = require('@metamask/spdx-satisfies')

assert(satisfies('MIT', 'MIT'))

assert(satisfies('MIT', '(ISC OR MIT)'))
assert(satisfies('Zlib', '(ISC OR (MIT OR Zlib))'))
assert(!satisfies('GPL-3.0', '(ISC OR MIT)'))

assert(satisfies('GPL-2.0', 'GPL-2.0+'))
assert(satisfies('GPL-3.0', 'GPL-2.0+'))
assert(satisfies('GPL-1.0+', 'GPL-2.0+'))
assert(!satisfies('GPL-1.0', 'GPL-2.0+'))
assert(satisfies('GPL-2.0-only', 'GPL-2.0-only'))
assert(satisfies('GPL-3.0-only', 'GPL-2.0+'))
assert(satisfies('LGPL-3.0-only', 'LGPL-3.0-or-later'))
assert(satisfies('GPL-2.0', 'GPL-2.0+'))
assert(satisfies('GPL-2.0-only', 'GPL-2.0+'))
assert(satisfies('GPL-2.0', 'GPL-2.0-or-later'))

assert(!satisfies(
  'GPL-2.0',
  'GPL-2.0+ WITH Bison-exception-2.2'
))

assert(satisfies(
  'GPL-3.0 WITH Bison-exception-2.2',
  'GPL-2.0+ WITH Bison-exception-2.2'
))

assert(satisfies('(MIT OR GPL-2.0)', '(ISC OR MIT)'))
assert(satisfies('(MIT AND GPL-2.0)', '(MIT AND GPL-2.0)'))
assert(satisfies('MIT AND GPL-2.0 AND ISC', 'MIT AND GPL-2.0 AND ISC'))
assert(satisfies('MIT AND GPL-2.0 AND ISC', 'ISC AND GPL-2.0 AND MIT'))
assert(satisfies('(MIT OR GPL-2.0) AND ISC', 'MIT AND ISC'))
assert(satisfies('MIT AND ISC', '(MIT OR GPL-2.0) AND ISC'))
assert(satisfies('MIT AND ISC', '(MIT AND GPL-2.0) OR ISC'))
assert(satisfies('(MIT OR Apache-2.0) AND (ISC OR GPL-2.0)', 'Apache-2.0 AND ISC'))
assert(satisfies('(MIT OR Apache-2.0) AND (ISC OR GPL-2.0)', 'Apache-2.0 OR ISC'))
assert(satisfies('(MIT AND GPL-2.0)', '(MIT OR GPL-2.0)'))
assert(satisfies('(MIT AND GPL-2.0)', '(GPL-2.0 AND MIT)'))
assert(satisfies('MIT', '(GPL-2.0 OR MIT) AND (MIT OR ISC)'))
assert(satisfies('MIT AND ICU', '(MIT AND GPL-2.0) OR (ISC AND (Apache-2.0 OR ICU))'))
assert(!satisfies('(MIT AND GPL-2.0)', '(ISC OR GPL-2.0)'))
assert(!satisfies('MIT AND (GPL-2.0 OR ISC)', 'MIT'))
assert(!satisfies('(MIT OR Apache-2.0) AND (ISC OR GPL-2.0)', 'MIT'))
```
