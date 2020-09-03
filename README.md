[//]: # ( )
[//]: # (This file is automatically generated by a `metapak`)
[//]: # (module. Do not change it  except between the)
[//]: # (`content:start/end` flags, your changes would)
[//]: # (be overridden.)
[//]: # ( )
# schema2dts
> A very simple JSONSchema7/OpenAPI3 to TypeScript types definitions generator

[![NPM version](https://badge.fury.io/js/schema2dts.svg)](https://npmjs.org/package/schema2dts)
[![Dependency Status](https://david-dm.org/nfroidure/schema2dts.svg)](https://david-dm.org/nfroidure/schema2dts)
[![devDependency Status](https://david-dm.org/nfroidure/schema2dts/dev-status.svg)](https://david-dm.org/nfroidure/schema2dts#info=devDependencies)
[![Package Quality](https://npm.packagequality.com/shield/schema2dts.svg)](https://packagequality.com/#?package=schema2dts)


[//]: # (::contents:start)

It is intended to support JSONSchema7/OpenAPI3 but may work for some if not most
JSONSchema versions.

This module assumes your JSONSchema / OpenAPI3 documents are valid. It also
doesn't support external references at the moment and expect a single object
whose definitions are all relative to the root object.

It is also meant to be a building block for higher level generators.

## Usage

```ts
import { readFileSync, writeFileSync } from 'fs';
import {
  generateJSONSchemaTypes,
  generateOpenAPITypes,
  buildIdentifier,
  toSource,
} from '.';

// Open API
const openAPISchema = JSON.parse(readFileSync('openapi.json').toString());

writeFileSync('API.d.ts', toSource(await generateOpenAPITypes(openAPISchema)));

// JSON Schema
const jsonSchema = JSON.parse(readFileSync('schema.json').toString());

writeFileSync('API.d.ts', toSource(await generateJSONSchemaTypes(jsonSchema)));
```

If you find some case with unexpected results, please add the fixtures to this
repository in a pull request and describe the problem you encounter.

[//]: # (::contents:end)

# Authors
- [Nicolas Froidure](https://insertafter.com/en/index.html)

# License
[ISC](https://github.com/nfroidure/schema2dts/blob/master/LICENSE)
