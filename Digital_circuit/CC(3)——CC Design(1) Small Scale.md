#DCorMCU 
## 小规模逻辑电路的设计
直接列真值表，写逻辑表达式，画电路图即可

### 优先编码器
每一个输入端含有优先级，允许多个输入同时被置 `1`，但是根据优先级确定输出
例如：扩展一个优先编码器
![[Pasted image 20230316105601.png|250]]

![[Pasted image 20230316110942.png|400]]


### 译码器
注意：译码器的输出是所有的最小项，因此译码器可以实现所有的逻辑函数
常用的的译码器是 `74 LS 138` 
![[Pasted image 20230316112624.png|500]]

### 显示译码器
![[Pasted image 20230321132345.png|400]]

显示译码器是一种将二进制数据转换成显示设备（例如七段数码管）显示信号的设备。`74LS47` 是输出低电平有效（驱动共阳极管），`74LS48` 则是输出高电平有效（驱动共阴极管） 

- LT：测试——低电平时所有灯点亮
- RBI：灭零——低电平有效，启动时灭零
- BI/RBO：输入：外部低电平时所有灯熄灭；输出——输入为 0 时输出低电平

利用这些端口，我们可以实现一些功能：例如，一个六位数码管我们不想让高位和低位显示 0，次高位和次低位的 0 需要根据最高位和最低位确定，个位和十分位两位不允许必须显示 0，那么：最高位和最低位的 RBI 接地；次高位和次低位的 RBI 由高维 BI/RBO 提供，个位和十分位 RBI 接 1

### 数值比较器
数值比较器负责检测两个数的大于、小于和相等。显然，应该从高位开始比较，只有当两个数的所有位全相等时，两个数才相等。
常用的 4 位数字比较器是 `74LS85` 
![[Pasted image 20230321135056.png|400]]
其中，三个 I 接口用于级联
![[Pasted image 20230321135621.png|400]]

低位输出连接到高位输入即可

