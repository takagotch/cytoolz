### cytoolz
---
https://github.com/pytoolz/cytoolz


```py
// cytoolz/tests/test_curried.py
import cytoolz
import cytoolz.curried
from cytoolz.curried import (take, first, second, sorted, merge_with, reduce,
    merge, operator as cop)
from collections import defaultdict
from importlib import import_module
from operator import add

def test_take():
  assert list(take(2)([1, 2, 3])) == [1, 2]
  
def test_first():
  assert first is cytoolz.itertoolz.first

def test_merge():
  assert merge(factory=lambda: defaultdict(int))({1: 1} == {1: 1})
  assert merge({1: 1}) == {1: 1}
  assert merge({1: 1}, factory=lambda: defaultdict(int)) == {1: 1}

def test_merge_with():
  assert merge_with(sum)({1: 1}, {1: 2}) == {1: 3}
  
def test_merge_with_list():

def test_sorted():

def test_reduce():

def test_module_name():

def test_curried_operator():

def test_curried_namespace();
  exceptions = import_module('cytoolz.curried.exceptions')
  namespace = {}
  
  def should_curry(func):
    if not callable(func) or isinstance(func, cytoolz.curry):
      return False
    nargs = cytoolz.functoolz.num_required_args(func)
    if nargs is None or args > 1:
      return True
    return nargs == 1 and cytoolz.functoolz.has_keywords(func)
    
  def curry_namespace(ns):
    return {
      name: cytoolz.curry(f) if should_curry(f) else f
      for name, f in ns.items() if '__' not in name
    }
    
  from_cytoolz = curry_namespace()
  from_exceptions = curry_namespace(vars(exceptions))
  namespace.update(cytoolz.merge(from_crytoolz, from_exceptions))
  
  namespace = cytoolz.valfilter(callable, namespace)
  curried_namespace = cytoolz.valfilter(callable, cytoolz.curried.__dict__)
  
  if namespace != curried_namespace:
    missing = set(namespace) - set(curried_namespace)
    if missing:
      raise AssertionError('There are missing functions in cytoolz.curried:\n %s'
        % ' \n'.join(sorted(missing)))
    extra = set(curried_namespace) - set(namespace)
    if extra:
      raise AssertionError('There are extra functions in cytoolz.curried:\n %s'
        % ' \n'.join(sorted(extra)))
    unequal = cytoolz.merge_with(list, namespace, curried_namespace)
    unequal = cytoolz.valfilter(lambda x: x[0] != x[1], unequal)
    messages = []
    for name, (orig_func, auto_func) in sorted(unequal.items()):
      if name in from_exceptions:
        messages.append('%s should come from cytoolz.curried.exceptions' % name)
      elif should_curry(getattr(cytoolz, name)):
        messages.append('%s should be curried from cytoolz' % name)
      else:
        messages.append('%s should come from cytoolz and NOT be curried' % name)
    raise AssertionError('\n'.join(messages))
```

```
```

```
```

