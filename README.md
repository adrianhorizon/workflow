<div align="center">
  <a href="https://github.com/adrianhorizon/workflows">
    <img src="https://avatars.githubusercontent.com/u/10576007?v=4" alt="Logo" width="100" height="100">
  </a>

  <h3 align="center">Adrian Workflows Configuration</h3>
</div>

## Getting Started

1. Create your Feature Branch (`git checkout -b feature/[TICKET-ID]`)
2. Commit your Changes (`git commit -m '[TICKET-ID]'`)
3. Push to the Branch (`git push origin feature/[TICKET-ID]`)
4. Open a Pull Request

<p align="right">(<a href="#top">back to top</a>)</p>


<!-- CONTACT -->
## Contact

* Adrian - [@adrianhorizon](https://github.com/adrianhorizon)

__Project Link:__ [https://github.com/adrianhorizon/workflows](https://github.com/adrianhorizon/workflows)

<p align="right">(<a href="#top">back to top</a>)</p>


### example

```yaml
name: Release

on:
  workflow_dispatch:
  push:
    branches: [develop]

jobs:
  release:
    uses: adrianhorizon/workflows/.github/workflows/release.yml@main
    secrets:
      github-token: ${{ secrets.GITHUB_TOKEN }}

  lint:
    needs: release
    uses: adrianhorizon/workflows/.github/workflows/lint.yml@main

  test:
    needs: lint
    uses: adrianhorizon/workflows/.github/workflows/test.yml@main

  sonar-cloud:
    needs: test
    uses: adrianhorizon/workflows/.github/workflows/build-security.yml@main
    secrets:
      github-token: ${{ secrets.GITHUB_TOKEN }}
      sonar: ${{ secrets.SONAR_TOKEN }}
```
