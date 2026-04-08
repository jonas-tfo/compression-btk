# seqshrink - lossless compression for biological sequences

Compression of FASTA-formatted biological sequence data using alphabet specific bit packing.

## Compression modes

| Mode    | Alphabet                | Bits/symbol |
|---------|-------------------------|-------------|
| `dna2`  | A, C, G, T              | 2           |
| `dna3`  | A, C, G, T, N, Gap      | 3           |
| `rna2`  | A, C, G, U              | 2           |
| `rna3`  | A, C, G, U, N, Gap      | 3           |
| `prot5` | 20 amino acids, X, Stop | 5           |

Sequence IDs are stored separately and compressed. The output format uses a custom binary container.

## Usage

```sh
# Compress
compression-btk compress -i input.fasta -o output.blok -m dna2

# Decompress
compression-btk decompress -i output.blok -o recovered.fasta
```

## Example:

Using the `dna3` mode on the genome assembly Avulg\_BH\_1.0 of Armadillidium vulgare (common pillbug):

| File | Size |
|------|------|
| Original `.fna` | 1.94 GB |
| Compressed `.blok` | 736 MB |
| **Reduction** | **~63%** (2.7× smaller) |
