# FPGA-Based Real-Time Pulse Simulator for Nuclear Instrumentation

This repository contains the LaTeX source for an academic paper describing the development and implementation of a real-time FPGA-based pulse simulator for calorimeter readout electronics.

## About the Paper

The paper presents a configurable hardware pulse simulator that generates synthetic detector signals at 40 MHz, replicating the behavior of particle detector readout chains. The simulator enables validation of signal processing techniques without requiring access to physical experimental facilities.

### Architecture

The simulator is composed of three main processing stages:

1. **Random Number Generation (RNG)** — Generates statistically independent sequences for event decision-making and energy sampling. Compares multiple algorithms (LFSR, Mersenne Twister, xorshift) in terms of hardware resource usage and statistical quality.

2. **Collision Energy Assignment** — Determines event occurrence based on configurable detector cell occupancy and assigns energy values from a configurable spectrum via inverse CDF lookup tables (128–4096 entries).

3. **Digital Shaper** — Convolves input impulses with the detector's characteristic response using IIR filters (CSP + PSC CR-4RC configuration) to produce realistic pulse waveforms, including pile-up effects and baseline variations.

### Key Features

- Real-time 40 MHz operation
- Runtime-configurable parameters: occupancy, offset, and energy spectrum
- Fixed-point arithmetic and parallel IIR filter implementation
- Generic design applicable to nuclear instrumentation and calorimetry

## Authors

- Fábio C. Luna — Federal University of Juiz de Fora
- Thiago C. A. Paschoalin — CEFET-MG
- Tiago M. Quirino — Rio de Janeiro State University
- Luciano M. de Andrade Filho — Federal University of Juiz de Fora

## Repository Structure

```
simulator_paper/
├── main.tex          # Main paper source (IEEE Transactions format)
└── references.bib    # Bibliography
```

## Compiling

The paper uses the `IEEEtran` document class. To compile:

```bash
pdflatex main.tex
bibtex main
pdflatex main.tex
pdflatex main.tex
```

Or using `latexmk`:

```bash
latexmk -pdf main.tex
```
