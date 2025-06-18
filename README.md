# Minimal example of multiinclude bug

## pre-commit

1. Install pre-commit

    ```sh
    pre-commit install
    ```

2. Run pre-commit

    ```sh
    pre-commit run --all-files
    ```

Output:

```text
Advanced oelint..........................................................Failed
- hook id: oelint-adv
- exit code: 1

/minimal-multiinclude/meta-test/meta-append2/recipes-extended/images/image-debug.bbappend:1:warning:oelint.var.multiinclude:'append2-image.inc' is included multiple times [branch:true]
/minimal-multiinclude/meta-test/meta-append1/recipes-extended/images/image-debug.bbappend:1:warning:oelint.var.multiinclude:'append-image.inc' is included multiple times [branch:true]
```

## oelint-adv

Run `oelint-adv **/* --rulefile=.oelint-ruleset.json --quiet`.

Output:

```text
/minimal-multiinclude/meta-test/meta-append1/recipes-extended/images/image-debug.bbappend:1:warning:oelint.var.multiinclude:'append-image.inc' is included multiple times [branch:true]
/minimal-multiinclude/meta-test/meta-append2/recipes-extended/images/image-debug.bbappend:1:warning:oelint.var.multiinclude:'append2-image.inc' is included multiple times [branch:true]
/minimal-multiinclude/meta-test2/meta-append3/recipes-extended/images/image-debug.bbappend:1:warning:oelint.var.multiinclude:'append3-image.inc' is included multiple times [branch:true]
/minimal-multiinclude/meta-test2/meta-append4/recipes-extended/images/image-debug.bbappend:1:warning:oelint.var.multiinclude:'append4-image.inc' is included multiple times [branch:true]
```
