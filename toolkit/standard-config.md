# Standard Configuration

Local development machine configuration is a matter of individual choice; as developers we are constantly optimizing our work environment.

This document serves to capture the "recommended setup" or standard configuration that we use. These are recommendations, not requirements.

## Hardware

- Mac computer
- 2.5GHz+ processor
- 4GB+ RAM

## Prerequisites

- [Docker Toolbox][docker-toolbox]

## Env Setup & Management (via Docker image)

- [rbenv][rbenv] and [ruby-build][ruby-build] for managing Ruby versions
- [nvm][nvm] and [npm][npm] for managing Node.js versions and packages

## Runtimes (via Docker image)

- Ruby 2.2.* (install via ruby-build)
- Node.js 4.* (install via nvm)
- Git 2.* (install via Homebrew)
- SQLite 3.* (install via Homebrew)
- PostgreSQL 9.* (install via Homebrew)

## Applications

- [Atom][atom] or [vim][vim] for editing code
- [Terminal][terminal] or [iTerm][iterm] for command shell

<!-- references -->

[rbenv]:http://rbenv.org/
[ruby-build]:https://github.com/sstephenson/ruby-build
[nvm]:https://github.com/creationix/nvm
[npm]:https://www.npmjs.com/
[atom]:https://atom.io/
[vim]:http://www.vim.org/
[terminal]:https://en.wikipedia.org/wiki/Terminal_(OS_X)
[iterm]:https://www.iterm2.com/
[docker-toolbox]:https://www.docker.com/docker-toolbox
