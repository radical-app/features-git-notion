Git Notion
==========

Syncs Github markdown files in your repository to Notion.

This utility is described in the following [blog post](https://www.swiftlane.com/blog/syncing-docs-from-code-repositories-to-notion/).

See example [Notion page](https://www.notion.so/git_feature_notion-195c08d3d14140eb9a35ac00f9a0f078).

## Installation
```
pip install git-feature-notion
```

or for local installation:

```bash
git clone https://github.com/NarekA/git-feature-notion.git
cd git-feature-notion
pip install -e .
```

## Configuring

`NOTION_TOKEN_V2` - Can be found in your [browser cookies](https://www.redgregory.com/notion/2020/6/15/9zuzav95gwzwewdu1dspweqbv481s5) for Notion's website.
`NOTION_ROOT_PAGE` - URL for notion page. Repo docs will be a new page under this page.
`NOTION_IGNORE_REGEX` - Regex for paths to ignore.
`NOTION_SEARCH_BY_REGEX` - Regex for pattern for file search.

These environment variables can be set.
```bash
export NOTION_TOKEN_V2=<YOUR_TOKEN>
export NOTION_ROOT_PAGE="https://www.notion.so/..."  # Can be in setup.cfg as well
export NOTION_IGNORE_REGEX="models/.*"               # Can be in setup.cfg as well
export NOTION_SEARCH_BY_REGEX="**/*.md"              # Can be in setup.cfg as well
```

These parameters can be set in the `setup.cfg` for the repo.
```
[git-feature-notion]
ignore_regex = models/.*
notion_root_page = https://www.notion.so/...
search_by_regex = "**/*.md"
```

## Usage

```bash
# To upload your current directory
git-feature-notion

# To upload another directory
git-feature-notion --path path/to/your/repo
```


## Pushing to PYPI

```bash
bumpversion patch   # Look-up bumpversion
rm -rf dist/
python3 setup.py sdist bdist_wheel
python3 -m twine upload dist/*
```
