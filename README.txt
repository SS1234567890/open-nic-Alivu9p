################################################################################
# Vivado (TM) v2022.2 (64-bit)
#
# README.txt: Please read the sections below to understand the steps required
#             to simulate the design for a simulator, the directory structure
#             and the generated exported files.
#
################################################################################

1. Simulate Design

To simulate design, cd to the simulator directory and execute the script.

For example:-

% cd questa
% ./top.sh

The export simulation flow requires the Xilinx pre-compiled simulation library
components for the target simulator. These components are referred using the
'-lib_map_path' switch. If this switch is specified, then the export simulation
will automatically set this library path in the generated script and update,
copy the simulator setup file(s) in the exported directory.

If '-lib_map_path' is not specified, then the pre-compiled simulation library
information will not be included in the exported scripts and that may cause
simulation errors when running this script. Alternatively, you can provide the
library information using this switch while executing the generated script.

For example:-

% ./top.sh -lib_map_path /design/questa/clibs

Please refer to the generated script header 'Prerequisite' section for more details.

2. Directory Structure

By default, if the -directory switch is not specified, export_simulation will
create the following directory structure:-

<current_working_directory>/export_sim/<simulator>

For example, if the current working directory is /tmp/test, export_simulation
will create the following directory path:-

/tmp/test/export_sim/questa

If -directory switch is specified, export_simulation will create a simulator
sub-directory under the specified directory path.

For example, 'export_simulation -directory /tmp/test/my_test_area/func_sim'
command will create the following directory:-

/tmp/test/my_test_area/func_sim/questa

By default, if -simulator is not specified, export_simulation will create a
simulator sub-directory for each simulator and export the files for each simulator
in this sub-directory respectively.

IMPORTANT: Please note that the simulation library path must be specified manually
in the generated script for the respective simulator. Please refer to the generated
script header 'Prerequisite' section for more details.

3. Exported script and files

Export simulation will create the driver shell script, setup files and copy the
design sources in the output directory path.

By default, when the -script_name switch is not specified, export_simulation will
################################################################################
# open-nic-Alivu9p
#
# 简要说明：
# 本仓库包含一个 FPGA 网卡（NIC）相关的 Vivado 工程与 RTL 源码，源自
# open-nic 项目的变体（分支/定制版）。仓库主要用于开发、综合与仿真。
#
# 目录概览（仓库根目录）：
# - ip/      : 包含 Vivado IP 目录和导出的 IP 配置文件（.xci、.bd、.bxml 等）
# - prj/     : Vivado 工程文件（.xpr）等构建脚本
# - src/     : RTL 源码（SystemVerilog/Verilog）、顶层封装、约束文件（.xdc）和
#              相关模块（packet_adapter、qdma_subsystem、utility 等）
# - README.txt : 本文件（已整理）

# 重要模块说明（位于 `src/`）：
# - open_nic_shell.sv / open_nic_shell_macros.vh : 项目顶层及宏定义
# - cmac_subsystem/ : 与 CMAC 子系统相关的封装、映射与 wrapper
# - packet_adapter/  : 包装器与收发逻辑（packet_adapter.sv 等）
# - qdma_subsystem/  : 与 QDMA 相关的控制与数据通路实现
# - utility/         : 常用模块（axi-lite、crc32、fifo、arbiter 等）

# 仿真（快速说明）
# 仿真脚本通常位于导出目录（例如 export_sim/<simulator>），并依赖 Xilinx
# 预编译仿真库。若使用导出脚本，请注意传入库路径（-lib_map_path）或在
# 生成脚本头部设置好仿真库映射。例如：
#   ./top.sh -lib_map_path /path/to/xilinx/simlibs
# 仿真工具与流程请参考导出脚本的 "Prerequisite" 部分。

# 使用/构建建议
# - 打开 Vivado：加载 `prj/prj.xpr`（若存在）以查看 block design 与约束。
# - 编辑 RTL：在 `src/` 下修改或添加模块，然后运行 Vivado 综合/实现流程。
# - 仿真：导出仿真文件并按目标仿真器运行生成的脚本（例如 Questa/Xcelium）。

# 其它说明
# - 本仓库曾短暂包含生成的 `assets/` 图片目录（项目插图），应用户要求已移除。
# - 如需恢复或重新生成封面/插图，请在 issue 中说明风格与文件名，我可重新生成。

# 许可与作者
# - 本仓库可能包含多来源代码与 IP，请在商业使用或分发前核查各文件的许可信息。

# 联系
# - 若需帮助整理具体模块、运行仿真或生成文档，请在仓库中留言或直接请求我执行相应任务。

################################################################################

