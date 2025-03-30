# Openmod 2025 Benders

This repository contains code and notebooks used for the tutorial on Benders decomposition during the Openmod 2025
workshop.

The [Calliope](https://calliope.readthedocs.io/en/stable/) example model (`national_scale`) as well as the code
interacting with the model are based on a development version of Calliope, available before the release of `v0.7.0`,
using the [GitHub repository](https://github.com/calliope-project/calliope) at the state of comit
`c2a7563953c6c415e54d02ba8aeae0db4be67079`.

Running this locally can be achieved, e.g., using `uv`:

```bash
uv init
uv add "calliope @ git+https://github.com/calliope-project/calliope@c2a7563953c6c415e54d02ba8aeae0db4be67079
```

> [!IMPORTANT]
> Also refer to the [openmod forum thread](https://forum.openmod.org/t/on-the-application-of-benders-decomposition-to-energy-system-models/5099)
> related to this tutorial.

## Notebooks

The notebooks showcase a basic implementation:

1. `openmod_2025_benders_basic.ipynb`: Basic implementation of Benders decomposition
2. `openmod_2025_benders_lshaped.ipynb`: Basic implementation of an L-shaped approach using three different "weather" weeks

These notebooks are available on Google Colab and can be run without any installation, just click on the links below:

1. [Basic](https://colab.research.google.com/drive/1tALKLf5hpd40m17n3QMjbsJYcWwYbg0f?usp=sharing)
2. [L-shaped](https://colab.research.google.com/drive/1UlG9i919DbV1BhyETsFPWMQdO3MM5yub?usp=sharing)

## License

Make sure to check the [license of Calliope](https://github.com/calliope-project/calliope/blob/main/LICENSE), especially
regarding the example model that is derived from it.

Otherwise, refer to the [LICENSE](LICENSE) file in this repository.
