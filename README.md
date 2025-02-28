# Geotribu Mastodon auto export

[![💾 Export Geotribu Mastodon accounts and lists](https://github.com/geotribu/geo-mastodon-comptes-listes/actions/workflows/export-mastodon-list.yml/badge.svg)](https://github.com/geotribu/geo-mastodon-comptes-listes/actions/workflows/export-mastodon-list.yml)

This project aims to automate the export of Mastodon lists and followed accounts to CSV format, ensuring simplified data retrieval and periodic storage. Generated files are published on GitHub Pages <https://geotribu.github.io/geo-mastodon-comptes-listes/>.

![Mastodon export - File explorer result](https://cdn.geotribu.fr/img/articles-blog-rdp/articles/2024/transition_mastodon/mastodon_lists_explorer.png)

There is no real logic code here, only CI/CD (YAML) workflow which is run monthly or manually.  
Under the hood, it's just the [geotribu cli](https://pypi.org/project/geotribu/)

## How to import lists and accounts

This project is a follow-up of the article [Mastodon: how to export lists and accounts](https://geotribu.fr/articles/2024/transition-mastodon/) (in French, but [Firefox Translate](https://support.mozilla.org/en-US/kb/website-translation) is your friend) where the rationale behind and how to import files is described.

## How to use it with your Mastodon account

### Locally

> [!NOTE]
> [pipx](https://pipx.pypa.io/) is a modern tool that make it simpler to install and perform common post-install operations (as registering the CLI in your PATH, etc.)

1. Install the geotribu CLI:

    ```sh
    pipx install 'geotribu>=0.32'
    # or with pip
    pip install -U 'geotribu>=0.32'
    ```

1. Generate an API key for your Mastodon account `https://your_mastodon_insctance/settings/applications/` with the minimal following scopes:

    - [x] `read:accounts`
    - [x] `read:follows`
    - [x] `read:lists`

1. Store it as environment variable:

    ```sh
    export GEOTRIBU_MASTODON_API_ACCESS_TOKEN=mastodon_api_key
    # on Windows cmd
    set GEOTRIBU_MASTODON_API_ACCESS_TOKEN=mastodon_api_key
    # on Windows PowerShell
    $Env:GEOTRIBU_MASTODON_API_ACCESS_TOKEN = 'mastodon_api_key'
    ```

1. Run it:

    ```sh
    geotribu social mastodon-export -w ./export-mastodon
    ```
