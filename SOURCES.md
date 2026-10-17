# Design and implementation sources

Verified references used for the implementation (reviewed 17 October 2026):

- GitHub — Managing your profile README: https://docs.github.com/en/account-and-profile/how-tos/profile-customization/managing-your-profile-readme
  - Confirms profile repository must be public, exactly match the username, and contain a non-empty root `README.md`.
- GitHub — Quickstart for writing and formatting on GitHub: https://docs.github.com/en/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/quickstart-for-writing-on-github
  - Documents `<picture>` with `prefers-color-scheme` for separate light/dark images.
- Platane/snk README: https://github.com/Platane/snk
  - Documents `Platane/snk@v3`, SVG output paths, light/dark palettes, and its contribution-graph animation approach.
- crazy-max/ghaction-github-pages README: https://github.com/crazy-max/ghaction-github-pages
  - Documents `target_branch`, `build_dir`, and `GITHUB_TOKEN` usage. The workflow uses `@v5` per its current README/release listing.
- GitHub — `GITHUB_TOKEN`: https://docs.github.com/en/actions/concepts/security/github_token
  - Explains the automatically generated, repository-scoped token.
- GitHub — Use `GITHUB_TOKEN` to authenticate: https://docs.github.com/en/actions/tutorials/authenticate-with-github_token
  - Recommends restricting workflow permissions to the minimum needed.

## Design decisions (opinion, not platform guarantees)

- Neon terminal palette: near-black `#090B14`, panel `#111525`, violet `#B9A5FF`, cyan `#78E8F2`, mint `#B8F7D4`.
- Keep stats cards, view counters, typing services, Spotify cards, and long badge rows out of the default README. Each extra hosted widget adds a dependency, another request, and another way for the profile to break or become visually noisy.
- SVG files are in the repo for the main header and terminal panel, reducing reliance on third-party image APIs. GitHub still serves repository images through its own rendering/image infrastructure.
- The snake animation is optional and hidden until its Action run succeeds. It uses one third-party Action in CI, and its generated output is stored in the profile repository's `output` branch.

## Verify before publishing

Project repository URLs and social URLs are based on previous conversation details and have not been confirmed against the live profile. Click-test and edit them before committing. The username `akash-aanand` is a best-known value from earlier repo URLs, not independently authenticated profile ownership.
