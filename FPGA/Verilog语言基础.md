# Verilog语言基础
## 1. timescale
timescale一般用于仿真激励文件中，它用来定义仿真的时间单位和时间精度，时间精度不能大于时间单位，且数字只能是1,10,100。具体地：
```
`timescale 1ns / 1ps
```
```
`timescale 100ns / 10ns
```
## 2. Vivado XDC约束文件
主要完成管脚，时钟，以及组的约束。
- 配置CFGBVS管脚电压
```
set_property CFGBVS VCCO [current_design]
```
- 配置电路的电压
```
set_property CONFIG_VOLTAGE 3.3 [current_design]
```
- 配置普通IO管脚，只需约束引脚号和电压。端口号若为数组，需要用{}括起来
```
set_property PACKAGE_PIN 引脚编号 [get_ports 端口名称]
set_property IOSTANDARD 电压 [get_ports 端口名称]
```
- 约束时钟周期，差分时钟只要定义和约束P脚
```
create_clock -period 5 [get_ports sys_clk_p]
```
## 3. FPGA供电电压
- 核心电压VCCINT，为内部逻辑门和触发器供电
- IO电压VCCO（Xilinx，Altera简称VCCIO），通常以Bank为界，一个Bank内只存在一种电源电压，每个Bank可以与一种电平接口芯片通信。
- 辅助电压VCCAUX，为一些模拟组件提供独立稳定的电源，如DCM数字时钟，高速串并转换器等










