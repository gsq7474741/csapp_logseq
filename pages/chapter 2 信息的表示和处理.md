deck:: my::csapp::chapter 2 信息的表示和处理

- meta
	- start:: ((63b2fe3b-55f9-4ac1-8abf-3fa84fceb5a7))
	- answer:: ((63b34926-efad-4409-aa3e-63413015a070))
	- end:: ((63b4a733-7fad-4c8a-8410-8c9c570439f8))
	- [[chapter 2 cards]]
-
- 整数次幂转换
  id:: 63b2ffa2-cd74-4aac-8179-0dbf0973e4d1
  card-last-interval:: 4
  card-repeats:: 1
  card-ease-factor:: 2.6
  card-next-schedule:: 2023-01-07T20:17:54.885Z
  card-last-reviewed:: 2023-01-03T20:17:54.885Z
  card-last-score:: 5
	- ((63b2ff9d-223d-49e0-9672-e586a6f012a6))
	- n次幂 :->除以4，系数是0的个数，余数是首位数字 $2^n$
	  id:: 63d9414c-7bbe-46a9-9b45-9d6885bd15f2
	- ```python
	  11 // 4 = 2
	  11 % 4 = 3
	  
	  # 11 = 0x800
	  ```
-
- 大端法-小端法
  card-last-score:: 5
  card-repeats:: 1
  card-next-schedule:: 2023-01-07T20:17:42.408Z
  card-last-interval:: 4
  id:: 63d9414c-c5c8-4741-8e63-cf1c9d6ab351
  card-ease-factor:: 2.6
  card-last-reviewed:: 2023-01-03T20:17:42.409Z
	- ((63b2fbe3-4240-469f-b379-7fe4304c0230))
	- 常见的内存布局是{{c1 小端法}} ，即{{c1 逆序}}
	  id:: 63d9414c-489c-4605-9fc2-bc40ad8dbb27
-
- ((63b3045f-bf14-49bd-9a57-84c6d8aead52)) ((63b34a1a-9983-4201-ab1f-4e0d4de41f0f))
	- A
		- 0x0035 9141 => 0000 0000 0011 0101 1001 0001 0100 0001
		- 0x4A56 4504 => 0100 1010 0101 0110 0100 0101 0000 0100
	- B
		- ______001 ^^1010 1100 1000 1010 0000 1^^
		- 010010100 ^^1010 1100 1000 1010 0000 1^^ 00
		- 21位对齐
	- C
		- 头尾部分
		- ((63b34a28-9bc2-4bdb-8f6c-ea40cc76c4e6))
-
- ((63b34a8b-408b-4013-b7d9-453bae43a4de)) ((63b34aa5-65f5-4ad6-9aaf-184d663919bd))
	- 61 62 63 64 65 66
	- ((63b34ab2-9014-44ad-a54a-eed2a4918bd8))
-
- ((63b31543-de39-40c9-8490-77ee207f6b31)) ((63b46997-d35d-4cf7-aa52-5c95eac291af))
	- ~a  1001 0110
	- ~b  1010 1010
	- a&b 1000 0010  看题。。。 0100 0001
	- a|b 1011 1110
	- a^b 0011 1100
-
- ((63b31665-14a3-4494-9102-7ef622cdaab3)) ((63b46a41-d168-42f6-b976-cd053fd9f4a2))
	- A
		- 黑-白
		- 蓝-黄
		- 绿-红紫
		- 红-蓝绿
	- B
		- 蓝 | 绿 = 蓝绿
		- 黄 & 蓝绿 = 绿
		- 红 ^ 红紫 = 蓝
-
- ((63b33960-8ebd-4215-a995-6d68d22f8197)) ((63b46a87-30bf-4ba6-9213-cde380777bc8))
	- |步骤|*x|*y|
	  :LOGBOOK:
	  CLOCK: [2023-01-03 Tue 04:18:30]--[2023-01-03 Tue 04:18:31] =>  00:00:01
	  :END:
	  |--|--|--|
	  |初始   | a | b |
	  |step 1| a | a^b |
	  |step 2| a^a^b | a^b |
	  |step 3| a^a^b | a^a^b^a^b |
	  |result| b | a |
	- ((63b46aaa-54b7-4f0f-bdce-d10b40f0a7af))
