# Contract format, version 1

The contract is strict JSON, not a general JSON Schema or a Frictionless schema.
Unknown and duplicate properties are errors. Names and strings are case-sensitive;
the validator does not trim, infer or rewrite values.

```json
{
  "version": 1,
  "delimiter": ",",
  "ordered": true,
  "primaryKey": ["sku"],
  "fields": [
    {"name": "sku", "type": "string", "required": true},
    {"name": "price", "type": "decimal", "minimum": 0},
    {"name": "active", "type": "boolean"},
    {"name": "launch_date", "type": "date"}
  ]
}
```

| Property | Meaning and default |
| --- | --- |
| `version` | Required numeric value 1. |
| `delimiter` | One of `,`, `;`, `|`, or `\t`. Default comma. |
| `ordered` | Require the same column order as `fields`; default true. Extra/missing columns always fail. |
| `fields` | Required array of 1–128 field objects, in expected header order. |
| `primaryKey` | Optional array of 1–8 distinct declared field names. All components must be nonempty and the tuple unique. Omit for no key. |

| Field property | Meaning and default |
| --- | --- |
| `name` | Required distinct, nonblank name, max 128 characters, no control characters. Every declared column must exist even when its values are optional. |
| `type` | `string` (default), `integer`, `decimal`, `boolean`, or `date`. |
| `required` | Nonempty string required; default false. Whitespace is not treated as empty. |
| `unique` | Nonempty raw strings must be unique; default false. Empty optional values are skipped. |
| `enum` | Optional 1–200 distinct strings, each at most 1024 characters. Comparison is to the raw value; omit for no restriction. |
| `minimum`, `maximum` | Inclusive JSON-number bounds for integer/decimal only. Minimum must not exceed maximum. |
| `decimalSeparator` | `.` (default) or `,`; valid only for decimal fields. Quote comma decimals when the CSV delimiter is comma. |

Integer accepts optional `+` or `-` and digits. Decimal accepts optional sign,
digits and an optional fractional part; grouping separators, exponents, `NaN`,
leading/trailing spaces, `.5` and `1.` are rejected. Numeric values are bounded
to 1,000 characters and checked with decimal arithmetic.

Boolean accepts exactly `true` or `false`. Date accepts a valid calendar date
written `YYYY-MM-DD`. String accepts any parsed CSV text. Empty optional values
skip type, bounds, enum and uniqueness checks. `NULL`, `null` and `N/A` are ordinary
text, not missing-value aliases. Raw uniqueness means `01` and `1`, or `A` and
` A`, are different keys. No cross-field numeric comparison is supported.

Standard doubled quotes and newlines inside quoted fields are accepted. Invalid
quotes and NUL characters are rejected. A trailing line break does not add a
record; an actual blank record remains data. Header-only files pass when headers
match; add a business check outside this tool if at least one data row is required.

Reports use zero for the header record and 1 for the first data record. Line and
column are 1-based physical positions; multiline records can span several lines.
The additional `offset` is a zero-based Java text offset, not a byte position.
Editor navigation uses line/column to account for IDE line-ending normalization.

`engineVersion` is the validation-engine version (currently 0.1.0), independent
of the packaging/licensing version. `complete: false` or `valid: false` never means
a successful check. Syntax/limit errors have `CSV_SYNTAX_OR_LIMIT`; missing files
or invalid contracts instead stop the operation with an error.
