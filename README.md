# mfdrouting - Multiple Flow Direction (MFD) flow routing

This Python 3 module implements the Multiple Flow Direction (MFD) flow routing
as proposed by [Freeman (1991)][id1]. As suggested by Freeman the free
parameter p, the exponent that scales the fractions of flows, is tuned to the
divergent flows of cones with p = 1.1, but can optionally be specified. It is
written in C and based on the code by [Pelletier (2008)][id2].

## Install

	git clone https://github.com/UP-RS-ESP/mfdrouting.git
	cd mfdrouting
	sudo python3 setup.py install

## Usage

    import numpy as np
    import mfdrouting
    help(mfdrouting)

will show:

    SCA(z, cellwidth, exponent = 1.1)
    Returns the specific catchment area of the topography (DEM) in z.

    Parameters
    ----------
    z : array_like
        A 2-D array containing the elevations of the topography (DEM).
    cellwidth : float
        The cell width of the grid in meters.
    exponent : float, optional
        The exponent determining the flow divergence in relation to the slope.
        See http://dx.doi.org/10.1016/0098-3004(91)90048-i.

    Returns
    -------
    a : ndarray
        The specific catchment area matrix on the same grid as z (DEM).

## Bugs

In case you receive a segmentation fault it is likely that the cause is a stack overflow.
Please try running your Python scripts in a shell with an unlimited stack size. On Linux
run

    $ ulimit -s unlimited

in your shell of choice.

[id1]: http://dx.doi.org/10.1016/0098-3004(91)90048-i "Calculating catchment area with divergent flow based on a regular grid. T. Graham Freeman, Computers & Geosciences (1991)."

[id2]: http://dx.doi.org/10.1594/IEDA/100145 "MFDrouting, version 0.1. J. D. Pelletier (2008)."
