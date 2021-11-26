#LoadBalance:
###**Active Health Checks**
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/pdcvxtan19_Selection_001.png)

![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/7yadz8dvpv_Selection_006.png)
**Weight 2** : Là trọng số, trọng số cao hơn thì chỉ định server đấy xử lý nhiều hơn.

![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/zlt3y70jqu_1.png)

Trong HA kiểm tra tình trạng thụ động với tham số observe : **observe layer4** : observe ở layer4/tcp
**error-limt 10**: 10 kết nối lỗi thì sẽ gọi on-error và đánh dấu máy chủ fails.

**option redispatch** :  Nếu client gặp lỗi kết nối sẽ ngay lập tức được chuyển đến server acctive.
**retries**: Số lần thử lại.
**timeout connect**: time giữa các lần thử lại.

###**Gauging Health with an External Agent**
![alt text](https://s3-ap-southeast-1.amazonaws.com/kipalog.com/f4iod83u7x_3.png)

*Với HAProxy, bạn có thể truy vấn tác nhân bên ngoài , là một phần mềm chạy trên máy chủ tách biệt với ứng dụng bạn đang cân bằng tải. Vì tác nhân có toàn quyền truy cập vào máy chủ từ xa, nó có khả năng kiểm tra các chỉ số quan trọng của nó chặt chẽ hơn.*

agent-check: Báo HAProxy để kết nối với một tác nhân bên ngoài.
**agent-addr** và **agent-port**: Thiết lập IP và cổng của tác nhân.
**agent-inter**: Khoảng thời gian giữa các lần kiểm tra.
----------------------------------------------------- REGEX HA -----------------------------------------------------------------
Reggex: /^(\/[^\/]+){0,2}\/?$/gm
DEMO

It works like this:

^ searches for the beginning of a line
(\/[^\/]+) searches for a path element
( starts a group
\/ searches for a slash
[^\/]+ searches for some non-slash characters
{0,2} says, that 0 to 2 of those path elements should be found
\/? allows trailling slashes
$ searches for the end of the line
Use these modifiers:

g to search for several matches within the input
m to treat every line as a separate input

linkref: https://stackoverflow.com/questions/53033626/regex-for-partial-path
