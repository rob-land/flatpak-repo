# rob-land Flatpak repo

The shared, GPG-signed Flatpak repository for rob-land's mobile Linux
apps, published to <https://rob-land.github.io/flatpak-repo/> for
x86_64 and aarch64.

```sh
flatpak remote-add --user rob-land \
  https://rob-land.github.io/flatpak-repo/rob-land.flatpakrepo
flatpak install --user rob-land land.rob.vitals   # or any other app
```

## How it works

Each app repo ([vitals], [banter], [clicker], [homie], [coffer],
[jamjar], [keepsake], [patch], [roster], [shoebox], [stacks]) builds
natively for both arches in its own GitHub Actions workflow and
uploads the per-arch OSTree repo tars (plus direct-install `.flatpak`
bundles) to its rolling `continuous` release.

The [aggregate workflow](.github/workflows/aggregate.yml) here runs
hourly (and on manual dispatch): it downloads those release tars
anonymously — so the app repos hold no secrets at all — merges every
ref into one OSTree repo, signs commits and summary with the repo GPG
key, and deploys the result to GitHub Pages. Deploys are skipped when
no app ref moved since the live site.

[vitals]: https://github.com/rob-land/vitals
[banter]: https://github.com/rob-land/banter
[clicker]: https://github.com/rob-land/clicker
[homie]: https://github.com/rob-land/homie
[coffer]: https://github.com/rob-land/coffer
[jamjar]: https://github.com/rob-land/jamjar
[keepsake]: https://github.com/rob-land/keepsake
[patch]: https://github.com/rob-land/patch
[roster]: https://github.com/rob-land/roster
[shoebox]: https://github.com/rob-land/shoebox
[stacks]: https://github.com/rob-land/stacks
