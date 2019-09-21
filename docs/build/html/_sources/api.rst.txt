API
###

Linear System of Equations
--------------------------

Local
~~~~~

This module contains pure ``numpy`` implementation of the secure LSE algorithm.

.. currentmodule:: secout.LSE.local

.. autosummary::
    secure_mask
    slse_transformation
    ppcgm
    solve

.. autofunction:: secure_mask
.. autofunction:: slse_transformation
.. autofunction::  ppcgm
.. autofunction:: solve

Dask
~~~~



.. currentmodule:: secout.LSE

..  autoclass:: DaskLSE
    :members:

Quadratic Programming
---------------------

Dask
~~~~

This module contains

.. currentmodule:: secout.QP

.. autoclass:: DaskQP
    :members:
    :undoc-members:

