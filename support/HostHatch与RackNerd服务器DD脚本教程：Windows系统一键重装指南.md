# HostHatch与RackNerd服务器DD脚本教程：Windows系统一键重装指南

## 系统重装前的环境准备
在开始DD（Disk Deployment）操作前，需确保服务器已安装必要依赖组件。以下命令需在root权限下执行：

### Debian/Ubuntu系统
bash
apt-get install -y xz-utils openssl gawk file wget screen && screen -S os

### RedHat/CentOS系统
bash
yum install -y xz openssl gawk file glibc-common wget screen && screen -S os

**系统更新提示**：  
若出现依赖异常，建议更新软件源后重试：
- CentOS：`yum makecache && yum update -y`
- Debian：`apt update -y && apt dist-upgrade -y`

👉 [【建议收藏】2025年Racknerd最新优惠套餐整理汇总 - 每日更新可用活动优惠](https://bit.ly/Rack_Nerd)

---

## 智能DD脚本功能解析
该脚本具备以下核心优势：
1. **多平台兼容**：支持国内外主流VPS服务商，特别优化HostHatch、RackNerd等平台的重装体验
2. **网络加速**：针对国内服务器访问海外资源慢的问题，内置加速方案
3. **UEFI支持**：专为Oracle Cloud（甲骨文云）提供3个专用选项（序号23-25）
4. **系统覆盖**：支持从Windows Server到Linux发行版共25种系统镜像

---

## 自动化重装操作流程
### 脚本下载与执行
bash
wget --no-check-certificate -O AutoReinstall.sh https://d.02es.com/AutoReinstall.sh && chmod a+x AutoReinstall.sh && bash AutoReinstall.sh

### 关键安装步骤说明
1. **IP配置确认**：输入`Y`启用自动IP获取，输入`N`进入手动配置模式
2. **镜像选择**：提供25种预设系统镜像，输入`99`可加载自定义镜像
3. **甲骨文专用**：选择23-25号镜像可实现UEFI模式安装

---

## 系统镜像密码对照表
| 序号 | 系统版本                      | 默认密码               |
|------|-------------------------------|------------------------|
| 1    | CentOS 7.7                   | Pwd@CentOS            |
| 5    | Debian 11                    | Minijer.com           |
| 12   | Windows Server 2019          | cxthhhhh.com          |
| 23   | Windows 7 Ent Lite(UEFI)     | nat.ee                |
| 25   | Windows Server 2012 Lite(UEFI)| nat.ee               |

---

## 自定义镜像部署方案
bash
wget --no-check-certificate -qO InstallNET.sh 'https://d.02es.com/InstallNET.sh' && bash InstallNET.sh -dd '[DD包直链地址]'

---

## 常见问题处理指南
1. **子网掩码异常**：谷歌云DD后若掩码显示255.255.255.255，需手动修改为255.255.255.0
2. **甲骨文安装建议**：推荐使用Ubuntu作为基础系统，CentOS可能出现兼容性问题
3. **网络诊断技巧**：Windows系统启用Ping功能：<kbd>Win+R</kbd>输入`control.exe /name Microsoft.NetworkAndSharingCenter`