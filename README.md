# DBPTIT REST + gRPC Setup (Python + PyCharm)

## 1. Cài phần mềm

Cài:

- Python
- PyCharm Community

Khi cài Python nhớ tick:

```text
Add Python to PATH
```

Kiểm tra:

```bash
python --version
pip --version
```

---

# 2. Tạo project PyCharm

```text
New Project
→ chọn Virtualenv
→ Create
```

---

# 3. Cài thư viện

Mở Terminal trong PyCharm:

```bash
pip install requests grpcio grpcio-tools
```

Nếu lỗi:

```bash
python -m pip install requests grpcio grpcio-tools
```

---

# 4. Cấu trúc project

```text
project/
│
├── rest_client.py
├── grpc_client.py
├── judge.proto
├── judge_pb2.py
└── judge_pb2_grpc.py
```

---

# 5. REST setup

REST chỉ cần:

```python
import requests
```

REST dùng:

```text
Port 2230
```

Không cần `judge.proto`.

---

# 6. gRPC setup

gRPC dùng:

```text
Port 2240
```

Cần:

```python
import grpc
import judge_pb2
import judge_pb2_grpc
```

---

# 7. Tạo file judge.proto

Tạo file:

```text
judge.proto
```

Nội dung:

```proto
syntax = "proto3";

package GRPC;

service JudgeService {
  rpc Request (JudgeRequest) returns (JudgeResponse);
  rpc Submit (SubmitRequest) returns (SubmitResponse);
}

message JudgeRequest {
  string student_code = 1;
  string question_alias = 2;
}

message JudgeResponse {
  string request_id = 1;
  string data = 2;
}

message SubmitRequest {
  string student_code = 1;
  string question_alias = 2;
  string request_id = 3;
  string answer = 4;
}

message SubmitResponse {
  string status = 1;
  string message = 2;
}
```

---

# 8. Generate file gRPC

Mở Terminal trong PyCharm:

```bash
python -m grpc_tools.protoc -I. --python_out=. --grpc_python_out=. judge.proto
```

Sau đó sẽ có:

```text
judge_pb2.py
judge_pb2_grpc.py
```

---

# 9. Chạy file Python

REST:

```bash
python rest_client.py
```

gRPC:

```bash
python grpc_client.py
```

---

# 10. Checklist trước khi thi

```text
✔ Python
✔ PyCharm
✔ requests
✔ grpcio
✔ grpcio-tools
✔ judge.proto
✔ generate judge_pb2.py
✔ generate judge_pb2_grpc.py
```

---

# 11. Ghi nhớ nhanh

```text
REST
→ requests
→ port 2230

gRPC
→ grpc
→ judge.proto
→ generate pb2
→ port 2240
```
