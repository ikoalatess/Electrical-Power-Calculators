# Electrical-Power-Calculators

我需要制作一个H5静态页面, 主要是用作移动设备展示, 技术可以使用 HTML + CSS + Vue + Bootstrap

功能参考 https://www.generatorsource.com/Power_Calculator.aspx

页面的尽可能的简洁, 按钮和各种样式尽可能利用 Bootstrap 样式设置美观

页面主要分四个部分

第一个部分, 是信息展示, 使用 table 作为信息展示
Calculation, Guide to Standard Uints,;
Power Calculator,Kilo Volt Amperes,kVA;
Converting kVA to kW,KiloWatts (1000 watts = 1 kW),kW;
Converting kW to kVA,Ampere (Volt-Amperes or Current),I;
Converting kW to HP,Volts,E;
Amperes when kVA is known,Power Factor,PE;
kVA Required to run motors,Percent Efficiency,%EFF;
,Horse Power,HP;
第一行为表格标题,第一行最后一列标题为空, 最后一行第一列为空, 内容我如上, 我使用 "," 分割, 使用 ";" 结尾, 要利用好 Bootstrap 自带样式美化表格

第二部分, 是一个计算展示, 标题是 Power Requirement Calculator
主要有以下几项
Phase 项, 类型 radio, 值为 1 或者 3
Volts Required V 项, 类型为 input, 值为用户输入, 默认值 380, 仅可以输入数字
Amperes I 项, 类型为 input, 值为用户输入, 默认值 240, 仅可以输入数字
Power Factor 项, 类型 radio, 值为 0.8 或者 1
计算按钮, 点击即可根据前面几项值算后面的结果
Power kW 为前面几项计算获取的值
单相公式 Power kW = (Volts × Amperes × Power Factor) / 1000
三相公式 Power kW = (√3 × Volts × Amperes × Power Factor) / 1000
功能参考 https://www.generatorsource.com/Power_Calculator.aspx

第三部分, 主要是电力单位的换算
主要有以下几项换算
    Converting kW to kVA
        kW 项默认值 480
    Converting kW to HP
        kW 项默认值 50
    What size genset is needed to start a 3 phase electric motor Direct on Line (DOL) start
        HP of Motor 项默认值 85
    上面三个换算要使用 Vue做双向绑定, 输入任意一端, 都可以计算对应的换算结果
功能参考 https://www.generatorsource.com/Power_Calculator.aspx

第四部分, 是一个计算展示, 标题是 Calculating Amperes (when you know kVA)
主要有以下几项
"Phase 1,2,3" 项, 类型为 input, 值为用户输入, 默认值 1, 仅可以输入数字
"Generator kVA" 项, 类型为 input, 值为用户输入, 默认值 500, 仅可以输入数字
"Volts Required" 项, 类型为 input, 值为用户输入, 默认值 240, 仅可以输入数字
计算按钮, 点击即可根据前面几项值算后面的结果
"Ampere I" 为前面几项计算获取的值
功能参考 https://www.generatorsource.com/Power_Calculator.aspx

按钮和各种样式尽可能利用 Bootstrap 样式设置美观

页面最下面写一段说明提示内容为:
"**法律免责声明：**
涉及复杂的电气计算时，建议咨询持证电工。本页面提供的计算工具仅用于生成一般性估算结果。在大多数情况下，还需考虑许多额外因素（例如海拔、现场条件、铁损、电机效率等）。如果您仍然不确定或需要帮助分析当前情况，欢迎随时联系我们咨询。"

------------------------------------------------------------------------------

Power Requirement Calculator 这样优化吧
Phase , Volts Required (V), Amperes (I), Power Factor, " = ", Power kW 这几项为一行, 下面一行为对应的 radio, input, input, radio, 计算按钮, input

电力单位换算
Converting kW to kVA 为一行
input kW, = 按钮, input kVA 为一行

Converting kW to HP 为一行
input kW, = 按钮, input HP 为一行

What size genset is needed to start a 3 phase electric motor Direct on Line (DOL) start 为一行
input HP, = 按钮, input kW 为一行

点击按钮要可以计算, 不点击也要做双向绑定计算, 还有就是默认值也要计算对应的比如480 kW 对应 600 kVA

Calculating Amperes (when you know kVA)参考
Phase , Generator kVA, Volts Required, " = ", Ampere I 这几项为一行, 下面一行为对应的 input, input, input, 计算按钮, input 结果

还有就是 信息展示, "Power Requirement Calculator", "电力单位换算", "Calculating Amperes (when you know kVA)" 这四部分需要用样式区分开了,现在感觉像一整块,不是很明显, 参考优秀的设计,如果参考不了就加上淡淡的底色区分吧

------------------------------------------------------------------------------

还是优化错了
Power Requirement Calculator
Phase , Volts Required (V), Amperes (I), Power Factor, " = ", Power kW 这几项为一行, 下面一行为对应的 radio, input, input, radio, 计算按钮, input
总共两行,一行是标题 "Phase , Volts Required (V), Amperes (I), Power Factor, " = ", Power kW",一行是 "radio, input, input, radio, 计算按钮, input"
需要对应上

电力单位换算
Converting kW to kVA 为一行
input kW, = 按钮, input kVA 为一行

Converting kW to HP 为一行
input kW, = 按钮, input HP 为一行

What size genset is needed to start a 3 phase electric motor Direct on Line (DOL) start 为一行
input HP, = 按钮, input kW 为一行

上面总共有6行

点击按钮要可以计算, 不点击也要做双向绑定计算, 还有就是默认值也要计算对应的比如480 kW 对应 600 kVA


Calculating Amperes (when you know kVA)参考
Phase , Generator kVA, Volts Required, " = ", Ampere I 这几项为一行, 下面一行为对应的 input, input, input, 计算按钮, input 结果
总共两行,一行是标题 "Phase , Generator kVA, Volts Required, " = ", Ampere I",一行是 "input, input, input, 计算按钮, input"
需要对应上

所有计算小数点保留2位

