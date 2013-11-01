# automator

## Services
- GitHub Markdown to Chrome
    - Takes the selected text and POSTs it to the GitHub [Raw Markdown service][github api] to convert [GitHub Flavored Markdown][github md] to HTML and then loads it in [Chrome][].
    - Repeating calls to this service will reload the existing page in the same tab.
- GitHub Markdown to Evernote
    - Takes the selected text and POSTs it to the GitHub [Raw Markdown service][github api] to convert [GitHub Flavored Markdown][github md] to HTML and uses it to create a new note in [Evernote][].

## Installation
- Clone the parent repository
- Double click on the service file
- When prompted select 'Install'
- You should see confirmation that the service install is complete
    - Services typically install in the `~/Library/Services/` directory
    - **Note** the automator file will be moved from whatever location it's currently in to the above location

### GitHub personal token
There is a rate limit on unauthenticated request to the GitHub API. Authenticated requests have a much higher [rate limit][github limit]. In order to avoid this, any service that uses GitHub can be updated to optionally provide a personal acces token. For more about personal access tokens see GitHub's pages on [authentication][github auth].

To update the actions to provide a personal access token:
- Open the desired service in Automator
- There should be a "Run Shell Script" step somewhere in the action
    - At the top of the action there will be the line:
    `#$personalAccessToken="--user PERSONAL_ACCESS_TOKEN:x-oauth-basic"`
- Uncomment this line by removing the '#'
- Replace 'PERSONAL_ACCESS_TOKEN'
- Save the automator action.

### Keyboard Shortcuts
Sometimes it's painful to have to dig into menus to trigger an Automator service. However through `System Preferences -> Keyboard` you can easily setup a shortcut to any of the Services on your system.

[github api]: <http://developer.github.com/v3/markdown/#render-a-markdown-document-in-raw-mode>
[github md]: <https://help.github.com/articles/github-flavored-markdown>
[github auth]: <http://developer.github.com/v3/auth/#basic-authentication>
[github limit]: <http://developer.github.com/v3/#rate-limiting>
[chrome]: <http://google.com/chrome>
[evernote]: <http://evernote.com>