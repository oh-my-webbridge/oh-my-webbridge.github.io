# oh-my-webbridge (https://oh-my-webbridge.github.io/en/)

A command from an agent or a script runs in your ordinary Chrome or Firefox profile, so pages keep that profile's logins, cookies and extensions. The daemon runs on the same computer as the browser and listens only on `127.0.0.1:17373`.

1. An agent or script sends a command through `omw call` or the SDK.
2. The `omw` daemon checks the token and forwards the command over a WebSocket to an extension in one browser.
3. The extension runs the command in a tab and returns JSON.

One daemon serves Chrome and Firefox at the same time. Each browser is paired once, and its extension stores the token.

<Demo
  name="activity-form"
  alt="An agent fills a form while the page shows an edge glow, a focus frame on the active field and typed text."
/>

## What an agent can do [#what-an-agent-can-do]

- Open tabs in the background, in one tab group per session. The group title comes from `group_title` or the session name. Tab groups only separate tasks on screen; every tab shares the profile and its cookies.
- Read a page as text (`read_page`) or as an accessibility snapshot with `@e` references that later actions target (`snapshot`).
- Click, type and fill form fields. Chrome sends this input through the DevTools protocol, so pages receive trusted events; Firefox sends clicks and key presses as untrusted events that a page may ignore.
- Take screenshots in either browser, and save a page as PDF in Chrome.
- Read network requests in either browser, and console messages in Chrome.
- Send raw CDP commands in Chrome when no action covers the task.

## Where to go next [#where-to-go-next]

- [Getting started](https://oh-my-webbridge.github.io/en/getting-started/): install the daemon and the extension, pair a browser and run the first commands.
- [Sessions and tabs](https://oh-my-webbridge.github.io/en/sessions/): one session per task, with its own tabs and tab group.
- [Agent activity](https://oh-my-webbridge.github.io/en/activity/): the glow, focus frame and toolbar icon that mark a tab an agent controls.
- [Actions](https://oh-my-webbridge.github.io/en/reference/actions/): every action, its arguments and the errors it returns.
