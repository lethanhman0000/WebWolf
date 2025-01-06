1. General
  1.1. Http basics
  Concept  Ý tưởng
This lesson presents the basics for understanding the transfer of data between the browser and the web application and how to trap a request/response with a HTTP proxy.
Bài học này trình bày những kiến ​​thức cơ bản để hiểu việc truyền dữ liệu giữa trình duyệt và ứng dụng web cũng như cách chặn yêu cầu/phản hồi bằng proxy HTTP.

  Goals  Bàn thắng
The user should become familiar with the features of WebGoat by manipulating the above buttons to view hints, show the HTTP request parameters, the HTTP request cookies, and the Java source code. You may also try using OWASP Zed Attack Proxy for the first time.
Người dùng nên làm quen với các tính năng của WebGoat bằng các thao tác trên các nút để xem gợi ý, hiển thị tham số yêu cầu HTTP, cookie yêu cầu HTTP và mã nguồn Java. Bạn cũng có thể thử sử dụng Proxy tấn công OWASP Zed lần đầu tiên.

  How HTTP works:  Cách HTTP hoạt động:
All HTTP transactions follow the same general format. Each client request and server response has three parts: the request or response line, a header section and the entity body.
Tất cả các giao dịch HTTP đều tuân theo cùng một định dạng chung. Mỗi yêu cầu của máy khách và phản hồi của máy chủ có ba phần: dòng yêu cầu hoặc phản hồi, phần tiêu đề và nội dung thực thể.

The client initiates a transaction as follows:
Khách hàng thực hiện giao dịch như sau:

The client contacts the server and sends a document request. A GET request can have url parameters and those parameters will be available in the web access logs.
Máy khách liên hệ với máy chủ và gửi yêu cầu tài liệu. Yêu cầu GET có thể có các tham số url và các tham số đó sẽ có sẵn trong nhật ký truy cập web.

GET /index.html?param=value HTTP/1.0
NHẬN /index.html?param=giá trị HTTP/1.0

Next, the client sends optional header information to inform the server of its configuration and the document formats it will accept.
Tiếp theo, máy khách gửi thông tin tiêu đề tùy chọn để thông báo cho máy chủ về cấu hình của nó và các định dạng tài liệu mà nó sẽ chấp nhận.

User-Agent: Mozilla/4.06 Accept: image/gif,image/jpeg, /
Tác nhân người dùng: Mozilla/4.06 Chấp nhận: image/gif,image/jpeg, /

In a POST request, the user supplied data will follow the optional headers and is not part of the contained within the POST URL.
Trong yêu cầu POST, dữ liệu do người dùng cung cấp sẽ tuân theo các tiêu đề tùy chọn và không phải là một phần của nội dung có trong URL POST.
