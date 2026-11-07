# goldbox

This branch is upstream SDL 3.4.8 at `d9d5536704d585616d4db3c8ba3c4ff6fc2757e1`, plus this directory and `.github/workflows/goldbox.yml`. Upstream's own
CI workflows are removed here, so that pushing this branch runs only goldbox.yml.

Pushing the tag `goldbox` builds the pins in `toolchain` with `sdl3-setup.sh` and publishes them as the release
`goldbox`: one archive per platform and a `SHA256SUMS`. Deleting the tag deletes the release. The Gold Box
reconstructions (talonius/bc-pool-of-radiance and others) download their toolchain from that release instead of
building it in every CI run.

`sdl3-setup.sh` and `toolchain-release.sh` are copies of Pool of Radiance's `scripts/` files of the same names; change
them there and copy them here. To build another version: change `toolchain` (and the recipe, if the way it is built
changed), commit, and move the tag:

    git tag -f goldbox && git push -f origin goldbox
