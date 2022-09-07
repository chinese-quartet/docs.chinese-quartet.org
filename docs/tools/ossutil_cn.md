---
title: OSSUtil快速指南
en_url: /tools/ossutil
hide:
  - navigation
  # - toc
---


`ossutil` 一款用户友好的终端命令行工具，可用于上传数据至Quartet Data Portal系统。ossutil支持在Windows、Linux、macOS等系统中运行，您可以根据实际环境下载和安装合适的版本。 

| 工具名称    | 推荐级别 | 注意事项                | 工具类型 | 特点                           | 预期平均速度     |
| ------- | ---- | ------------------- | ---- | ---------------------------- | ---------- |
| OSSUtil | 强烈推荐 | 建议在Linux服务器和有线网络下使用 | 终端工具 | 支持大量文件并发上传、断点续传及文件目录（文件夹）的上传 | 40-100MB/s |

- 点击 [链接](https://www.alibabacloud.com/help/doc-detail/120075.htm)下载ossutil
- 点击 [链接](https://www.alibabacloud.com/help/doc-detail/50452.htm)查看更多帮助信息

如下以Linux版ossutil安装为例，说明ossutil安装与使用

#### 1. 下载ossutil

  ```
  wget http://gosspublic.alicdn.com/ossutil/1.7.6/ossutil64
  ```

#### 2. 修改文件可执行权限

  ```
  chmod 755 ossutil64
  ```

#### 3.通过交互模式生成ossutil配置文件

  a. 运行如下命令：

  ```
  ./ossutil64 config
  ```

  b. 依据提示信息指定配置文件存储路径（回车选择默认路径即可）

  c. 依据提示选择语言（回车选择默认选项即可）

  d. 依据提示配置以下参数, 包括 Endpoint, AccessKey ID, AccessKey secret, and Security Token Service (STS) token.
  
  - Endpoint填写 http://oss-cn-shanghai.aliyuncs.com
  - AccessKeyId (accessKey), AccessKeySecret (accessSecret), STS Token (stsToken) 可从QDP系统下载的 data.json 文件中获取，其通过点击"New Token"生成

  ![New Token](/assets/images/new-token.png)

  data.json文件示例如下所示:

  ```json
  {
      "uploadPath": "oss://quartet-data-portal/data/your@email.address/transcriptomics/",
      "region": "oss-cn-shanghai",
      "durationHours": 12,
      "expiration": "Thu Sep 23 2021 22:02:21 GMT+0800",
      "accessKey": "STS.NSw4TPayxZcbeXQbDfoZiHE16",
      "accessSecret": "38DvQmDt7o7jkrtGXEakjXJMXvoAhYF4cKsGJUaX9Lhz",
      "stsToken": "CAIS2wR1q6Ft5B2yfSjIr5DCf+7kjKZZ7aGJZ37ghkQzY9VFp4Ca1Dz2IHlJdXFgBOEdsf4wlWFR7/wdlrxKVpZfWUHYQcJs56xQ6x+oZ7DGv8HtHWi3dzTiSwapEBfe8JL4kI6bJYqv2J7PBnnAkihsu5uYERypQ12iN7CQlJdjda55dwKkbD1Ado80Qwx5s501OGf2P/SgOQKI523LFxhQpxZbg2Fy4rjdusqH8UjygVn31uIyrYb8KYTecKsKBppkVMqv1+Fbb7fI1DUqiyJH76BrlqdJiwSlj9iWGAtW+A7UcbiWoMRyJRVla7R/F6dYpb3kkudks+iUm43rwlFcIOxMUi3ZS5unxsTsFv6lP9B/eLrmfX/LleqpH67pvhg4Jm4BPQVRcMAgMmN3DB0nUXaYWA/Omj3jZgOkVNLEssUf2oZ0yFPF5MeDI0P1LZySzScfPO1FDSQvLAVE+W36bogMcQFHb0gdUtTzd4hoaw1Eoq7FpBDbUjYarktapPrjffjbyOl9Hoz0RcBBypFPJsYE4XI3Rk7rRq7rhk4IfSl9RqxK2a2XBP3d06OfweOcRe/FB4plvU5BIwjLoiSMWQEDT3z978EqLkuF9t3QxarD6JRmHyMg+9xWC0eIfcsrpFoh2Y2b2Aie6/OkTmqj+HEz4NjA445K6EB/ObWG+7bK52CF4CbIPvlowJaPBTVVLE7pKyAj8pe7nWkaoh0NqWawNisE5k6ZvWTKJ5RGg6TbmyIfXf0MyLWBEm3/5Bh5FNuT/7sXVep+dfhJSOq12RtuwvD3PaENd1wiPn4agAEagz7gU9EpH9fkAUugKbeH9H8ph22NrWAu8WUQF5PPi9CnqP1itUkdDtaTTprv4E5zD3RyWiYH9yA5jn9pYjwvj1tSBXjOCrIo/MLx0DGVSTZ6yExb+SYPNKzaWQ1rloPtKqGWOcXNCOgvYiy8U21Hw8UVzO7EErVAuPvlDNdqWg==",
      "authorizedCode": "eyJpZCI6IlNUUy5OU3c0VFBheXhaY2JlWFFiRGZvWmlIRTE2Iiwic2VjcmV0IjoiMzhEdlFtRHQ3bzdqa3J0R1hFYWtqWEpNWHZvQWhZRjRjS3NHSlVhWDlMaHoiLCJzdG9rZW4iOiJDQUlTMndSMXE2RnQ1QjJ5ZlNqSXI1RENmKzdraktaWjdhR0paMzdnaGtRelk5VkZwNENhMUR6MklIbEpkWEZnQk9FZHNmNHdsV0ZSN1wvd2RscnhLVnBaZldVSFlRY0pzNTZ4UTZ4K29aN0RHdjhIdEhXaTNkelRpU3dhcEVCZmU4Skw0a0k2YkpZcXYySjdQQm5uQWtpaHN1NXVZRVJ5cFExMmlON0NRbEpkamRhNTVkd0trYkQxQWRvODBRd3g1czUwMU9HZjJQXC9TZ09RS0k1MjNMRnhoUXB4WmJnMkZ5NHJqZHVzcUg4VWp5Z1ZuMzF1SXlyWWI4S1lUZWNLc0tCcHBrVk1xdjErRmJiN2ZJMURVcWl5Skg3NkJybHFkSml3U2xqOWlXR0F0VytBN1VjYmlXb01SeUpSVmxhN1JcL0Y2ZFlwYjNra3Vka3MraVVtNDNyd2xGY0lPeE1VaTNaUzV1bnhzVHNGdjZsUDlCXC9lTHJtZlhcL0xsZXFwSDY3cHZoZzRKbTRCUFFWUmNNQWdNbU4zREIwblVYYVlXQVwvT21qM2paZ09rVk5MRXNzVWYyb1oweUZQRjVNZURJMFAxTFp5U3pTY2ZQTzFGRFNRdkxBVkUrVzM2Ym9nTWNRRkhiMGdkVXRUemQ0aG9hdzFFb3E3RnBCRGJVallhcmt0YXBQcmpmZmpieU9sOUhvejBSY0JCeXBGUEpzWUU0WEkzUms3clJxN3JoazRJZlNsOVJxeEsyYTJYQlAzZDA2T2Z3ZU9jUmVcL0ZCNHBsdlU1Qkl3akxvaVNNV1FFRFQzejk3OEVxTGt1Rjl0M1F4YXJENkpSbUh5TWcrOXhXQzBlSWZjc3JwRm9oMlkyYjJBaWU2XC9Pa1RtcWorSEV6NE5qQTQ0NUs2RUJcL09iV0crN2JLNTJDRjRDYklQdmxvd0phUEJUVlZMRTdwS3lBajhwZTduV2thb2gwTnFXYXdOaXNFNWs2WnZXVEtKNVJHZzZUYm15SWZYZjBNeUxXQkVtM1wvNUJoNUZOdVRcLzdzWFZlcCtkZmhKU09xMTJSdHV3dkQzUGFFTmQxd2lQbjRhZ0FFYWd6N2dVOUVwSDlma0FVdWdLYmVIOUg4cGgyMk5yV0F1OFdVUUY1UFBpOUNucVAxaXRVa2REdGFUVHBydjRFNXpEM1J5V2lZSDl5QTVqbjlwWWp3dmoxdFNCWGpPQ3JJb1wvTUx4MERHVlNUWjZ5RXhiK1NZUE5LemFXUTFybG9QdEtxR1dPY1hOQ09ndllpeThVMjFIdzhVVnpPN0VFclZBdVB2bEROZHFXZz09IiwicHJpdmlsZWdlIjoiUmVhZC1Xcml0ZSIsImV4cGlyYXRpb24iOiIyMDIxLTA5LTIzVDE0OjAyOjIxWiIsIm9zc3BhdGgiOiJvc3M6XC9cL3F1YXJ0ZXQtZGF0YS1wb3J0YWxcL2RhdGFcL3l1ZXFpYW5nc29uZ0BmdWRhbi5lZHUuY25cL1JOQV90ZXN0XC90cmFuc2NyaXB0b21pY3NcLyIsInJlZ2lvbiI6Im9zcy1jbi1zaGFuZ2hhaSIsImR1cmF0aW9uX3NlY29uZHMiOjQzMjAwfQ=="
  }
  ```

  参数示例如下:

  - 请输入endpoint: `http://oss-cn-shanghai.aliyuncs.com`

  - 请输入accessKeyID: `{accessKey}, 例如：STS.NSw4TPayxZcbeXQbDfoZiHE16`

  - 请输入accessKeySecret: `{accessSecret}, 例如：38DvQmDt7o7jkrtGXEakjXJMXvoAhYF4cKsGJUaX9Lhz`

  - 请输入stsToken: `{stsToken}, 例如：CAIS2wR1q6Ft5B2yfSjIr5DCf....`

#### 4. 上传文件
  
  运行ossutil的cp命令即可将本地的文件或者目录上传至QDP系统存储系统

  - 点击[链接](https://www.alibabacloud.com/help/object-storage-service/latest/cp-upload-objects)查看`cp命令`更多帮助信息

  - 在确认上传完所有文件后，请回到QDP网站，点击`Check按钮`确认您的数据

  - Token有效期为12小时。但请勿担心，一旦文件开始上传则整个过程不会受Token过期的影响，除非您主动结束掉或者ossutil意外退出。此外，若Token过期，您可以回到QDP网站再次针对相同路径生成Token，再次上传相应文件。因ossutil支持断点续传，因此将减轻Token过期对您数据上传效率的影响

  - 若您期望上传整个目录下的文件，请指定`-r`参数

  - 建议您尽可能将一次分析所需的文件放到不同的子目录下，这将有助于您后续挑选预期文件完成分析
  
  - 若您上传文件的速度小于预期，请确认您使用的是有线网络，且为千兆网卡。此外，您可以调整`--parallel`与`--part-size`参数来优化
  
  ```
  ./ossutil64 cp -r your_directory oss://quartet-data-portal/data/your@email.address/transcriptomics/
  ```
