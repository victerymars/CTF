程序很短，简单看了下逻辑，就是常量数组异或而已，代码如下
```
>>> flag='''45 00 00 00 74 00 00 00  19 00 00 00 69 00 00 00
58 00 00 00 3D 00 00 00  62 00 00 00 0F 00 00 00
66 00 00 00 16 00 00 00  65 00 00 00 3A 00 00 00
0A 00 00 00 64 00 00 00  01 00 00 00 5E 00 00 00
3C 00 00 00 45 00 00 00  1A 00 00 00 75 00 00 00
1B 00 00 00 7E 00 00 00'''.replace('\n',' ').replace('  ',' ').split(' ')
>>> aa=''
>>> for j in range(22):
	aa+=chr(int(flag[j*4],16)^22)

	
>>> aa
'Sb\x0f\x7fN+t\x19p\x00s,\x1cr\x17H*S\x0cc\rh'
>>> 0x45
69
>>> f=[]
>>> for j in range(22):
	f.append(int(flag[j*4],16))

	
>>> f
[69, 116, 25, 105, 88, 61, 98, 15, 102, 22, 101, 58, 10, 100, 1, 94, 60, 69, 26, 117, 27, 126]
>>> for i in range(21):
	print chr(f[i]^f[i+1]),

	
1 m p 1 e _ m i p s _ 0 n e _ b y _ o n e
>>> a=''
>>> a='S'
>>> for i in range(21):
	a+=chr(f[i]^f[i+1])

	
>>> a
'S1mp1e_mips_0ne_by_one'
>>>
```
不幸的是，做完发现，为什么这个串在strings里直接就有啊！这样不太好吧……
