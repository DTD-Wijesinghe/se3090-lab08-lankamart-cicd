# SE3090 Lab 08 Implementation

Student: Wijesinghe.D.T.D.
IT number: IT24100858
Repository: https://github.com/DTD-Wijesinghe/se3090-lab08-lankamart-cicd

## CI workflow

`.github/workflows/ci.yml` runs on pushes to `main`, `feature/**`, `chore/**`, and `fix/**`, and on pull requests targeting `main`. It checks out the repository, installs .NET 8, restores the solution, builds in Release mode, and runs `LankaMart.ServiceTests`.

The delivery work is maintained on the `chore/add-ci` branch so it can be reviewed and merged into `main` through the GitHub pull-request workflow required by Lab 08.

The workflow uses `permissions: contents: read` and does not require database credentials, connection strings, JWT keys, or other secrets. The service tests use fakes and therefore run without PostgreSQL or a web server.

## Code quality and security review

The project keeps configuration secrets outside committed JSON files, validates JWT issuer, audience, lifetime, signing key, and algorithm, hashes refresh tokens before persistence, uses strict equality for security comparisons, and enforces object-level order ownership. The CI workflow verifies that the solution builds and that the service/security tests pass on every change.

The review also confirms that the development-only JWT marker is refused outside Development, production sensitive-data logging is not enabled, and `.gitignore` excludes local environment files, production settings, and build output.

## Original requirement sheet

`docs/SE3090_Lab08_Requirements_Original.pdf` is an unchanged copy of the supplied requirement PDF. Its SHA-256 is `E83AE2797DA0DC80EE9CE2131CF3A1B89589930CFF0F7F432BFDC590C03C6173`.
