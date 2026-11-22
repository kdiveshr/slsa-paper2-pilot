# slsa-paper2-pilot

Study repo for Paper 2 (IEEE IT Professional): does SLSA provenance verification actually protect you? It mints real provenance for Paper 1's Maven JARs in GitHub Actions, then tests the verifier against tampering, honest rebuilds, and a compromised builder.

## What's in here

- `pilot.yml` — the 3-project pilot (22 November 2026): provenance minting, the legacy generator spot-check, and the first detection matrix (25 of 25 as expected). This is where we found Maven 3.10.1 makes unfixed builds byte-identical by default, so the full run pins Maven 3.9.9.
- `full-run.yml` — the full run (22 November 2026): 25 projects, 199 verification cases. Tampering caught 73 of 73; honest rebuilds mistaken for tampering 22 of 25; after the Paper 1 fix, 0 of 24; builder compromise passed 25 of 25.
- `slsa-retry-scheduledashboard.yml` — the single-job retry that recovered the one cell lost to a Maven Central rate limit.
- `slsa-rebuild-petclinic-paper1.yml` — the rebuild that settled the petclinic digest question: checkout depth, not the JDK.

## Ground rules

All tampering is self-inflicted on our own copies — a marker file added to one JAR in the `compromise` variant. No real secrets, no upstream repos touched, no third-party repos touched.

Provenance is minted by this repo's workflows, not inside each project's fork, so the attestation's source URI names this repo. The digest binding the study tests is unaffected; the paper says so plainly.

## Results

The numbers and the manuscript live with the paper, not here — this repo holds the workflows only. Headline: the verifier catches every tamper it can see, mistakes most honest rebuilds for tampering, and is blind to builder compromise. The Paper 1 fix removes the false positives entirely.
