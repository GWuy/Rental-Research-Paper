# HƯỚNG DẪN LÀM VIỆC NHÓM – RESEARCH PAPER

**Đề tài:** *Design and Evaluation of an Event-Driven Microservices Architecture for a Rental Property Management System*
**Định dạng:** IEEE Conference, LaTeX, viết bằng tiếng Anh
**Nhóm viết:** Dương, Huy, Duy, Hoàng
**Lưu ý:** Phạm Quang Long không tham gia viết bài. **Duy** tiếp nhận toàn bộ phần nghiên cứu và viết về Gateway/Kafka/DevOps do Long phát triển.

## 1. Mục tiêu của project

Đây là **một bài research paper chung**, không phải bốn bài độc lập. Bài báo tập trung vào kiến trúc Microservices, giao tiếp hướng sự kiện, tính nhất quán dữ liệu và đánh giá hệ thống quản lý cho thuê phòng. Mỗi người viết một nhóm nội dung riêng, sau đó ghép lại tự động qua `main.tex`.

> **Quan trọng:** Nội dung hiện có trong các file `.tex` chỉ là bản nháp/khung. Các chỗ `TODO` cần được hoàn thiện. Không tự đặt số liệu benchmark, kết quả nghiên cứu hoặc nguồn trích dẫn.

## 2. Cấu trúc thư mục

```text
rental-research-paper/
├── main.tex                       # File chính ghép toàn bộ bài báo (dùng chung)
├── references.bib                 # Tài liệu tham khảo BibTeX (dùng chung)
├── README.md                      # Hướng dẫn kỹ thuật chung
├── .gitignore                     # Loại trừ file biên dịch tạm
├── sections/
│   ├── abstract.tex               # Dương
│   ├── introduction.tex           # Dương – Section I
│   ├── related_work.tex           # Dương – Section II
│   ├── system_architecture.tex    # Huy – Section III
│   ├── event_driven_design.tex    # Duy – Section IV
│   ├── evaluation.tex             # Hoàng – Section V
│   ├── discussion.tex             # Hoàng – Section VI
│   └── conclusion.tex             # Hoàng – Section VII
├── tables/
│   ├── related_work.tex           # Dương
│   ├── services.tex               # Huy
│   ├── events.tex                 # Duy
│   └── experiments.tex            # Hoàng
├── figures/
│   └── README.md                   # Hướng dẫn lưu sơ đồ/hình
└── experiments/
    └── README.md                   # Hướng dẫn lưu kịch bản/dữ liệu kiểm thử
```

**Các file dùng chung:** `main.tex`, `references.bib`, `README.md`. Không tự ý thay cấu trúc hoặc xóa lời gọi `\input{...}` của người khác.

## 3. Phân công chính thức

| Thành viên      | Chương sở hữu                              | Số từ mục tiêu | Trách nhiệm bổ sung                                                                 |
| ----------------- | ---------------------------------------------- | -----------------: | -------------------------------------------------------------------------------------- |
| **Dương** | Abstract, I. Introduction, II. Related Work    |       1.700–1.900 | Tìm, kiểm chứng và chuẩn hóa nguồn học thuật; tổng hợp abstract cuối cùng |
| **Huy**     | III. System Architecture & Security            |       1.700–1.900 | Sơ đồ kiến trúc, service decomposition, database ownership, security              |
| **Duy**     | IV. Event-Driven Design & Infrastructure       |       1.400–1.600 | Toàn bộ phần viết Gateway/Kafka/DevOps của Long; event flow, outbox, deployment   |
| **Hoàng**  | V. Evaluation, VI. Discussion, VII. Conclusion |       1.700–1.900 | Thiết kế thực nghiệm, xử lý số liệu, bảng và biểu đồ kết quả            |

Mục tiêu là **cân bằng tổng công sức** (nghiên cứu, viết, vẽ hình, chạy test, phân tích), không chỉ chia số từ bằng nhau. Duy ít từ hơn vì phải tiếp nhận phần kỹ thuật của Long; các thành viên khác hỗ trợ cung cấp log và môi trường test cho Hoàng.

### 3.1. Dương – Abstract, Introduction & Related Work

**File sửa:** `sections/abstract.tex`, `sections/introduction.tex`, `sections/related_work.tex`, `tables/related_work.tex`.

