
# FLAMES

<img  src="inst/images/FLAMES-01.png">

This branch is for verifying outputs with [the R debug pipeline](https://github.com/OliverVoogd/FLAMES/tree/debug). Sorting is used excessively to force results being exactly the same to the debug branch of the Python `FLAMES` pipeline, this may lead to more memory usage and longer running time.


[The initial `FLAMES` pipeline](https://github.com/LuyiTian/FLAMES) was written in Python 2, and certain operations in Python 2 significantly reduced the reproducibility of outputs. For example, the order of `dict.keys()` or `Counter.most_common()` is not deterministic. The `FLAMES` `R` version uses Python 3.7 or higher, where most of these operations are now deterministic^. To verify the difference in outputs between the original Python 2 pipeline and the `R` pipeline is solely due to non-deterministic operations in Python 2, this branch and the debug brach of the Python pipeline uses sorting to force `dict.keys()`, `Counter.most_common()` etc. to have the same order in both pipelines.


### ^*Changes since python 2.7*

> Changed in version 3.7: Dict order is guaranteed to be insertion order.

<https://docs.python.org/3.7/library/stdtypes.html#typesmapping>

> Changed in version 3.7: As a dict subclass, Counter inherited the capability to remember insertion order. Math operations on Counter objects also preserve order. Results are ordered according to when an element is first encountered in the left operand and then by the order encountered in the right operand.

<https://docs.python.org/3/library/collections.html?highlight=counter#collections.Counter>
