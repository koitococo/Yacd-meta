[中文](./README_CN.md)

> Yet Another [Clash](https://github.com/yaling888/clash) [Dashboard](https://github.com/yaling888/clash-dashboard)

## Usage

Install [twemoji](https://github.com/mozilla/twemoji-colr/releases) to display emoji better on Windows system.

The site http://yacd.metacubex.one is served with HTTP not HTTPS is because many browsers block requests to HTTP resources from a HTTPS website. If you think it's not safe, you could just download the [zip of the gh-pages](https://github.com/MetaCubeX/yacd/archive/gh-pages.zip), unzip and serve those static files with a web server(like Nginx).

Proxy search supports case-insensitive JavaScript regular expressions for groups, providers and nodes. Enter the pattern without enclosing slashes, for example `HK|JP` or `^HK`. Empty input shows all results; invalid expressions match nothing.
A matching group or provider name keeps its card visible, but each node inside must still match the expression; a matching parent name does not show all its nodes. For example, `^(?!.*HK).*$` excludes nodes whose names contain `HK`.
The proxy search expression is saved in your browser's localStorage and restored automatically when you refresh the page. Clearing the search is saved too.
During search, individual and bulk collapse/expand controls share the same state; bulk actions affect only visible cards in the active tab. Changing the search resets temporary collapse overrides, and clearing it restores your saved collapse preferences.

The “Refresh status” button to the left of the latency-test button immediately fetches health-check state and latency history for all proxies and providers, regardless of the search filter or frontend query cache. It does not run new latency tests or update subscriptions; use “Test all” for active checks.

**Supported URL query params**

| Param    | Description                                                                        |
| -------- | ---------------------------------------------------------------------------------- |
| hostname | Hostname of the clash backend API (usually the host part of `external-controller`) |
| port     | Port of the clash backend API (usually the port part of `external-controller`)     |
| secret   | Clash API secret (`secret` in your config.yaml)                                    |
| theme    | UI color scheme (dark, light, auto)                                                |
| title    | Custom title for the webpage (displayed in browser tab)                            |

## Development

```sh
# install dependencies
# you may install bun from https://bun.sh
bun install

# start the dev server
# then go to http://127.0.0.1:3000
bun start


# build optimized assets
# ready to deploy assets will be in the directory `public`
bun run build
```
