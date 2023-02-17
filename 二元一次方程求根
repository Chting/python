#!/usr/bin/python3
#求ax^2 + bx + c = 0的根
import math
def quadratic(a, b, c):
  if not (isinstance(a, (int, float)) and isinstance(b, (int, float)) and isinstance(c, (int, float))):
   raise TypeError('bad operand type')
  if a != 0:
   r = b**2 - 4 * a * c
   if r < 0:
    print ('方程 ax^2 + bx + c = 0 无实数根！')
   elif r == 0:
    print ('方程 ax^2 + bx + c = 0 有两个相等的实数根！')
    root = -b / (2 * a)
    print ("根为: %f" % root)
   else:
    print ('方程 ax^2 + bx + c = 0 有两个不等的实数根！')
    root1 = -b + math.sqrt(r) / (2 * a)
    root2 = -b - math.sqrt(r) / (2 * a)
    print ("根为:%f, %f" % (root1, root2))
  else:
   print ('a不能等于0')
a,b,c = (input('三个数:').split())
quadratic(float(a), float(b), float(c))
