# Conventions to Follow When Writing Code

## File structure

Some apps are server-only (e.g., an API), other apps are client-only (e.g., a single-page app), and other apps may be [universal][universal-javascript] (e.g., API + user interface).

With that in mind, file structure may vary a bit from project to project. Here is what someone can expect, and this may be semi-enforced via the use of a project generator tool (e.g., [Yeoman][yeoman]).


    README.md           # purpose, orientation, installation, getting started
    CONTRIBUTING.md     # how to edit / contribute to the codebase
    LICENSE             # license text (e.g., "ISC" for open-source or "UNLICENSED" for proprietary)
    circle.yml          # integration with Circle CI to run automated tests
    client/             # (for client and universal apps) code that only runs client-side
    common/             # (for universal apps) code that may run client- or server-side
    config/             # configuration files or code
    dist/               # (for client and universal apps) in .gitignore, for bundled assets
    public/             # (for server and universal apps) publicly-accessible static assets
    scripts/            # scripts for automation and other common tasks
    server/             # (for server and universal apps) code that only runs server-side



<!-- references -->

[universal-javascript]:https://medium.com/@ghengeveld/isomorphism-vs-universal-javascript-4b47fb481beb
[yeoman]:http://yeoman.io/
