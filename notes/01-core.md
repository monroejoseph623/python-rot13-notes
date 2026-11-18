# Explore a reversible text transform: implementation

## What the example does

ROT13 rotates Latin letters and leaves other characters unchanged. It is an educational substitution cipher, not encryption or a way to protect secrets.

The public function is `solve(value)`. The JSON input contract can be seen in this concrete example:

```json
"Hello Python"
```

Expected result:

```json
"Uryyb Clguba"
```

Run `python3 example.py` for the Python representation of the result. `solution.py` contains the full implementation and can also be imported by another script.

## Scope

The function implements exactly the behavior described above. It does not perform network or filesystem access. Python exceptions indicate unsupported input; the next lesson turns them into a command-line error response. Review the limitations before reusing it in an application.
