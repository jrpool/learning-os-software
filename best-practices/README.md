# Best Practices

Discipline in following best practices is the key to effective collaboration and ease of long-term maintenance.

At Learners Guild, we adhere to the following practices.

## Security

##### All communication over encrypted channel

APIs should expose endpoints only over HTTPS. This should be true for standard request-response APIs (RESTful and otherwise) as well as any "push" APIs (via something like Web Sockets).

Client applications should always communicate with internal APIs over HTTPS.

## Documentation

##### Every repository has a README

Every organization repository has a README.md file in the root directory that explains the intent for that piece of software.

At minimum, this document covers or links to:

- Purpose
- Example use case
- Installation and getting started
- How to contribute
- Where to go for help

In addition, any code we write should make a best attempt at following a standard set of [conventions](conventions.md) for things like file structure and file naming. Furthermore, if a service is being started from scratch, it should use one of our predefined project templates or generators.

##### Code is self-documenting

Inline documentation and comments are reserved for rare occasions of exceptionally complicated code. Code is written in such a way as to reflect its intent and usage clearly (using proper variable and function names, for example).

The urge to write an explanatory comment is usually a sign that the code should be refactored for clarity.

## Testing

##### Deployment fails unless all tests pass

No service should be deployable unless the testing suite succeeds. This is a hard requirement that helps prevent reckless deploys and obsolete tests.

##### Source code has at least 90% test coverage

Coverage is not a perfect measurement of a solid testing suite, but as a single metric it offers a decent enough proxy.

Good developers will write more robust tests for the most critical components of their code, and lighter tests for the auxiliary pieces.

##### Unit tests are fast, and run automatically

A good unit testing suite should run in < 5 seconds and should _never_ depend on external libraries or services.

All projects should integrate with [Codeship][codeship] to run tests in the cloud.

##### Integration tests exist for common use cases

Every service has a purpose and primary use case(s); integration tests explicitly exercise and demonstrate that purpose. Every service should include at least two integration tests: a "happy path" and "sad path".

## Code Style

##### Code is linted

For JavaScript, we use [XO][xo].

## Version Control

##### Commit messages are well written and easy to read

Commit messages should tersely and accurately explain _why_ the change was made.

Read Chris Beams' [article on good commit messages][good-commit-messages] for more explanation.

##### New code is added via pull requests after review

We follow the [GitHub Flow][gh-flow] for our development cycles:

- All new features and patches are created on a branch
- Merging happens via a pull request
- Branches are not merged until at least one other person has ok'd the pull request

##### Semantic versioning is followed as best as possible

Especially in the context of a [service-oriented architecture][soa], a good versioning strategy is essential to keep dependencies clear and allow simultaneous development.

We follow [Semantic Versioning][semver] as much as possible, the minimum being:

- A major version change for incompatible API changes
- A minor version change for new backwards-compatible functionality

Git tags are added for all major changes and significant minor changes.

## Dependency Management

##### Lock dependency versions

Every dependency (for development, test, and production environments) is explicitly declared along with the required version.

When there are external dependencies that cannot be explicitly declared in a dependency-management file (a `Gemfile` or `package.json`, for Ruby or Node.js projects), they should be made explicit in the README. For example, if the code requires a database connection, written instructions (and scripts, ideally) for setting up a database should be included.

##### Latest releases and patches are preferred

Whenever possible and appropriate, fuzzy version check is preferred so that new patches and bugfixes can be allowed without breaking the API.

For example, in a `package.json` requiring the `gitbook-cli` package, use the syntax: `"gitbook-cli": "^1.0.0"` to match _any_ release with a major version number `1` (`1.x.x`). Do not use `"gitbook-cli": "1.0.0"` because this locks in a single major/minor/patch release and will not allow for updates when new patches and minor releases come out.

## File structure

Some apps are server-only (e.g., an API), other apps are client-only (e.g., a single-page app), and other apps may be [universal][universal-javascript] (e.g., API + user interface).

With that in mind, file structure may vary a bit from project to project. Here is what someone can expect (for the most part):

    CONTRIBUTING.md   # how to edit, or otherwise contribute to, the codebase
    LICENSE           # license text (e.g., "ISC" or "MIT" for open-source or "UNLICENSED" for proprietary)
    README.md         # purpose, orientation, installation, getting started
    src
      client/         # (for client and universal apps) code that only runs client-side
      common/         # (for universal apps) code that may run client- or server-side
      config/         # configuration files or code
      data/           # database migrations and configuration
      dist/           # (for client and universal apps) in .gitignore, for bundled assets
      public/         # (for server and universal apps) publicly-accessible static assets
      server/         # (for server and universal apps) code that only runs server-side
        actions/      # core business logic; 1 function exported per module (file)
        graphql/      # GraphQL API definition
          mutations/  # GraphQL mutation fields
          queries/    # GraphQL query fields
          schemas/    # GraphQL custom schemas
        services/     # internal services (interfaces to external services)
        workers/      # background task processors
      test/           # test utilities

<!-- references -->

[universal-javascript]:https://medium.com/@ghengeveld/isomorphism-vs-universal-javascript-4b47fb481beb
[ruby-lint]:https://github.com/YorickPeterse/ruby-lint
[xo]:https://github.com/sindresorhus/xo
[good-commit-messages]:http://chris.beams.io/posts/git-commit/
[gh-ruby-styleguide]:https://github.com/styleguide/ruby
[airbnb-js-styleguide]:https://github.com/airbnb/javascript
[gh-flow]:https://guides.github.com/introduction/flow/
[soa]:../global-requirements/soa.md
[semver]:http://semver.org/
[codeship]:codeship.com
