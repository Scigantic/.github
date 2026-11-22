# Scigantic

Scigantic is a catalog of more than 8,000 public scientific datasets (cryo-EM and protein structure, cancer genomics and imaging, neuroscience, chemistry and drug discovery, earth observation, climate) that open in a hosted Jupyter notebook with the data already mounted, so there is no download step. Search it at [scigantic.com/explore](https://scigantic.com/explore?utm_source=github&utm_medium=org-profile&utm_campaign=org-profile), or from an AI assistant through the public MCP server at `https://api.scigantic.com/mcp`.

The packages in this org are the Python libraries behind that catalog, released on their own. Each one reads a specific public archive or file format: EMPIAR, EMDB, AlphaFold DB, ChEMBL, PubChem, SureChEMBL, the NCI Genomic and Imaging Data Commons, the Brain Image Library and others. They search and stream the data in place, without a mirror of your own and without downloading more than you ask for. All are MIT or MIT-0 licensed and work without a Scigantic account.

```python
import scigantic_nci as nci

clin = nci.gdc.clinical("TCGA-BLCA")           # 412 cases, read from public S3
nci.gdc.mutation_frequency("TCGA-BLCA")        # TP53 0.488, TTN 0.425, KMT2D 0.263, ...
```

Browse the catalog by field: [structural biology](https://scigantic.com/topics/structural-biology?utm_source=github&utm_medium=org-profile&utm_campaign=org-profile), [cryo-EM](https://scigantic.com/topics/cryo-em?utm_source=github&utm_medium=org-profile&utm_campaign=org-profile), [drug discovery](https://scigantic.com/topics/drug-discovery?utm_source=github&utm_medium=org-profile&utm_campaign=org-profile), [genomics](https://scigantic.com/topics/genomics-and-bioinformatics?utm_source=github&utm_medium=org-profile&utm_campaign=org-profile), [neuroscience](https://scigantic.com/topics/neuroscience?utm_source=github&utm_medium=org-profile&utm_campaign=org-profile), [histopathology](https://scigantic.com/topics/histopathology?utm_source=github&utm_medium=org-profile&utm_campaign=org-profile).

## Structural biology & cryo-EM

| Package | What it does |
|---|---|
| [scigantic-empiar](https://github.com/Scigantic/scigantic-empiar) | Stream any of ~3,000 EMPIAR cryo-EM datasets (8.9 PiB) over parallel HTTP range reads, nothing downloaded |
| [scigantic-emdb](https://github.com/Scigantic/scigantic-emdb) | Search all 60,895 EMDB structures by protein, organism, resolution, molecular weight, or PDB cross-reference |
| [scigantic-wwpdb](https://github.com/Scigantic/scigantic-wwpdb) | Fetch any of ~45,000 wwPDB Chemical Component Dictionary ligands and monomers by id, no download |
| [scigantic-cryoet](https://github.com/Scigantic/scigantic-cryoet) | Search ~370 CZ CryoET Data Portal tomography datasets by organism, sample type, disease, or annotation coverage |
| [scigantic-alphafold](https://github.com/Scigantic/scigantic-alphafold) | Fetch an AlphaFold DB v6 predicted structure by UniProt accession with one HTTP range request against EBI's bulk tars (Swiss-Prot plus 46 proteomes). Zero dependencies. |
| [scigantic-msa](https://github.com/Scigantic/scigantic-msa) | Build a protein MSA from the ColabFold MMseqs2 server merged with published open alignments (OpenFold3, LiteFold, OpenProteinSet), or from open data alone, and write the input files for AlphaFold 3, Boltz, Chai-1, ColabFold, OpenFold3 or Protenix. Zero dependencies. |

## Chemistry & bioactivity

| Package | What it does |
|---|---|
| [scigantic-chembl](https://github.com/Scigantic/scigantic-chembl) | Query ChEMBL directly from a public S3 mirror with DuckDB, no local database |
| [scigantic-bindingdb](https://github.com/Scigantic/scigantic-bindingdb) | Query BindingDB the same way, including a live cross-reference bridge into ChEMBL |
| [scigantic-pubchem](https://github.com/Scigantic/scigantic-pubchem) | Live PubChem client with throttle-aware retry, BioAssay/gene/protein/Tox21 coverage, and caching PubChemPy doesn't have |
| [scigantic-comptox](https://github.com/Scigantic/scigantic-comptox) | Query EPA's ToxCast bioactivity data from a public S3 mirror, plus live Chemical/Hazard/Exposure lookups over EPA's own CCTE API |
| [scigantic-deeppk](https://github.com/Scigantic/scigantic-deeppk) | Client for Deep-PK's small-molecule ADMET/toxicity prediction API, plus a mirrored CYP450 inhibitor/substrate reference dataset |
| [scigantic-surechembl](https://github.com/Scigantic/scigantic-surechembl) | SureChEMBL patent chemistry: 31M compounds and 45M patents by id, name, SMILES, InChIKey or structure search, the patents for any ChEMBL or PubChem compound, full patent text, EBI's bulk parquet read in place with DuckDB, and joins into scigantic-chembl and scigantic-bindingdb |

## Microscopy & neuroscience

| Package | What it does |
|---|---|
| [scigantic-bil](https://github.com/Scigantic/scigantic-bil) | Search all 14,000+ Brain Image Library datasets (6 PB of BICCN brain microscopy) and read light-sheet, fMOST and STPT volumes over HTTP: one slice, one thumbnail, or an OME-Zarr level, nothing downloaded |
| [scigantic-facebase](https://github.com/Scigantic/scigantic-facebase) | Search FaceBase's ~1,070 open craniofacial datasets and read zipped micro-CT scans slice by slice over HTTP, with the dataset citation FaceBase asks for. Open-access data only, nothing mirrored |

## Cancer genomics & imaging

| Package | What it does |
|---|---|
| [scigantic-nci](https://github.com/Scigantic/scigantic-nci) | NCI Genomic Data Commons as per-project clinical, expression, mutation, copy-number, miRNA, RPPA and methylation tables, and the Imaging Data Commons as per-collection series indexes with a sample DICOM series per modality, read from public S3 with no credentials |

## Comparative genomics

| Package | What it does |
|---|---|
| [scigantic-ucsc](https://github.com/Scigantic/scigantic-ucsc) | Conservation scores (phyloP, phastCons), nine-species hg38 multiz alignment slices, TOGA gene-loss annotations and assembly lists from UCSC's public S3 bucket, read by byte range with no download |

## Public health

| Package | What it does |
|---|---|
| [scigantic-who](https://github.com/Scigantic/scigantic-who) | Query every WHO Global Health Observatory indicator from a public parquet mirror with DuckDB, with WHO's dimension codes decoded |

## File formats & agent tooling

| Package | What it does |
|---|---|
| [scigantic-headers](https://github.com/Scigantic/scigantic-headers) | Decode scientific file headers (cryo-EM, imaging, flow cytometry, mass spec, sequencing, structural biology) into typed fields. Zero dependencies. |
| [scigantic-mcp](https://github.com/Scigantic/scigantic-mcp) | MCP server for the Scigantic archive catalog: search thousands of datasets and get LLM-ready schema cards without downloading anything |
| [scigantic](https://github.com/Scigantic/scigantic) | Command line and Python launcher: give it a Hugging Face dataset or a Scigantic archive id and it opens the dataset in a hosted notebook, or lists and streams the files locally over `hf://` |
| [scigantic-cards](https://github.com/Scigantic/scigantic-cards) | A JSON format for describing a dataset to an LLM agent, a linter for it, and `init` to draft a card from a folder or bucket (file counts, sizes, CSV columns, decoded file headers). `verify` runs the card's snippets to check they work. JSON Schema included. Zero dependencies. |

```
pip install scigantic-empiar scigantic-emdb scigantic-wwpdb scigantic-cryoet \
            scigantic-chembl scigantic-bindingdb scigantic-pubchem scigantic-comptox \
            scigantic-deeppk scigantic-surechembl scigantic-bil scigantic-facebase scigantic-nci \
            scigantic-ucsc scigantic-msa scigantic-alphafold scigantic-who scigantic-headers \
            scigantic-mcp scigantic-cards scigantic
```

Each package has its own README, tests and CI. Issues and PRs are welcome.
