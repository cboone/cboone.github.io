---
date: 2026-01-22
description: "Type-safe assertion functions for Go tests"
externalUrl: "https://github.com/cboone/attest"
title: "Attest"
---

Type-safe assertion functions for Go tests. Requires Go 1.21+.

## Installation

```go
go get github.com/cboone/attest
```

## Assertions

**Equality**: `Equal`, `NotEqual`, `DeepEqual` with support for `cmp.Option` via `WithCmpOpts`.

**Nil checking**: `Nil` and `NotNil`, handling typed nils correctly.

**Strings**: `Contains`, `HasPrefix`, `HasSuffix`, `EqualFold`, `Matches` (regex).

**Collections**: `Len`, `Empty`, `NotEmpty`, `ContainsElement`, `HasKey`.

**Errors**: `NoError`, `IsError`, `ErrorIs`, `ErrorAs`, `ErrorContains`.

**Golden files**: Compare output against reference files in `testdata/golden/` using `Golden` and `GoldenBytes`. Update reference files with the `-attest.update` flag.

## Fatal assertions

For test-stopping failures, use `Must(t)` for method-based calls or `MustXxx` package-level functions:

```go
attest.Must(t).NotNil(conn)
attest.MustEqual(t, 42, result)
```

## See also

### [testify](https://github.com/stretchr/testify)

The most widely-used Go assertion library. Attest takes a different approach with type safety and a smaller API surface.
