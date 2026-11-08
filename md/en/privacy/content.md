# Privacy (https://oh-my-webbridge.github.io/en/privacy/)

> **Developer preview**
>
> omw is in developer preview and iterating rapidly. **THERE WILL BE COMPATIBILITY-BREAKING CHANGES.**

The browser extension and the omw daemon run on your computer. The project runs no server and receives no data from either of them.

## Data the extension reads [#data-the-extension-reads]

To carry out a command from the daemon, the extension reads data from the browser. Depending on the command, it reads:

- the address, title and content of pages in the tabs a session uses, or in a tab that a [CDP](https://oh-my-webbridge.github.io/md/en/reference/cdp/content.md) client connects to: text, the accessibility tree, element values, screenshots and PDFs
- cookies and page storage, for the `cookies` and `storage` actions
- the requests and responses of a tab while a session records its network traffic
- the addresses and titles of open tabs, for the CDP target list (`/json/list`) and when a session looks for a tab to borrow

When you open the popup, it reads the address and title of the active tab. On a page that the extension can access, it also reads the page language, the structured-data types, the length of the selected text, and how many tables, form fields, code blocks, videos, images and articles the page has. The popup uses these values to rank prompt suggestions and does not send them anywhere.

## Where the data goes [#where-the-data-goes]

After pairing, the extension connects to one address: the daemon at `127.0.0.1:17373` on the same computer. It sends each result there and to no other address. The daemon accepts connections from the same computer only and returns the result to the program that sent the command, such as an agent or a script. That program decides what happens to the data next; an agent can pass page content to its model provider.

## Data on disk [#data-on-disk]

- The extension keeps the daemon token and its settings in the browser's extension storage. Session state lives in session storage, which the browser clears when it restarts.
- The daemon keeps its configuration, including the token, and the session bindings in its configuration directory: `~/Library/Application Support/oh-my-webbridge` on macOS, `~/.config/oh-my-webbridge` on Linux, or the directory in `OMW_HOME`. Screenshots and PDFs go to the path given in the command, or to `artifacts` in that directory.
- Files that the `download` action saves go to the browser's download folder.

## Analytics [#analytics]

The extension and the daemon contain no analytics, telemetry, crash reporting or advertising. The filter lists for [page presets](https://oh-my-webbridge.github.io/md/en/presets/content.md) ship inside the extension; nothing is downloaded at run time.

## Questions [#questions]

Ask privacy questions in [GitHub Issues](https://github.com/oh-my-webbridge/oh-my-webbridge/issues).
