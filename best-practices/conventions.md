# Conventions to Follow When Writing Code

## File structure

Some apps are server-only (e.g., an API), other apps are client-only (e.g., a single-page app), and other apps may be [universal][universal-javascript] (e.g., API + user interface).

With that in mind, file structure may vary a bit from project to project. Here is what someone can expect (for the most part):


    .github
      CONTRIBUTING.md   # how to edit / contribute to the codebase
      PULL_REQUEST_TEMPLATE.md    # how to format pull request changes proposed
    src
      client/             # (for client and universal apps) code that only runs client-side
      common/             # (for universal apps) code that may run client- or server-side
      config/             # configuration files or code
      data/                 # database migrations and configuration
      dist/               # (for client and universal apps) in .gitignore, for bundled assets
      public/             # (for server and universal apps) publicly-accessible static assets
      server/             # (for server and universal apps) code that only runs server-side
    LICENSE             # license text (e.g., "ISC" for open-source or "UNLICENSED" for proprietary)
    README.md           # purpose, orientation, installation, getting started



<!-- references -->

[universal-javascript]:https://medium.com/@ghengeveld/isomorphism-vs-universal-javascript-4b47fb481beb
