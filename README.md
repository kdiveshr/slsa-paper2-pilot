# slsa-paper2-pilot

Pilot repo for Paper 2 (IEEE IT Professional): SLSA provenance verification
detection matrix. Test repo only — 2–3 projects, Nov 2026.

- Builds 3 small public Spring Boot (Maven) projects from Paper 1 at their
  pinned commits (plus Paper 1 fix commits), mints SLSA provenance with
  GitHub Artifact Attestations (`actions/attest-build-provenance@v2`), and
  uploads the JARs so `slsa-verifier` / `gh attestation verify` can be run
  locally against them.
- One legacy spot-check job uses the frozen `slsa-github-generator`
  generic workflow @v2.1.0 (unmaintained since Aug 2026).
- All tamper is self-inflicted on own copies (a marker file added to one
  JAR in the `compromise` variant). No real secrets, no upstream repos
  touched, no third-party repos touched.

Trigger: Actions tab → `slsa-pilot` workflow → Run workflow.
