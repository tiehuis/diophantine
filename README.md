# Diophantine

Provides methods for solving quadratic and linear diophantine equations.

Diophantine equations are of equations of the form:

```
Ax^2 + Bxy + Cy^2 + Dx + Ey + F = 0
```

where the solutions `x` and `y` are in the set of integers.

The methods used to solve these are those specified [here](https://www.alpertron.com.ar/METHODS.HTM).

## Examples

```
extern crate diophantine;

use diophantine::Solution;

fn main() {
    // 0x^2 + 0xy + 0y^2 + 0x + 6y + 12 = 0
    let sol1 = diophantine::solve(0, 0, 0, 0, 6, 12);

    match sol1 {
        // single solution
        Solution::Single(x) => {
            println!("{:?}", x);
        }

        // finite set of solutions
        Solution::Multiple(x) => {
            println!("{:?}", x);
        }

        // an iterator over an infinite sequence of solutions
        Solution::Recurrence(eq) => {
            println!("{:?}", eq.take(5).collect::<Vec<_>>());
        }

        // multiple recurrences can be found
        Solution::Recurrences(eq) => {
            println!("{:?}", eq);
        }

        // always check the case where no solution exists
        Solution::None => {
            println!("no solution found");
        }
    }
}
```
