import re
import statistics

fname = 'test.txt'
output = []

try:
    fhand = open(fname)
except:
    print('File cannot be opened:',fname)
    exit()

for line in fhand:
    line = line.rstrip()
    if line.startswith('Reply'):
        stuff = line.split()
        rand = re.split('(\d+)', stuff[4])
        output.append(rand[1])

output = list(map(int, output))

a = len(output)
print('Entries =', a)
b = min(output)
print('MIN =', b)
c = max(output)
print('MAX =', c)
d = sum(output)/len(output)
print('AVG(mean) =', d)
e = statistics.stdev(output)
print('Standart deviation =', round(e, 5))