- **Abstract:** Vấn đề, mục tiêu, giải pháp, phương pháp và **kết quả thực tế** (hoàn thiện sau khi Hoàng đo xong).
- **I. Introduction:** Background and Motivation; Problem Statement; Research Objectives and Questions; Main Contributions; Paper Organization.
- **II. Related Work:** Traditional Rental Management Systems; Microservices Architecture; Event-Driven Architecture; Existing Approaches and Research Gaps.
- **Bàn giao:** Các file .tex hoàn chỉnh; Table I so sánh các nghiên cứu có thật; danh mục nguồn đã kiểm chứng (đề xuất tối thiểu 8–10 nguồn phù hợp cho toàn nhóm, không phải 8–10 nguồn tự bịa).
- **Không viết:** Cấu hình Kafka/Gateway/DevOps, chi tiết triển khai service hoặc kết quả đo.

### 3.2. Huy – System Architecture & Security

**File sửa:** `sections/system_architecture.tex`, `tables/services.tex`; thêm hình kiến trúc vào `figures/`.

- **III. System Architecture:** System Overview and Requirements; Microservices Decomposition; Database-per-Service; Authentication and Authorization; Service Interfaces and Access Boundaries.
- Trình bày 7 service nghiệp vụ, Gateway và Eureka; ranh giới dữ liệu; mô hình quyền CUSTOMER/STAFF/ADMIN.
- **Bàn giao:** Section III; bảng trách nhiệm các service; **Fig. 1 – Overall Architecture**, sơ đồ/mô tả RBAC.
- **Không viết:** Chi tiết producer/consumer, transactional outbox, GitHub Actions hay benchmark.

### 3.3. Duy – Event-Driven Design & Infrastructure

**File sửa:** `sections/event_driven_design.tex`, `tables/events.tex`; thêm hình luồng sự kiện/triển khai vào `figures/`.

- **IV. Event-Driven Design:** Cross-Service Rental Workflow; OpenFeign; Kafka; Transactional Outbox; Idempotent Consumer; Gateway Routing/Request Flow; Docker/CI-CD.
- **Nhận phần Long:** Đọc mã nguồn/cấu hình Gateway, Kafka, DevOps thực tế, rồi trình bày chính xác trong Section IV. Không mặc nhiên nhận trách nhiệm sửa hoặc xây lại code của Long.
- **Bàn giao:** Section IV; bảng topic/event; **Fig. 2 – Rental Workflow**, **Fig. 3 – Outbox Processing**, **Fig. 4 – Deployment Topology**; thông tin kỹ thuật cho các bài test.
- **Không viết:** Lý thuyết Related Work dài dòng, tổng quan RBAC chi tiết hoặc kết quả benchmark.

### 3.4. Hoàng – Evaluation, Discussion & Conclusion

**File sửa:** `sections/evaluation.tex`, `sections/discussion.tex`, `sections/conclusion.tex`, `tables/experiments.tex`; thêm biểu đồ vào `figures/`, dữ liệu kiểm thử vào `experiments/`.

- **V. Evaluation:** Experimental Setup; Metrics; API Latency/Throughput; Kafka/Event Reliability; Duplicate Event; Failure Recovery.
- **VI. Discussion:** Giải thích kết quả, trade-offs, limitations và threats to validity.
- **VII. Conclusion:** Tóm tắt những gì thực nghiệm chứng minh được và hướng nghiên cứu tiếp theo.
- **Bàn giao:** Các chương V–VII; bảng test và kết quả; **Fig. 5 – Performance Results**, **Fig. 6 – Failure Recovery**; dữ liệu thô, lệnh test, môi trường và số lần chạy.
- **Không viết:** Lặp lại chi tiết thiết kế service, Kafka hay hạ tầng đã thuộc Huy/Duy.

## 4. Quy tắc tránh trùng lặp

| Chủ đề                                                  | Chủ sở hữu nội dung | Giới hạn phần còn lại                                             |
| ---------------------------------------------------------- | ----------------------- | ---------------------------------------------------------------------- |
| Lý thuyết Microservices, EDA, công trình trước       | **Dương**       | Huy/Duy chỉ giải thích cách **hệ thống này** áp dụng    |
| Sơ đồ kiến trúc, phân tách service, quyền và DB   | **Huy**           | Duy chỉ nhắc thành phần đủ để giải thích luồng hoạt động |
| Gateway filter/routing, Kafka, Outbox, Docker/CI-CD        | **Duy**           | Huy chỉ đề cập Gateway ở cấp độ kiến trúc và phân quyền   |
| Workflow liên service                                     | **Duy**           | Huy chỉ mô tả trách nhiệm của mỗi service                       |
| Thực nghiệm, số liệu, đồ thị, phân tích kết quả | **Hoàng**        | Người khác cung cấp log, setup và xác nhận kỹ thuật           |
| Phần Gateway/Kafka/DevOps của Long                       | **Duy**           | Các bạn khác review và hỗ trợ khi cần, không cùng viết       |

