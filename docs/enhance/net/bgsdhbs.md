# 办公室电话接入部署

[[toc]]

## 电话部署概况

号码清单.xlsx的 线架编号 为：配线架模块的外部卡座编号。深色（绿色）的代表所处楼层没有这样的号码，可能由于迁移或注销等原因。分机号码由运营商及代理商、高科通信（乙方）负责。

![test.png](https://i.loli.net/2020/10/24/5Rvxj1koNsa9eyX.png)

楼层座位平面图的座位电话线路编号为：内部编号。如平面图21号座位33号码的电话，为了布线方便，企业网管会将座位与电话内线编号对应，座位21，内线也为21；电话主机的**外线编号**是由运营商/代理商设定的，也就是说电话的外线与内线编号并非互相一致，当然也可以要求他们运营商将分机号码的内线编号设成与内线一样的编号。

不过我们早已和运营商沟通将电话的外线编号设定成与内线编号一致，这样就不用在额外做一张每个电话的外线表了。

![13-22-31.png](https://i.loli.net/2020/10/24/Gnj4ykATYbdsNVx.png)

机房配线架电话编号详细：外部与内部的数字编号相互之间是独立的
* 配线架为5行10列的排序分布
* 蓝色部分为外部编号：依次10-80
* 绿色部分为内部编号：依次10-100

内外线为上下分割方式，当然也可以根据企业部门需求进行左右划分。

![1234.png](https://i.loli.net/2020/10/24/7Dw6h5YVWsvJFTH.png)



## 接线操作方法

将电话线放置对应卡槽，手握线钳且正面朝上，快速用力推进去。听到咔嚓一声，说明已将电话线卡住对应编号模块内，如图示。

![234.png](https://i.loli.net/2020/10/24/IYOu6xqmJB4CPQ1.png)

使用测试电话的两根铜线接入到内线编号卡槽进行测试

![2341.jpg](https://i.loli.net/2020/10/24/IKGUmnpqwOFvejM.jpg)

并拿起电话，听下是否有拨号音，图中电话亮灯**且有拨号音**说明没问题。

![4321.png](https://i.loli.net/2020/10/24/dEJFs8tNaVcCrSn.png)

## 故障排查

### 寻线

比如说34卡座端口，首先插入电话线，然后将寻线仪按钮调整到寻线功能提示灯位置，此时寻线仪会释放信号。

![12221.png](https://i.loli.net/2020/10/24/xCHsvDn26Uqrf4h.png)

此时将接收器打开

![2323.png](https://i.loli.net/2020/10/24/4W7KgY3mUBHGzod.png)

到机房的内线34卡槽，测试会听到类似报警的信号声音，这里要注意：听到信号声不代表就一定是那根线的卡槽位，而是取决于信号音的强弱。如果是连那根线的卡槽位信号声响都太弱的话，则是电话线路也存在一定问题。接着我们进行短路测试！

### 短路测试

万用表开关调入Ω下方蜂鸣标处，对准需测试的卡槽两端，检测是否有无电阻，有提示声音，则代表无电阻，短路。

可参考 [万用表怎么测短路](https://zhidao.baidu.com/question/300430513.html)

![2332.png](https://i.loli.net/2020/10/24/D5qMvbWaNQ2wBTU.png)

### 故障处理

测线仪有信号，但跳线时仅有电流音，说明外线不通、或内线断开。用铜线对准外线卡槽测试，是否能正常拨号（有拨号音），如果外线不通，查看光猫、电话交换机电源、线路是否接入正常。内线不通根据布线方式进行重新拉线或更换其他座位处理。

## 呼叫转移

设置需求：避免不在座机旁漏接电话；首先，联系运营商开通呼叫转移，有三种情况:
* 全部转移:在固定电话上按“`*57*手机号码#`”,取消方法在固定电话上按“#57#”
* 遇忙转移:固定电话上按“`*40*手机号码#`”,取消方法按＂#40#＂
* 无人接听转移:按“`*41*手机号码#`”,取消方法按“#41#”

名词示意

* 全部转移（无条件转移）：设置后所有来电将立即转接到预先设定的固定电话或其他信息工具上。
* 遇忙转移：用户在通话过程中有第三方对其呼叫，将电话转移至预先设好的固定电话或其他通信工具上。如果没有设置无应答呼叫转移，拒绝接听时也会将这个电话视为遇忙呼叫转移。
* 不接听转移：接通后而无人应答对所发生的电话转移，一般手机上振铃超过6次而接听则视为无应答转移。