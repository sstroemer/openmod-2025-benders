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

## Literature

While there are many resources available on Benders decomposition, I can "recommend" the following starting points:

1. **A general review:** Rahmaniani, R., Crainic, T. G., Gendreau, M., & Rei, W. (2017). The Benders decomposition algorithm: A literature review. _European Journal of Operational Research, 259(3), 801-817._ [\[doi: 10.1016/j.ejor.2016.12.005\]](https://doi.org/10.1016/j.ejor.2016.12.005)
2. **An important read on the application of interior-point methods:** Gondzio, J. (2025). Interior Point Methods in the Year 2025. _EURO Journal on Computational Optimization, 13, 100105._ [\[doi: 10.1016/j.ejco.2025.100105\]](https://doi.org/10.1016/j.ejco.2025.100105) (cf. [\[doi: 10.1016/j.ejor.2011.09.017\]](https://doi.org/10.1016/j.ejor.2011.09.017))
3. **A recent, comprehensive energy system application:** Göke, L., Schmidt, F., & Kendziorski, M. (2024). Stabilized Benders decomposition for energy planning under climate uncertainty. _European Journal of Operational Research, 316(1), 183-199._ [\[doi: 10.1016/j.ejor.2024.01.016\]](https://doi.org/10.1016/j.ejor.2024.01.016)

## Using `Gurobi`

Note that the notebooks hosted on colab make use of `GLPK` (since the `pyomo.kernel` backend used by `Calliope` does -
at the time of doing this - does not allow interfacing with `HiGHS`) for simplex-based solves, as well as `Ipopt` for
an interior-point method used in the main/first-stage model (since `pyomo` does not easily allow extracting `ipm`
solutions from `GLPK`). This considerably slows down the solving process.

If you have access to a `Gurobi` license, you can make use of it - as is done and shown in the "local" notebooks
included in this repository.

> [!IMPORTANT]
> Note that `opt_m.options["Method"] = 2` forces `Gurobi` to use the barrier method, while
> `opt_m.options["Crossover"] = 0` disables crossover.

The use of a non-simplex method for the first-stage model is an easy first step towards reducing oscillations (refer to
the literature section).

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
