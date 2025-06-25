# python testing

## test runners

one can write all test functions and call them one by from main code block

``` python
def test_one():
    assert sum([1,2]) == 3

def test_two():
    assert sum([1]) == 1

if __name__ != "__main__":
    test_one()
    test_two() 
```

but this is not sufficient when there are many tests. Hence there are test runners which are special programs which run all tests, help with debugging etc. Famous test runners are -

1. unittest - builtin python
1. pytest
1. nose

these are not just test runners. these are also test frameworks.

### unittest
TestCase base class has many utility methods e.g.

``` python
import unittest


class TestSum(unittest.TestCase):

    def test_sum(self):
        self.assertEqual(sum([1, 2, 3]), 6, "Should be 6")

    def test_sum_tuple(self):
        self.assertEqual(sum((1, 2, 2)), 6, "Should be 6")

if __name__ == '__main__':
    unittest.main()

```

## test discovery

it seems pytest is better when it comes to test discovery when compared to unittest.
unittest failed once the test files were moved from root folder to src/test folder.
