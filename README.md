# [Fabien](https://github.com/fabarea)’s dotfiles

These are the basic dotfiles that I am using to start a "minimal" configuration
on a remote server. Some configuration can be overwriten in `.local` files.

## Setup

To set up the `dotfiles` just run in the terminal

```sh
bash -c "$(wget -qO - https://raw.github.com/fabarea/dotfiles-minimal/master/src/os/setup.sh)"
```

The setup process will:

* Download the dotfiles on your computer (by default it will suggest
  `~./dotfiles`)
* Create some additional [directories](src/os/create_directories.sh)
* [Symlink](src/os/create_symbolic_links.sh) the
  [`git`](src/git),
  [`shell`](src/shell), etc..-

## Cherry picking of some configuration files

Sometimes it is handy to only pick some configuration files. It can be achieved with `curl` as follows:

```
# Git configuration
curl https://raw.githubusercontent.com/fabarea/dotfiles-minimal/master/src/git/gitconfig > ~/.gitconfig

# Bash aliases
curl https://raw.githubusercontent.com/fabarea/dotfiles-minimal/master/src/shell/aliases/bash_aliases >> ~/.bash_aliases

# Editor config
curl https://raw.githubusercontent.com/fabarea/dotfiles-minimal/master/.editorconfig > .editorconfig
```

## Next step

* `nano ~/.gitconfig.local` adjust the content

```
[user]
	name = Fabien Udriot
	email = fabidule@omic.ch
	date = YYYY
```

## Customize

### Local Settings

The `dotfiles` can be easily extended to suit additional local
requirements by using the following files:

#### `~/.bash.local`

The `~/.bash.local` file it will be automatically sourced after
all the other [`bash` related files](src/shell), thus, allowing
its content to add to or overwrite the existing aliases, settings,
PATH, etc.

Here is a very simple example of a `~/.bash.local` file:

```bash
#!/bin/bash

# Set PATH additions.

PATH="$PATH:$HOME/projects/dotfiles/src/bin"

export PATH
```

## Acknowledgements

Inspiration and code was taken from many sources, including:

* [Mathias Bynens'](https://github.com/mathiasbynens)
  [dotfiles](https://github.com/mathiasbynens/dotfiles)

## License

The code is available under the [MIT license](LICENSE.txt).
