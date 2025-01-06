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

===========================================================
2.HTTP Proxies
What’s an HTTP Proxy  Proxy HTTP là gì
  A proxy is some forwarder application that connects your HTTP client to backend resources. HTTP clients can be browsers or applications like curl, SOAP UI, Postman, etc. Usually, these proxies are used for routing and getting internet access when there is no direct connection to the internet from the client itself. HTTP proxies are therefore also ideal when you are testing your application. You can always use the proxy log records to see what was actually sent from client to server. So you can check the request and response headers and the XML, JSON, or other payloads.
  Proxy là một số ứng dụng chuyển tiếp kết nối máy khách HTTP của bạn với các tài nguyên phụ trợ. Máy khách HTTP có thể là trình duyệt hoặc ứng dụng như Curl, SOAP UI, Postman, v.v. Thông thường, các proxy này được sử dụng để định tuyến và truy cập Internet khi không có kết nối trực tiếp với Internet từ chính máy khách. Do đó, proxy HTTP cũng lý tưởng khi bạn đang thử nghiệm ứng dụng của mình. Bạn luôn có thể sử dụng bản ghi nhật ký proxy để xem những gì thực sự được gửi từ máy khách đến máy chủ. Vì vậy, bạn có thể kiểm tra các tiêu đề yêu cầu và phản hồi cũng như XML, JSON hoặc các tải trọng khác.

  HTTP Proxies receive requests from a client and relay them. They also typically record them. They act as a man-in-the-middle. It even works fine with or without HTTPS as long as your client or browser trusts the certificate of the HTTP Proxy.
  Proxy HTTP nhận yêu cầu từ khách hàng và chuyển tiếp chúng. Họ cũng thường ghi lại chúng. Họ đóng vai trò là người trung gian. Nó thậm chí còn hoạt động tốt khi có hoặc không có HTTPS miễn là ứng dụng khách hoặc trình duyệt của bạn tin cậy vào chứng chỉ của HTTP Proxy.

 

  ZAP Proxy Capabilities  Khả năng proxy ZAP
With ZAP, you can record traffic, inspect traffic, modify requests and responses from and to your browser, and get reports on a range of known vulnerabilities that ZAP detects through the inspection of the traffic. The passive and active reporting on security issues is usually used in Continuous Delivery pipelines that use a GUI-less ZAP. Here we will use ZAP interactively and mainly to see and modify requests to find vulnerabilities and solve assignments. ZAP has a graphical user interface but now also has a HUD Heads-On-Display, which uses a web socket connection between the browser, and the ZAP proxy.
  Với ZAP, bạn có thể ghi lại lưu lượng truy cập, kiểm tra lưu lượng truy cập, sửa đổi các yêu cầu và phản hồi từ và tới trình duyệt của mình, đồng thời nhận báo cáo về một loạt lỗ hổng đã biết mà ZAP phát hiện thông qua việc kiểm tra lưu lượng truy cập. Báo cáo thụ động và chủ động về các vấn đề bảo mật thường được sử dụng trong quy trình Phân phối liên tục sử dụng ZAP không có GUI. Ở đây, chúng tôi sẽ sử dụng ZAP một cách tương tác và chủ yếu để xem và sửa đổi các yêu cầu tìm lỗ hổng và giải quyết các bài tập. ZAP có giao diện người dùng đồ họa nhưng hiện cũng có HUD Heads-On-Display, sử dụng kết nối ổ cắm web giữa trình duyệt và proxy ZAP.

 

  Next pages
  You can go through all lesson pages or click on these links to skip some pages.
Bạn có thể xem qua tất cả các trang bài học hoặc nhấp vào các liên kết này để bỏ qua một số trang.

  Configuring OWASP ZAP and browser
Định cấu hình OWASP ZAP và trình duyệt

  Filtering requests with ZAP
Lọc yêu cầu bằng ZAP

  A proxy assignment with ZAP
Việc gán proxy với ZAP

  Replaying requests with ZAP
Phát lại các yêu cầu bằng ZAP

  Replaying requests with Burp
Phát lại các yêu cầu với Burp
=========================================================
3.Developer Tools  Công cụ dành cho nhà phát triển
  Google Chrome Developer Tools
