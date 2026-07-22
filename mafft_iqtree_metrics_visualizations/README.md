# MAFFT + IQ-TREE: metrics and visualizations

This curated local copy contains only aggregate/status files and visualization
artifacts from the completed server mode. It intentionally excludes source and
filtered TSV data, FASTA alignments, tree inference working files, supported-
subset memberships, raw per-sequence motif records, and mutation tables.

## What completed

The legacy runner completed all 12 commands for `MAFFT + IQ-TREE` with exit
code 0 in 1806.658 seconds (30 minutes 6.7 seconds). The immutable input hash
recorded by the server is
`5705ffd2929434ffced8fba6c1640385b9597e0cca3ec1879fcf87f6f6bed9f1`, and
the source revision is `6783067e3d2f1ea5b0f1c9393371f59769e0fe67`.

The run began with 6196 rows. The legacy filter removed 412 duplicate rows and
65 additional rows by its length/reference rule, leaving 5719. It built 380
V/J groups, selected 266 groups containing 5517 sequences, produced 266 MAFFT
alignments, 266 IQ-TREE trees, and 266 HTML visualizations. IQ-TREE commands
used `GTR+F+I+G4`, 1000 UFBoot replicates, and 1000 SH-aLRT replicates.

The supported-subset stage exported 1238 nested subset FASTAs with 5282 total
memberships. These membership files are not retained in this curated copy.
The motif scanner reported 133633 hotspot and 267312 coldspot occurrences over
5517 records; these are motif occurrences/opportunities, not measured SHM
events relative to germline.

## Important scientific limitations

`mutation_stats.tsv` is retained only as historical output. Its 68445 rows
(46202 nonsynonymous and 22243 synonymous) must not be treated as a validated
production estimate: nested subsets can repeat observations, raw IgBLAST
output was not retained, and the historical dN/dS denominator used only codons
where a mutation was already observed. The dN/dS column is therefore a biased
proxy and is not suitable for biological or corporate decisions.

The legacy `complete=true` status means that commands returned successfully. It
does not prove full input preservation, independent recomputation of outputs,
approved input/reference provenance, a locked environment, or corporate
release eligibility. In particular, removing 412 duplicate rows conflicts with
the new no-silent-loss production contract.

The retained PNG renders correctly at 3900 x 900, but its labels such as
"pedigree complexity" and "difference of descendants from an ancestor" are not
scientifically justified by these unrooted trees. They describe a deterministic
display orientation, not an established ancestor/descendant direction. The new
pipeline labels these quantities as unrooted supported subsets and does not
claim lineage direction without an approved germline/outgroup rooting method.

At the 2026-07-22 10:59 UTC audit snapshot, `MAFFT + MrBayes` was still active:
14 GPU groups were explicitly non-converged, zero consensus trees were
accepted, and one of 16 GPU-routed groups was still running. The two MACSE modes
had not started. Those incomplete results were not copied here.

## Files

- `metrics_summary.json`: safe aggregate summary generated during this audit.
- `run_status.json`, `run_manifest.json`, `config.json`: exact server files.
- `mutation_stats.tsv`: exact but scientifically unapproved historical metric.
- `tree_analytics.png`: aggregate 3900 x 900 visualization.
- `trees_visualization/iqtree/`: 266 exact interactive HTML tree views.
- `_evidence/`: orchestration log and server-side integrity manifests.

The HTML tree views contain original tip identifiers because they are part of
the requested visualization. They must remain in controlled storage.