-
- ((63b33dcf-3e54-4aa7-a762-3817fbe60afe)) ((63b46ada-fa79-4154-8da3-c83f7e219b77))
	- A
		- k+1 ^^应该是k 索引从0开始^^
	- B
		- 因为 `a[k+1] ^ a[k+1] = 0`
	- C
		- change `<=` to `<`
-
- ((63b33f32-180a-4e9d-aafd-87b99bad495d)) ((63b48b1c-ec84-47e9-be0b-16f1461b330f))
	- A
		- x & 0xFF
	- B
		- ~x & ~0xFF | (x & 0xFF)  ^^x ^ ~0xFF^^
	- C
		- x | 0xFF
-
- ((63b34489-090b-4c26-8827-71b2e88927b7)) ((63b48b32-1f36-4ac5-81d6-7fd1d13ab44a))
	- bis(x, m) = m | x
	- bic(x, m) = ~m & x
	- bis(x, y)
	- bis(bic(x, m), bic(m, x))
-
- 逻辑运算
	- ((63dfe471-8572-4787-82a6-9a9e4335c599))
	- c语言中{{c1 所有非零参数}}表示True，{{c1 参数0}}表示False
	  id:: 63dfe482-ec41-4298-b662-d852dd0faab4
	- 逻辑运算是{{c1 2}}个字符
	  id:: 63dfe4be-29a0-4c91-8c9e-6f5f4dca3a7d
-
- ((63b346ae-5388-4d5f-bac4-05fbcd915192)) ((63b48b43-ab7a-408c-9fd6-f83fc6588226))
	- {{renderer :luckysheet, e2.14@1672776520270}}
-
- ((63b46193-5e7c-4994-ae1b-7d6228997873)) ((63b48b50-9d57-499d-a342-bbd9dbb4f67d))
	- ! (x ^ y)
-
- 两种形式的右移
	- ((63b46390-199c-49cb-936a-43f440ba2f3f))
	  card-last-interval:: 4
	  card-repeats:: 1
	  card-ease-factor:: 2.6
	  card-next-schedule:: 2023-01-07T20:18:04.775Z
	  card-last-reviewed:: 2023-01-03T20:18:04.775Z
	  card-last-score:: 5
	  id:: 63d9414c-75cb-4d71-b24a-7a250c4f728e
	- 逻辑右移在左端补{{c1 k 个 0}}
	  id:: 63df97e6-4486-41f9-a759-92eb107338cf
	- 算术右移在左端补{{c1 k 个 最高位}}
	  id:: 63df984a-36b5-4010-bb5b-6556dd8fd67d
	- 有符号数，一般使用{{c1 算术}}右移
	  id:: 63df986a-122f-496b-9fbb-0defb9987624
	- 无符号数，必须使用{{c1 逻辑}}右移
	  id:: 63df9891-81ca-4095-97af-a924af4a323e
-
- ((63b465e9-2df0-408b-b057-8a95c5be2cd5)) ((63b46914-c7c7-4399-8e6c-d73044248679))
	- {{renderer :luckysheet, 2.16@1672831964003}}
	-
-
- 大量移位
	- ((63b48b70-c4b0-48dd-917d-04925b1cb220))
	  card-last-interval:: 4
	  card-repeats:: 1
	  card-ease-factor:: 2.6
	  card-next-schedule:: 2023-01-07T20:18:07.312Z
	  card-last-reviewed:: 2023-01-03T20:18:07.312Z
	  card-last-score:: 5
	  id:: 63d9414c-ad08-4680-8ce8-284379ef64a3
	- 只考虑{{c1 $log_2w$}}  位
	  id:: 63d9414c-1fcb-46be-9ec8-620fef7270fb
-
- 整数的数据与算数操作术语
	- ((63b4a54a-23a3-460b-b31c-e3e9000fb389))
-
- 正负$T_{max}$范围
	- ((63b4a654-bf03-463d-8a58-bf3077966025))
	- 负数范围（绝对值）比正数范围{{c1 大1}}
	  id:: 63d9414c-6b40-4674-8b85-f7106dd948d2
	- -32768 ~ 32767
