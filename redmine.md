# Redmine
## Description
- Redmine là một ứng dụng quản lý project linh hoạt, có thể theo dõi trạng thái của Task.
- Với từng role khác nhau, flow khác nhau
#### Role

#### Tracker
1. User story
2. Task
3. Bug
4. CR/Request
5. Requirement
6. QA
#### Flow
- Life circle của 1 issue

| Status|Ý nghĩa |Whose? | Next action|
|---|---|---|---|
|New|Issue chưa được clear. Nếu là tracker là Bug, thì Dev chưa tái hiện được. Nếu là tracker là User Story, Task, CR thì Dev chưa hiểu được database, liên quan bảng nào, impact đến phần nào khác không. Nếu tracker là QA, thì Comtor chưa hiểu được CR này trên màn nào, thiết bị nào và chưa hỏi khách hàng/client|PM, BA, Dev, QC, Comtor|Dev: Cần đọc requiremnt và ERD, hoặc tái hiện được bug, tìm được root cause, check impact. Xong thì chuyển sang cột TODO. Comtor: Cần đọc hiểu issue và hỏi khách hàng.|
|TODO |Issue đã được clear, issue ở trạng thái này là Dev có thể làm được và có thể không gặp suprise gì. Tuỳ theo priority mà chuyển sang cột In progress.| Dev | |
|In progress | Dev: Thể hiện số issue trong ngày dev sẽ fix, hoặc hiện tại đang fix. Có thể kết hợp với due date. Comtor: Thể hiện rằng QA này đã hỏi khách, và chờ khách trả lời|Dev, Comtor|Dev: cần fix và tạo MR để chuyển sang cột Waiting deploy for internal|
|Waitting for deploy internal|Dev: đã tạo MR. MR đang chờ được review, merge và deploy. PM: merge và deploy trên server test.|PM, Dev|PM review, merge và deploy. Sau đó chuyển issue sang cột Deploy internal|
|Deploy Internal|Issue này đã được phản ánh trên server test. Dev đã check trên server test trước khi inform QC(Để hạn chế tình trạng MR rác)|QC|QC chuyển issue này sang cột testing và test|
|UT Inspected|Thường không dùng, nếu dùng thì có ý nghĩa Dev đã check trên server test|QC|QC chuyển issue này sang cột testing và test|
|Waiting for deploy customer|QC đã test và verify defect này được fix, cột này và cột Deploy customer chỉ dùng trong trường hợp defect, hoặc bug, request khách hàng log|PM, Comtor|PM tạo PR nếu cần, và inform Comtor thông báo khách hàng|
|Deploy Customer|Khách hàng đã merge PR|Comtor|Done|
|Close|issue này đã được fix. Cột này chỉ dùng trong trường hợp issue internal||Done|
