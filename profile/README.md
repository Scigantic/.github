# Scigantic

Scigantic builds a platform for working with public scientific data: a searchable catalog of thousands of archives, notebooks that mount them directly with no download step, an in-notebook AI assistant with schema-aware context, and fine-tuning pipelines for biological sequence models. [scigantic.com](https://scigantic.com)

The packages in this org are the query layer underneath that platform, released standalone. Each one is a permissively licensed Python client for a specific public archive or file format, self-contained and usable with no dependency on the rest of Scigantic. Together they're a library of libraries: point-lookups, search, and streaming access over public scientific data, without mirroring a database yourself or downloading more than you need. Using one on its own is a preview of the access layer that Scigantic's contextualized archives and fine-tuning infrastructure are built on top of.

## Structural biology & cryo-EM

| Package | What it does |
|---|---|
| [scigantic-empiar](https://github.com/Scigantic/scigantic-empiar) | Stream any of ~3,000 EMPIAR cryo-EM datasets (8.9 PiB) over parallel HTTP range reads, nothing downloaded |
| [scigantic-emdb](https://github.com/Scigantic/scigantic-emdb) | Search all 60,895 EMDB structures by protein, organism, resolution, molecular weight, or PDB cross-reference |
| [scigantic-wwpdb](https://github.com/Scigantic/scigantic-wwpdb) | Fetch any of ~45,000 wwPDB Chemical Component Dictionary ligands and monomers by id, no download |
| [scigantic-cryoet](https://github.com/Scigantic/scigantic-cryoet) | Search ~370 CZ CryoET Data Portal tomography datasets by organism, sample type, disease, or annotation coverage |

## Chemistry & bioactivity

| Package | What it does |
|---|---|
| [scigantic-chembl](https://github.com/Scigantic/scigantic-chembl) | Query ChEMBL directly from a public S3 mirror with DuckDB, no local database |
| [scigantic-bindingdb](https://github.com/Scigantic/scigantic-bindingdb) | Query BindingDB the same way, including a live cross-reference bridge into ChEMBL |
| [scigantic-pubchem](https://github.com/Scigantic/scigantic-pubchem) | Live PubChem client with throttle-aware retry, BioAssay/gene/protein/Tox21 coverage, and caching PubChemPy doesn't have |
| [scigantic-comptox](https://github.com/Scigantic/scigantic-comptox) | Query EPA's ToxCast bioactivity data from a public S3 mirror, plus live Chemical/Hazard/Exposure lookups over EPA's own CCTE API |

## File formats & agent tooling

| Package | What it does |
|---|---|
| [scigantic-headers](https://github.com/Scigantic/scigantic-headers) | Decode scientific file headers (cryo-EM, imaging, flow cytometry, mass spec, sequencing, structural biology) into typed fields. Zero dependencies. |
| [scigantic-mcp](https://github.com/Scigantic/scigantic-mcp) | MCP server for the Scigantic archive catalog: search thousands of datasets and get LLM-ready schema cards without downloading anything |

```
pip install scigantic-empiar scigantic-emdb scigantic-wwpdb scigantic-cryoet \
            scigantic-chembl scigantic-bindingdb scigantic-pubchem scigantic-comptox \
            scigantic-headers scigantic-mcp
```

Every package here is MIT or MIT-0 licensed, with its own README, tests, and CI. Issues and PRs welcome.
