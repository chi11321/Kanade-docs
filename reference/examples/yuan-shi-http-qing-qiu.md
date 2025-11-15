# 原始HTTP请求

```lua
network.socket("192.168.31.1:80"):and_then(function(socket)
    socket:write_all([[
GET / HTTP/1.1
Host: 192.168.31.1
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/117.0.5938.132 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9
Connection: close


    ]]):await()
    print(socket:read_to_string():await())
end)

network.tls_socket("www.baidu.com:443"):and_then(function(socket)
    socket:write_all([[
GET / HTTP/1.1
Host: www.baidu.com
Cookie: PSTM=1762169402; BAIDUID=CF70524A3B67D7BC4876FE4CFF484FC4:FG=1; BD_UPN=123253; BIDUPSID=A09EB6C645BD6C14F1327E2E8F1EF414; BAIDUID_BFESS=CF70524A3B67D7BC4876FE4CFF484FC4:FG=1; ZFY=K7M5RNxXAU7uTp6cwwoY21LgdlDG3T3QdgHpQDbPUbo:C; BDORZ=B490B5EBF6F3CD402E515D22BCDA1598; BA_HECTOR=aga10k012ga18ga08g0l0g2gah80011kh6e3m25; channel=baidusearch; baikeVisitId=04595605-cf76-4c84-b9e2-30528876e0b7; __bid_n=19318a3a7ca9824c744560; H_PS_PSSID=63142_65606_65753_65759_65800_65917_65361_65927_65989_66083_66098_66117_65866_66207_66225_66236_66309_66354_66321_66340_66377_66282_66272_66390_66393; BD_HOME=1; delPer=0; BD_CK_SAM=1; PSINO=6; H_WISE_SIDS=63142_65606_65753_65759_65800_65917_65361_65927_65989_66083_66098_66117_65866_66207_66225_66236_66309_66354_66321_66340_66377_66282_66272_66390_66393; COOKIE_SESSION=71829_0_6_6_14_8_1_2_6_5_1_1_520611_0_0_0_1762867327_0_1762939146%7C9%230_0_1762939146%7C1; ab_sr=1.0.1_OTliY2ZkMTYzOGY1ZGJkYTgyMWUzYTZhYWU3OTg2ZjliZTBiNDEyNTRhOTc3YTZkYTU2NjExNWZhYjg5NzE3ZmRkZTU2NGI0N2Q1YmUzYTVhNmU4ZmM2NmYwZDNmMzM5ZDNjMWVlZGI4ZWM2YThkNWE2YzM5MGRhZmQxZGI3ZDJlZGFiYWY4Nzg0M2I1ZmVkYTk0MWE5YmQ3NWE2YmM0Mw==; RT="z=1&dm=baidu.com&si=8be0561f-7d7d-463a-b64c-14ef3c632307&ss=mhvsxrlw&sl=0&tt=0&bcn=https%3A%2F%2Ffclog.baidu.com%2Flog%2Fweirwood%3Ftype%3Dperf&ld=3lo&ul=1x6jk&hd=1x6mb"
Cache-Control: max-age=0
Sec-Ch-Ua: "Chromium";v="142", "Google Chrome";v="142", "Not_A Brand";v="99"
Sec-Ch-Ua-Mobile: ?0
Sec-Ch-Ua-Platform: "macOS"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/142.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Language: zh-CN,zh;q=0.9
Priority: u=0, i
Connection: close


    ]]):await()
    print(socket:read_to_string():await())
end)
```

