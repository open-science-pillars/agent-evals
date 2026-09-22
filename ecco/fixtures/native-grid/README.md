# native-grid fixture

`ecco_05deg_stub.nc` is a SYNTHETIC stand-in for a granule of the ECCO
0.5 degree interpolated temperature and salinity product
(`ECCO_L4_TEMP_SALINITY_05DEG_MONTHLY_V4R4`): `THETA` and `SALT` on
`time/Z/latitude/longitude`, no face fluxes, no `hFac` geometry, no
snapshots.

Which case exposes it, and what a passing answer to that case looks
like, are in the case file and stay there. This directory sits in the
workspace a trial reads, so a sentence here saying what the right
answer is would be the answer, handed over beside the fixture the case
has to expose. The same goes for the file's own `summary` attribute,
which records that it is synthetic and names no case.

Every value is an analytic function of the coordinates. Nothing in the
file is observational data or ECCO output, and the global attributes
(`title`, `synthetic`, `summary`, `imitates_collection`,
`imitates_doi`) say so. It must never be used for science.

Rebuild or verify it with the generator beside it:

    uv run ecco/fixtures/native-grid/make_ecco_05deg_stub.py            # write
    uv run ecco/fixtures/native-grid/make_ecco_05deg_stub.py --check    # byte compare

The build is deterministic (NetCDF3 classic, no timestamps, no random
numbers), so `--check` compares a fresh build byte for byte against the
committed file.
