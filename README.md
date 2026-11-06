# ISO 20022 Messages (XSD)

从 ISO 20022 官网逐项下载的全部报文定义 XSD 文件集合，已解压并按报文前缀分类，只保留 xsd。

- 数据来源 1（现行报文定义）：https://www.iso20022.org/iso-20022-message-definitions
- 数据来源 2（报文归档）：https://www.iso20022.org/catalogue-messages/iso-20022-messages-archive

## 目录结构

```
├── Message Definitions/   # 现行（当前生效）的报文定义：807 个 xsd，32 个前缀目录
├── Archive/               # 历史归档：2707 个 xsd，31 个前缀目录
└── README.md
```

两个目录都按报文前缀（即 ISO 20022 的业务域）分类，目录名就是报文类型前缀，例如
`Message Definitions/pacs/pacs.008.001.08.xsd`、`Archive/camt/camt.053.001.03.xsd`。

## 前缀（业务域）说明

| 前缀 | 业务域 | 现行/归档 |
|---|---|---|
| pacs | Payments Clearing and Settlement，支付清算与结算 | 10 / 90 |
| pain | Payments Initiation，支付发起 | 12 / 107 |
| camt | Cash Management，现金管理 | 105 / 351 |
| acmt | Bank Account Management，银行账户管理 | 36 / 145 |
| auth | Financial Instrument Reporting（数据报告） | 90 / 118 |
| seev | Securities Events，证券事件 | 73 / 391 |
| sese | Securities Settlement，证券结算 | 61 / 368 |
| semt | Securities Management，证券管理 | 48 / 160 |
| setr | Securities Trade，证券交易 | 29 / 86 |
| reda | Reference Data，参考数据 | 67 / 248 |
| tsmt / tsin / tsrv | Trade Services，贸易服务 | — |
| caaa / caad / caam / casp / cain / ... | Card 系列卡交易报文 | — |
| colr | Collateral Management，抵押管理 | 22 / 44 |
| catp / catm | ATM 相关报文 | 17 / 61 |
| fxtr | Foreign Exchange Trade，外汇交易 | 15 / 32 |
| head | Business Application Header，业务应用头 | 3 / 8 |
| admi | Administration，系统管理 | 10 / 23 |

完整目录清单直接看仓库根目录下的两个文件夹即可。

## 文件命名规则

```
<pacs|pain|camt|...>.<三个数字>.<报文编号>.<主版本>.<次版本>.xsd
例如：pacs.008.001.08.xsd
```

版本号直接体现在文件名里，同一报文的不同版本（如 camt.053.001.01 ~ camt.053.001.08）在同一目录下并列存放，可追溯任意历史版本的结构。

- **Message Definitions/**：官网当前发布的最新定义，一个业务域内的全部报文。
- **Archive/**：历次发布的历史版本合集（已去重，重复打包的相同文件只保留一份）。

## 用途

- 支付清算系统、报文网关的 ISO 20022 报文 schema 校验（`xmllint --schema` 等）
- 依据 XSD 派生 JSON Schema / Java DTO / 数据库模型
- 查询某个报文号（如 pacs.008）历史版本的结构差异，配合 XSD 对比工具做多版本比对

## 注意

- 版权与最终解释权归 ISO 20022 Registration Authority（https://www.iso20022.org）所有，本仓库仅作学习与开发参考的镜像整理。
- 现行标准请以官网为准，本仓库为静态快照。原始 zip 备份在本地 `ZIP/` 目录，未上传。
