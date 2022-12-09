# hackintosh-HP-Pavilion-Power-15-cb074tx
黑苹果 ventura 惠普光影精灵 III 代 HP 畅游人 Power 15-cb074TX 笔记本  

## 描述
`EFI` 是调好的 opencore 0.8.8 引导，三码已清，自行更换，清理nvram  
`opencore debug 流程` 是针对个人机器 惠普光影精灵 III 代 HP 畅游人 Power 15-cb074TX 笔记本 做的记录和调试，方便自己以后做参考，其它主板型号和CPU请酌情参考  

## 目录结构

    .                                  
    ├── EFI                            # 配置好已经清除三码的 EFI 引导文件 
    └── opencore debug 流程             # opencore配置制作流程说明 
        ├── 01Finding your hardware    # 第一步找到你的硬件参数说明
        ├── 02DVMT cfg unlock          # 第二步根据第一步找到的主板型号，解锁 CFGLOCK 和配置最大 DVMT 说明
        ├── 03USB Creation             # 第三步下载 opencore 文件说明
        ├── 04Gathering files          # 第四步根据第一步获取的硬件参数配置 kexts 和 ACPI 文件说明 
        ├── 05config.plist Setup       # 第五步根据官网教程进行常规配置说明
        └── 06debug                    # 第六步根据报错现象做调试说明

## 官方机型参数
<a href="https://support.hp.com/cn-zh/product/hp-pavilion-power-15-cb000-laptop-pc/15551388/model/17033411/document/c05549489" title="官方参数">https://support.hp.com/cn-zh/product/hp-pavilion-power-15-cb000-laptop-pc/15551388/model/17033411/document/c05549489</a>  

## 注意
1.本机SSD更换为 傲腾SSD 支持安装 Ventura 可以按照流程制作 nvme.aml 补丁，其实就在 EFI -> OC -> ACPI 里  

2.我现在用的免驱博通网卡，不需要驱动  
如果你是intel网卡，那在 ventura 的配置应该是这样的  
<img width="964" alt="image" title="intel" src="https://user-images.githubusercontent.com/94947393/205294387-150b0bc5-4517-43a8-9082-b0403ec64484.png">   
你如果已经将intel网卡替换成了 博通网卡 然而买错了不能免驱的话，网卡配置是这样的：  
<img width="964" alt="image" title="Broadcom" src="https://user-images.githubusercontent.com/94947393/201841163-97df13ad-4a79-4dab-af6b-25089f28a4b2.png">     

3.本机cfglock已经通过  `opencore debug 流程` -> `02DVMT cfg unlock` 步骤解锁了，并未勾选 oc 配置 `Kernel` -> `Quirks` -> `AppleXcpmCfgLock`  

4.若你的机器没有解锁cfglocal你需要勾选 oc 配置 `Kernel` -> `Quirks` -> `AppleXcpmCfgLock`  

5.本机独显 rx460 能识别但是毫无用处，没办法只能通过ssdt屏蔽了  

## 我得到了什么？
我大概了解到7代CPU的配置基本相同甚至主板也相似，解锁方案也是一样的，ACPI都是一样的，只是驱动稍有不同，只能说太神奇了，有点上道的感觉  

## 声明
对于 `opencore debug 流程` 请斟酌参考，若参考某流程导致机毁人亡，本人不敢也没能力承担责任，实在抱歉