-
- 无符号数编码
	- ((63b560a8-9130-4cb3-ba99-e2caf1039bd3))
	- 公式 #card
	  id:: 63d9414c-43dd-4624-95ed-f745a30f5c68
		- $$B2U_w(\vec{x})=\sum_{i=0}^{w-1}x_i2^i$$
	- 就是正常的二进制转整数
	- 范围 $B2U_w: {\{0,1\}}^w\to$ {{c1 $\{0,...,2^{w-1}\}$}}
	  id:: 63d9414c-1511-45a2-8f84-2c643d662872
-
- 补码编码
	- ((63b56268-9597-4e6c-88dd-fe4fdea85557))
	- 公式 #card
	  id:: 63dfe53d-aded-4d07-abd9-2f498cbf906f
		- $$B2T_w(\vec{x})=-x_{w-1}2^{w-1}+\sum_{i=0}^{w-2}x_i2^i$$
	- 最高位权重为{{c1 $-2^{w-1}$}}  ,用条形图直观理解
	  id:: 63d9414c-7c4e-44a8-a374-c201b484e0e2
	- ((63b56332-8152-41ae-a3ac-f3c905a455d0))
	- ((63b5635b-c7c9-4407-80f2-4b62184cab15))
	- 范围 $B2T_w: {\{0,1\}}^w\to$ {{c1 $\{-2^{w-1},...,2^{w-1}-1\}$}}
	  id:: 63d9414c-72f4-441e-8073-e1f5198fc574
-
- ((63b563c8-9508-4627-a170-49ea36447402)) ((63b56502-6a82-478f-932f-b8db772a336f))
	- {{renderer :luckysheet, 2.17}}
	-
-
- ((63b565ba-79e6-4fde-88d3-b47d0c1bcccb))
- ((63b568ae-5247-4557-87b4-d8cf179a02ed))
	- ```asm
	  			BA98 7654 3210
	  sub	0x2e0	0010 1110 0000 : 736
	  mov -0x58	
	  ```
-
- 补码与无符号数的关系 #unsure
	- ((63b5ec75-00ec-43a9-9ed3-1b013af66b00))
	- $$\begin{cases}
	    & |x|+T2U_w(x)=2^w , x<0\\
	    & x+|U2T_w(x)|=2^w , x>0\\
	  \end{cases}$$
-
- ((63b5edee-9fe1-41ae-a3ac-7cf02dc12608))
	- {{renderer :luckysheet, workbook@1672867376673}}
	-
-
- 补码转无符号数
	- ((63b5eee0-dcc0-4e96-84b3-77b271a2bf06))
	- 公式 #card
	  id:: 63dfe5c2-2c68-4a1f-8b42-bf401dc8b4d8
		- $$T2U_w(x)=\begin{cases}
		    & x+2^w &, x<0\\
		    & x     &, x\ge0\\
		  \end{cases}$$
-
- ((63b5ef7e-ebe1-4bdb-a0ea-f5ffb0b24194))
	- 正数和零不变，负数加16
-
- 无符号数转补码
	- ((63b5efbf-f60e-455d-ba8e-27ce6238350d))
	- 公式 #card
	  id:: 63dfe63a-68aa-4cf1-8368-059a475d0d37
		- $$U2T_w(u)=\begin{cases}
		    & u &, u\le TMax_w\\
		    & u-2^w     &, u>TMax_w\\
		  \end{cases}$$
-
- ((63bc47ce-8423-46ea-bfd2-acc0ffce9386))
-
- ((63bc494f-3191-4b0e-9bfa-5f5cdee51193))
-
- ((63bc49d2-1e66-4262-8c08-4d2a51d46f6f)) ((63bc4c81-0bcf-4295-bec1-facc0b6caf63))
	- {{renderer :luckysheet, workbook@1673284063474}}
	-
-
- ((63bda1ab-9ff5-4c49-ad65-42f518906fe0))
	- ((63bda197-044e-4dd3-b5d1-046b1ab61bf0))  补0
	- ((63bda1a5-ed80-4161-bafc-e3fba1ef9081))  补最高位
