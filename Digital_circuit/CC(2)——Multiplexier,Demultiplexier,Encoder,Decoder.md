#DCorMCU 

## 数据选择器
- 如同一个多路开关，选择哪一路的数据最终会被输出
![[Pasted image 20230316100133.png|350]]

显然，这个电路通过两位二进制码控制将哪一路的信号送到输出端
![[Pasted image 20230316100436.png|300]]

### 选择器的自身扩展
选择器可以组成能够选更高位数的选择器，例如，`74LS153` 内部包含两个独立运行的数据选择器
![[Pasted image 20230316101900.png|300]]

## 多路分配器
- 与数据选择器的功能正好相反，多路分配器根据控制信号将一个数据分配到多个输出中的一个
![[Pasted image 20230316102119.png|300]]

## 编码器
3 位二进制编码器
![[Pasted image 20230316103010.png|300]]

