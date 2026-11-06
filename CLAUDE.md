# navi-cheats

Personal [navi](https://github.com/denisidoro/navi) cheatsheets, one `<tool>.cheat` file per tool in the repo root. Cheatsheets are not code, so there's no build or test suite.

## Writing cheatsheets

- Start with a `% tool, tags` line. Follow it with `# description` and command pairs, then `; Gotchas`, and put `$ var:` suggestions last. Use `mitmproxy.cheat` as the style reference.
- Run every command against sample data in a temp directory, and read the output before adding it. Commands can exit 0 and still do nothing, such as `mlr fill-down -a`. Test gotchas too, rather than writing them from memory.
- Write for the version installed here, and check with `--version` first. `yq` is mikefarah/yq (Go, v4), which is not fully jq-compatible.
- navi inserts values as typed, so an apostrophe breaks `'<value>'`. Use double quotes where the shell would otherwise break, such as `VALUE="<value>" yq ...`.
- navi can hang without a terminal. When testing through navi, use `timeout` and `script`, and set variables through the environment: `value=x timeout 8 script -qec "navi --print --best-match --query '...'" /dev/null`

## Publishing

Push cheatsheets to `master`, since `navi repo add` clones the default branch. It imports a one-time copy, so changes only reach navi when the import is run again.
