# What this revival changed

`kosmos/awesome-generative-art` has not taken a commit since January 2022. This
fork carries the maintenance and runs the gate from
<https://github.com/olitreadwell/awesome-list-template>.

## The readme

- The awesome badge pointed at `cdn.rawgit.com`, a dead CDN. It points at
  awesome.re and sits on the heading line, which is where the linter wants it.
- The readme ended with a License section. The linter forbids one, so `LICENSE`
  holds the CC0 1.0 legal code that section described and the heading is gone.
- `Contribute` and `Support on Beerpay` were listed as sections that hold
  entries. Both are prose, so both are out of `awesome.toml`.
- The Contents block was rebuilt by `make toc`.

## Entries

Ninety-six entries carried a bracketed marker (`[Mac, Win]`, `[history]`,
`[p5.js]`) in place of a description, so the link and the rest of the line had
no separator and the line had no closing period. Each took the same mechanical
repair: insert ` - ` after the link, then keep the marker exactly as upstream
wrote it. The brackets are escaped, because the linter reads `[Win]` as a
reference link to a definition that does not exist:

```diff
-- [vvvv](https://vvvv.org/) [Win]
+- [vvvv](https://vvvv.org/) - \[Win\].
```

No marker lost or gained a word. One marker, `[history]` on the Code as Creative
Medium entry, was missing its opening bracket upstream and has it back.

- The Coursera course "The Arduino Platform and C Programming" was listed twice
  in the same Lectures section, once bare and once with the `[arduino]` marker.
  The bare copy is gone.
- `resonate.io` moved from http to https.
- Five links stay on http and sit in `links.allowlist`: ptahi.ru and
  csounds.com answer on http only, and the CoGe VJ page, `modul8.ch`, and one
  lulu.com product page are gone. imimot.com and garagecube.com are still up, so
  a maintainer may want to repoint those two rather than drop them.

Left alone:

- 72 entries came from upstream with a title and nothing else. The gate warns
  about them and `tests/test_readme.py` holds the count still.
- Three spell-check warnings stay, two of them inside markers (`ios`, `webgl`).

## Link rot this fork knows about

`make links` reports 15 dead or blocked links out of 198. The notable ones:

- `beerpay.io` fails its TLS handshake, so the whole "Support on Beerpay"
  section is dead. It is left as upstream wrote it.
- `genart.herokuapp.com` and two `lynda.com` course pages return 404. Lynda
  redirects to LinkedIn Learning, which then 404s.
- `coursera.org/learn/music-technology` and one YouTube list return 404.

## Tooling

The fork runs the same gate the engine ships, pinned to engine revision
`311c719`. `make check` covers the list rules, the Contents block, the GitHub
stars and activity snapshot, the exports, and the tests in
`tests/test_readme.py`.
