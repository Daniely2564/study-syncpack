# Synpack

Syncpack helps you find and fix inconsistencies between every dependency defined throughout your monorepo's package.json files.

## Synpack Github Action

Link: https://jamiemason.github.io/syncpack/github-action

### Usage with Examples

Fix mismatches

App 1

```json
{
  "dependencies": {
    "lodash": "^4.17.21",
    "next": "^13.4.1",
    "next-connect": "^1.0.0",
    "typescript": "^5.0.4"
  }
}
```

App 2

```json
{
  "dependencies": {
    "lodash": "^3.0.1",
    "next": "^12.0.1",
    "typescript": "^4.1.6"
  }
}
```

#### Listing mismatching dependencies

```bash
syncpack list --source "apps/*/package.json"
```

![](<res/![](res/2023-05-08-15-58-20.png).png>)

Output

```bash
syncpack fix-mismatches --source "apps/*/package.json"
```

#### Auto fixing mismatching dependencies

```bash
syncpack fix-mismatches --source "apps/*/package.json"
```

![](res/2023-05-08-16-06-19.png)

We see that the `package.json` in the repo1 had no changes since they were all upto date. However, the `package.json` in the repo2 was all updated.

`package.json` from repo2

```json
{
  "dependencies": {
    "lodash": "^4.17.21",
    "next": "^13.4.1",
    "typescript": "^5.0.4"
  }
}
```

## Cons

Syncpack first of all doesn't have the ability to udpate `package-lock.json` file. Also, unlike dependabots, it doesn't let you know if there are newly available versions and what was the critical problem.
