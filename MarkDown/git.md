## Configuration

```
git config --global user.name "<your_name>"
git config --global user.email <your_email_address>

git config --global core.editor vim|"code --wait" # set default editor respectively, to vim, or vs-code
git config --global -e # opens the default editor

git config --global core.autocrlf input|true # respectively on Linux, or windows

git config --global color.ui true # make the output colorful
git config --global push.default current


git config --global diff.tool meld
```

## Useful commands

```
git <command> --help|-h 
```

## Getting Started

`git init`
`git clone url`

## Basics

```shell
git status
git add <file>?
git add .
git commit -m "<meaningful_message>"
git commit # opens the default editor
git commit -a -m "<message>"
```