-
- ((63bda27c-74b2-4814-91ee-41fb8187f5ef)) ((63bda604-5b3e-40f8-94d3-1618273a593f))
	- 1011
		- $$-2^3+2+1=-5$$
	- 1 1011
		- $$-2^4+8+2+1=-5$$
	- 11 1011
		- $$-32+16+8+2+1=-5$$
-
- ((63bda3bb-ad0e-4966-bf95-7a453818c711))  ((63bda610-b646-4f7b-8800-082ac6c88c43))
	- ```c
	  int fun1(unsigned word) { 
	    return (int) ((word << 24) >> 24);
	  } 
	  
	  int fun2(unsigned word) {
	    return ((int) word << 24) >> 24;
	  }
	  ```
	- {{renderer :luckysheet, workbook@1673372724260}}
	- ((63bda62a-38ed-4ca3-9db2-e3674e3eea0b))
-
- ((63bda647-a176-4782-be6e-7c8baa4cf68a))
	- ((63bda65d-4fe8-4ad3-9674-cdd58f505c03))
	- ((63bda669-7869-4a70-8e44-41a60786ab1f))
	- ((63bdd217-289e-4db3-aee0-61bfa2f764a7))
-
- ((63bdd227-d36b-457c-a3aa-f0733a9c5f3e)) ((63bdd52b-dd23-46d8-8b18-7a6199659c90))
	- 4 bit -> 3 bit
	- {{renderer :luckysheet, workbook@1673385396546}}
	-
-
- ((63be7842-23df-45fd-bb0f-3d8e0a33de24)) ((63be7acb-941e-443d-8907-28d7d6278c2f))
	- i <= length-1 这个比较处，当length=0时，数组越界
	- 修改：加分支判断，length为0直接返回0.
-
- ((63be79c6-3fb1-42f9-95c5-4b12547f4874)) ((63be7ad7-5650-4dca-8730-f24238de3af1))
	- A
		- s的长度小于t的长度时，可能会产生无符号减法溢出
	- B
		- 减法溢出
	- C
		- 改为直接判断大小
-
- ((63be82a1-af16-44c4-b047-1ec1febc268a))
	- ((63be82ae-0b8c-4a75-af35-51569e3adcbe))
	- ((63be82ed-1ca3-4a0e-90d2-69748eaf2922))
	- ((63be8348-b005-443c-8099-6d7f21f9b404))
		- 结果小于其中一个加数时发生溢出，溢出时一定会小于其中的任意一个
-
- ((63be83c4-3534-4684-b2e0-f399263367f5)) ((63be8431-60a5-400c-8394-8fc4e23075a3))
	- ```c
	  int uadd_ok(unsigned x, unsigned y){
	    unsigned res = x + y;
	    // return res > x && res > y;
	    return res >= x;
	  }
	  ```
-
- ((63be8555-fed4-4f26-8bf8-f70d0ea1a36b))
	- ((63be8560-1dd7-4ebc-8ce7-13487e76fb50))
	- 无符号加法逆元为 $2^w-x$ or 0
-
- 阿贝尔群
	- ((63df5996-4823-4208-b180-c4895a5c7c97))
	- 阿贝尔群的性质 #card #incremental
	  id:: 63df5999-84e5-45f4-b628-605df9d55f07
		- 可交换
		- 可结合
	- 阿贝尔群中元素的性质 #card #incremental
	  id:: 63df5af1-7b56-4d6f-866c-12fd2cb4ac2c
		- 有单位元 0
		- 每个元素有一个加法逆元
-
- ((63be85ae-0943-4d35-8801-ba4b0e56e0e8)) ((63be862a-6a78-4d98-a742-c2ce39f8f6aa))
	- {{renderer :luckysheet, workbook@1673430461468}}
	-
-
- $$a_n=a_{n-2}+a_{n-3}-1$$
-
- 补码加法
	- ((63e09d47-8e2e-48d1-981e-25843a4a88f7))
	- 正溢出的结果为{{c1 $x+y-2^w$}}
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-