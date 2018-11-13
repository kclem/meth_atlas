# Methylation Atlas Deconvolution

This is a standalone program for deconvolution of array methylome.
It uses an input **reference atlas** file to deconvolve a given **sample**, or multiple samples.
Outputs a csv file, and plots a stacked bars figure.

### atlas
A reference atlas file. 
- csv file
- Contains a header (columns names).
- The first column must be Illumina IDs.

The reference atlas used on the paper is supplied in this repository - *reference_atlas.csv*.

### samples
A file containing one or more samples, with similar requirements as the atlas file (csv, header, index column).


### Usage

```
usage: deconvolve.py [-h] [--atlas_path ATLAS_PATH] [--slim] [--plot]
                     [--out_dir OUT_DIR]
                     samples_path

positional arguments:
  samples_path          Path to samples csv file. It must have a header line.
                        The first column must be Illumina IDs (e.g cg00000029)

optional arguments:
  -h, --help            show this help message and exit
  --atlas_path ATLAS_PATH, -a ATLAS_PATH
                        Path to Atlas csv file. The first column must be
                        Illumina IDs (e.g cg00000029)
  --slim                Write the results table *without indexes and header
                        line*
  --plot                Plot stacked bars of the results
  --out_dir OUT_DIR, -o OUT_DIR
                        Output directory
```

### Example
```
deconvolve.py -a reference_atlas.csv sample.csv --plot
```
will deconvolve all samples given as columns in *sample.csv*, dump the resulting coefficients to a csv file named *sample_deconv_output.csv*, plot them, and dump the figure to *sample_deconv_plot.png*.
