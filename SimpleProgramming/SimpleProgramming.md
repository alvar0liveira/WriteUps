# Simple Programming CTF 

From [CTFLearn](https://ctflearn.com/challenge/174)

Get the number of lines where the # of 0 is multiple of 3 OR the # of 1 is multiple of 2

```python 
import functools
import operator

file = open('data.dat', 'r')

counter = 0

for l in file:
	# Convert the line into bits and remove the newline at the end
        line = [ int(x) for x in str(l).rstrip()]

	#  Accumulate the numbers of 1, because the sum of 1's == # of 1's
        sum1 = functools.reduce(operator.add, line)

	# Because its binary the number of 0's is going to be equal to length line minus the number of 1's (or the sum)
        sum0 = len(line) - sum1 

        if sum1 % 2 == 0 or sum0 % 3 == 0 :
                counter += 1


print('CTFlearn{' + str(counter) + '}')

```
