# Ordered batch processing for Explore a reversible text transform

`batch.py` accepts an outer JSON array containing separate inputs. This is an extra level of nesting when `solve` itself accepts a list. It produces one result envelope per item, preserving input order and zero-based position.

```sh
python3 batch.py < samples/batch.json
```

The batch covers these three input/output pairs:

## Case 1

Input:
```json
"Hello Python"
```

Result:
```json
"Uryyb Clguba"
```

## Case 2

Input:
```json
"Uryyb Clguba"
```

Result:
```json
"Hello Python"
```

## Case 3

Input:
```json
"你好 123"
```

Result:
```json
"你好 123"
```

## Partial failures

Each successful item has `ok: true` and `result`. A failed item has `ok: false` and an exception type; later items still run. Exit status 1 means at least one item failed, while status 2 means the batch envelope itself was invalid. An empty outer array is a valid empty batch.

ROT13 rotates Latin letters and leaves other characters unchanged. It is an educational substitution cipher, not encryption or a way to protect secrets.

The implementation processes sequentially, avoiding shared-state concurrency and keeping output order predictable. Input is limited to one MiB and 1000 items; this version materializes all results in memory. The next lesson removes that whole-batch memory requirement with line-oriented processing.
