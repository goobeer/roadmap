# roadmap
[osit.top](https://www.osit.top)域使用自签名证书，消除浏览器"您的连接不是私密连接"警告。
<img src="/asserts/tlswarning.png" style="width:60%" title="自签名证书客户端安全警告" />

## 亲们，看到浏览器上述提示"您的连接不是私密连接"的提示信息不要慌，出现这种情况有以下原因：
1. 使用自签名证书
2. 服务证书过期了
3. 证书被恶意篡改
4. 其他原因

对于osit.top域下所有的子域，使用的是自签名证书目的是保护CS数据安全。该自签名根证书密钥使用的是4096位，自签名证书完全安全，大家不必因为浏览器这个安全检查提示而恐慌。解决上述"您的连接不是私密连接"警告，只需要手动导入自签名根证书到"受信任的根证书颁发机构"中即可消除上述警告。

下载自签名根证书：[osit.top自签名根证书](/asserts/osit.top.ca.cer)

## 手动导入自签名证书方式：
### windows系统导入自签名根证书步骤：
1. 双击所下载的根证书[osit.top自签名根证书](/asserts/osit.top.ca.cer)
   <img src="/asserts/win_cer_import.png" style="width:60%" title="windows安装自签名根证书" />
2. 点击安装证书，存储位置选择"本地计算机"
   <img src="/asserts/win_cer_import_s1.png" style="width:60%" title="windows安装自签名根证书" />
3. 将所选择的证书"osit.top.ca.cer"放到"受信任的根证书颁发机构"
   <img src="/asserts/win_cer_import_s2.png" style="width:60%" title="windows安装自签名根证书" />
4. 单击"完成"按钮，至此再次刷新对应的界面，就不会再次出现"您的连接不是私密连接"警告。
   <img src="/asserts/win_cer_import_s3.png" style="width:60%" title="windows安装自签名根证书" />
   <img src="/asserts/win_cer_import_s4.png" style="width:60%" title="windows安装自签名根证书" />

### Android系统导入自签名根证书步骤：
1. 下载[osit.top自签名根证书](/asserts/osit.top.ca.cer)到手机存储中
2. 逐步按照如下图片操作导入osit.top.ca.cer证书到"凭据存储中"
   <img src="/asserts/and_s1.png" style="width:60%"  title="android安装自签名根证书步骤1" />
   <img src="/asserts/and_s2.png" style="width:60%"  title="android安装自签名根证书步骤1" />
   <img src="/asserts/and_s3.png" style="width:60%"  title="android安装自签名根证书步骤1" />
### linux安装自签名证书:
#### archlinux安装自签名证书:
1. 复制osit.ca.crt自签名证书到/etc/ca-certificates/trust-source/anchors目录下，并信任自签名证书
`# cp osit.ca.crt /etc/ca-certificates/trust-source/anchors/ && update-ca-trust`
`# trust list|grep osit`	//检查信任的自签名证书
#### debian安装自签名证书:
1. 复制osit.ca.crt自签名证书到/usr/local/share/ca-certificates/目录下，并信任自签名证书
   `# cp osit.ca.crt /usr/local/share/ca-certificates/ && update-ca-certificates`