**Nguyên tắc:** Mỗi mục và mỗi hình/bảng chỉ có một người sửa chính. Review bằng nhận xét/Pull Request, không tự ý thay phần của người khác. Nếu sửa file dùng chung, báo nhóm trước.

## 5. Quy chuẩn viết LaTeX

1. **Viết bằng tiếng Anh**, văn phong học thuật, nhất quán thuật ngữ.
2. Mỗi người viết trong `sections/*.tex`, **không thêm** `\documentclass`, `\begin{document}`, `\end{document}` vào file chương.
3. Trong mỗi chương dùng `\section`, `\subsection`, `\cite{key}`, `\ref{label}` hợp lệ; các bảng con import bằng `\input{tables/ten_file}`.
4. Hình lưu trong `figures/` (ưu tiên PDF vector hoặc PNG rõ nét); chú thích bằng `\caption` và gán `\label`.
5. Tài liệu tham khảo ghi vào `references.bib` sau khi xác minh nguồn; không tạo DOI, tác giả hoặc kết quả giả.
6. Các chỗ thiếu thông tin ghi `\todo{...}` hoặc comment `% TODO`, không tự suy đoán rằng chức năng đã triển khai.
7. Không đưa thông tin bí mật (API key, password, token, IP nội bộ nhạy cảm) vào bài hoặc GitHub.

## 6. Quy trình GitHub đề xuất

**Mỗi người tạo branch từ `main`:**

```bash
git checkout main
git pull origin main
git checkout -b paper/duong    # Thay bằng paper/huy, paper/duy, paper/hoang
```

Quy trình mỗi lần làm việc:

1. `git pull origin main` trước khi bắt đầu một phần mới và cập nhật branch theo quy trình của nhóm.
2. Chỉnh **chỉ những file mình sở hữu**.
3. Compile thử `main.tex` (nếu đã có LaTeX trên máy).
4. Commit có nội dung rõ ràng, ví dụ: `docs: draft related work section`.
5. Push branch và mở Pull Request vào `main`.
6. Một thành viên khác review, sau đó mới merge; không force-push hoặc ghi đè việc người khác.

**Lưu ý:** Lệnh tạo branch ở trên chỉ là ví dụ. Mỗi người dùng tên branch tương ứng, không tạo tất cả branch trên cùng một máy rồi cùng sửa một nhánh.

## 7. Biên dịch để đọc PDF

Mở **`main.tex`** (không chạy từng file trong `sections/`). Trong VS Code với LaTeX Workshop, dùng `Ctrl + Alt + B` để build và `Ctrl + Alt + V` để xem PDF, nếu máy đã cài bộ LaTeX.

Hoặc chạy tại thư mục project:

```bash
latexmk -pdf -interaction=nonstopmode -halt-on-error main.tex
```

Nếu dùng MiKTeX trên Windows, `latexmk` có thể yêu cầu Perl. Nếu chưa có `latexmk`:

```bash
pdflatex main.tex
bibtex main
pdflatex main.tex
pdflatex main.tex
```

## 8. Checklist trước khi nộp phần của mình

- [ ] Đã viết đủ phạm vi và mục tiêu số từ.
- [ ] Không trùng nội dung với chương người khác.
- [ ] Mọi hình/bảng đều có chú thích, nhãn và được nhắc trong bài.
- [ ] Mọi trích dẫn `\cite{...}` đều tồn tại trong `references.bib`.
- [ ] Không còn TODO quan trọng chưa được giải quyết (hoặc đã báo rõ lý do).
- [ ] Không có thông tin giả hoặc số liệu chưa đo.
- [ ] `main.tex` biên dịch thành công (hoặc đã báo lỗi cụ thể).
- [ ] Đã mở Pull Request và yêu cầu ít nhất một người review.

## 9. Quy tắc bàn giao cuối cùng

- **Dương:** Chuẩn hóa phần mở đầu, nghiên cứu liên quan và bibliography; cập nhật Abstract sau khi có kết quả.
- **Huy:** Kiểm tra tính chính xác của kiến trúc, database, phân quyền.
- **Duy:** Kiểm tra toàn bộ mô tả sự kiện, Gateway/Kafka/DevOps và tính nhất quán với mã nguồn.
- **Hoàng:** Kiểm tra khả năng tái lập thực nghiệm, số liệu, biểu đồ và các kết luận.

**Tất cả thành viên cùng chịu trách nhiệm chất lượng bài cuối**, nhưng từng file có một người phụ trách chính để tránh xung đột.