Công cụ dành cho nhà phát triển Google Chrome
  To complete certain assignments, you sometimes may have to look at the JavaScript source code or run a JavaScript command on your own. To do that, Google Chrome has a set of tools that allow you to do that and much more. While these tools are not specific to Google Chrome, almost every modern browser has a bunch of its own. Our introduction will focus on the ones found in Google Chrome. You can, however still use the browser of your choice, like Firefox or Safari, although some steps of this tutorial maybe different for you.
  Để hoàn thành một số nhiệm vụ nhất định, đôi khi bạn có thể phải xem mã nguồn JavaScript hoặc tự mình chạy lệnh JavaScript. Để làm được điều đó, Google Chrome có một bộ công cụ cho phép bạn làm điều đó và hơn thế nữa. Mặc dù những công cụ này không dành riêng cho Google Chrome nhưng hầu hết mọi trình duyệt hiện đại đều có một loạt công cụ riêng. Phần giới thiệu của chúng tôi sẽ tập trung vào những thứ được tìm thấy trong Google Chrome. Tuy nhiên, bạn vẫn có thể sử dụng trình duyệt bạn chọn, như Firefox hoặc Safari, mặc dù một số bước trong hướng dẫn này có thể khác đối với bạn.

  Keep in mind that the following tutorial is not there to teach everything about these tools. This tutorial will only focus on the essential knowledge to complete specific assignments. Also, if you are already familiar with these tools, you can safely skip these lessons.
  Hãy nhớ rằng hướng dẫn sau đây không hướng dẫn mọi thứ về những công cụ này. Hướng dẫn này sẽ chỉ tập trung vào những kiến ​​thức cần thiết để hoàn thành các bài tập cụ thể. Ngoài ra, nếu bạn đã quen với những công cụ này, bạn có thể yên tâm bỏ qua những bài học này.

  To get started: open the developer tools. There are multiple ways to open them:
Để bắt đầu: hãy mở công cụ dành cho nhà phát triển . Có nhiều cách để mở chúng:

  Right-click anywhere in the browser window and select the option "Inspect".
Nhấp chuột phải vào bất kỳ đâu trong cửa sổ trình duyệt và chọn tùy chọn "Kiểm tra" .

  Go to the browser menu (three dots in the top right corner), then go to "More tools" and select the option "Developer tools".
Chuyển đến menu trình duyệt (ba dấu chấm ở góc trên bên phải), sau đó đi tới "Công cụ khác" và chọn tùy chọn "Công cụ dành cho nhà phát triển" .

  Use the keyboard shortcut Ctrl + Shift + I
Sử dụng phím tắt Ctrl + Shift + I
=========================================================
4.The CIA Triad  Bộ ba CIA
The CIA Triad (confidentiality, integrity, availability) is a model for information security. The three elements of the triad are considered the most crucial information security components and should guarantee in any secure system.
  Bộ ba CIA (bảo mật, toàn vẹn, sẵn sàng) là một mô hình về bảo mật thông tin. Ba yếu tố của bộ ba được coi là thành phần bảo mật thông tin quan trọng nhất và cần đảm bảo trong bất kỳ hệ thống bảo mật nào.
Serious consequences can result if even one of these elements is breached.
  Hậu quả nghiêm trọng có thể xảy ra nếu ngay cả một trong những yếu tố này bị vi phạm.

  The CIA Triad was created to provide a baseline standard for evaluating and implementing security regardless of the underlying system and/or organization.
  Bộ ba CIA được tạo ra để cung cấp tiêu chuẩn cơ bản để đánh giá và triển khai bảo mật bất kể hệ thống và/hoặc tổ chức cơ bản.
==========================================================
5. Writing new lesson
  This lesson describes the steps needed to add a new lesson to WebGoat. In general, there are four steps:
Bài học này mô tả các bước cần thiết để thêm bài học mới vào WebGoat. Nói chung, có bốn bước:

Write the content. In WebGoat, we use AsciiDoc as a format.
  Viết nội dung. Trong WebGoat, chúng tôi sử dụng AsciiDoc làm định dạng.

Create a lesson class  Tạo một lớp học

Write HTML glue page, so WebGoat knows how to display the content
  Viết trang keo HTML để WebGoat biết cách hiển thị nội dung

Add one or more assignments within the lesson
  Thêm một hoặc nhiều bài tập trong bài học

Let’s see how to create a new lesson.
  Hãy xem cách tạo một bài học mới.
==================================end========================================
