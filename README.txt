# HCMUT LaTeX Report Template

Template báo cáo LaTeX chuyên nghiệp cho Đại học Bách Khoa TP.HCM với nhiều tính năng được cấu hình sẵn.

## Nguồn gốc
- Repository: https://github.com/hoang-himself/hcmut-report
- Issues: https://github.com/hoang-himself/hcmut-report/issues
- Commit: 350906b86be7adae1c953217029cbe12ad4f6ac5

## Tính năng chính

### 1. Class báo cáo HCMUT (hcmut-report.cls)
- **Layout chuyên nghiệp**: Định dạng A4, margin chuẩn (trái 3cm, phải 2cm, trên/dưới 2cm)
- **Header tự động**: Logo và thông tin trường tự động xuất hiện trên mỗi trang
- **Trang bìa tự động**: Tạo trang bìa theo format chuẩn của HCMUT
- **Hỗ trợ tiếng Việt**: Sử dụng vntex và babel
- **Numbering tự động**: Đánh số section, equation, table, figure theo section

### 2. Code Highlighting (codespace.sty)
- **Listings**: Hỗ trợ nhiều ngôn ngữ lập trình với syntax highlighting
- **Minted**: Code highlighting chất lượng cao (yêu cầu Python Pygments)
- **Inline code**: Chèn code ngay trong dòng văn bản
- **External files**: Import code từ file bên ngoài
- **Line numbering**: Đánh số dòng tự động
- **Custom styling**: Màu sắc và theme có thể tùy chỉnh

### 3. Tables nâng cao
- **Booktabs**: Bảng đẹp không viền dọc
- **Tabularx**: Bảng tự động điều chỉnh độ rộng
- **Longtable**: Bảng dài nhiều trang
- **Multirow/Multicol**: Gộp ô ngang và dọc

### 4. Enumerator tùy chỉnh
- **Custom numbering**: Đánh số theo ý muốn (a, b, c hoặc i, ii, iii)
- **Custom labels**: Nhãn tùy chỉnh cho từng item
- **Flexible formatting**: Định dạng linh hoạt

### 5. Figures linh hoạt
- **Max width**: Tự động điều chỉnh kích thước ảnh
- **Frame**: Thêm khung cho ảnh
- **Scale**: Thay đổi tỷ lệ ảnh
- **Adjustbox**: Nhiều tùy chọn định dạng ảnh

### 6. References và Citations
- **Natbib**: Hệ thống trích dẫn mạnh mẽ
- **Cleveref**: Tham chiếu thông minh với \Cref{}
- **Hyperref**: Liên kết tự động trong PDF
- **Bibliography**: Quản lý tài liệu tham khảo

## Cách sử dụng

### Cài đặt cơ bản
1. Đảm bảo có LaTeX distribution (TeX Live, MiKTeX)
2. Cài đặt Python và Pygments (cho minted):
   ```bash
   pip install Pygments
   ```

### Biên dịch
```bash
# Cơ bản
pdflatex report.tex
bibtex report
pdflatex report.tex
pdflatex report.tex

# Với minted (cần --shell-escape)
pdflatex --shell-escape report.tex
bibtex report
pdflatex --shell-escape report.tex
pdflatex --shell-escape report.tex
```

### Cấu hình thông tin báo cáo
Trong file `report.tex`, chỉnh sửa các thông tin:

```latex
\coursename{Tên môn học}
\reporttype{Loại báo cáo}
\title{Tiêu đề báo cáo}
\advisor{& Giảng viên hướng dẫn &}
\stuname{%
  & Sinh viên 1 & MSSV 1 \\
  & Sinh viên 2 & MSSV 2 \\
}
```

### Sử dụng code highlighting

#### Listings (đơn giản)
```latex
% Inline code
\lstinline[language=python]{print('Hello')}

% Code block
\begin{lstlisting}[language=python,caption={Mô tả}]
print('Hello World')
\end{lstlisting}

% Import từ file
\lstinputlisting[language=python,caption={Mô tả}]{code/example.py}
```

#### Minted (chất lượng cao)
```latex
% Inline code
\mintinline{python}{print('Hello')}

% Code block
\begin{code}{python}
print('Hello World')
\end{code}

% Import từ file
\inputcode{python}{code/example.py}
```

### Tạo bảng đẹp
```latex
\begin{table}[H]
  \centering
  \caption{Tiêu đề bảng}
  \label{tab:example}
  \begin{tabularx}{\linewidth}{l*{2}{X}}
    \toprule
    Cột 1 & Cột 2 & Cột 3 \\
    \midrule
    Dữ liệu & Dữ liệu & Dữ liệu \\
    \bottomrule
  \end{tabularx}
\end{table}
```

### Chèn hình ảnh
```latex
\begin{figure}[H]
  \centering
  \includegraphics[max width=0.8\linewidth]{path/to/image}
  \caption{Mô tả hình ảnh}
  \label{fig:example}
\end{figure}
```

### Quy ước đặt tên label
- `chap:` cho chapters
- `sec:` cho sections  
- `eq:` cho equations
- `fig:` cho figures
- `tab:` cho tables
- `lst:` cho listings
- `enum:` cho enumerators

### Tham chiếu
```latex
% Tham chiếu thông thường
\ref{fig:example}

% Tham chiếu thông minh (tự động thêm "Figure", "Table"...)
\Cref{fig:example}
```

## Cấu trúc thư mục
```
├── report.tex          # File chính
├── hcmut-report.cls    # Class định nghĩa format
├── codespace.sty       # Package cho code highlighting
├── chapters/           # Thư mục chứa các chapter
├── code/              # Thư mục chứa source code
├── graphics/          # Thư mục chứa hình ảnh
│   └── hcmut.png      # Logo trường
└── refs/              # Thư mục chứa bibliography
    └── example.bib    # File tài liệu tham khảo
```

## Ghi chú
- Template hỗ trợ cả tiếng Anh và tiếng Việt
- Để sử dụng tiếng Việt làm ngôn ngữ chính, đổi `[english]` thành `[english,vietnamese]` trong hcmut-report.cls
- Minted yêu cầu flag `--shell-escape` khi biên dịch
- Có thể sử dụng mode `draft` để biên dịch nhanh hơn trong quá trình viết

## Troubleshooting
- **Lỗi minted**: Cài đặt Python Pygments và sử dụng `--shell-escape`
- **Lỗi font tiếng Việt**: Cài đặt gói vntex
- **Lỗi bibliography**: Chạy bibtex sau lần pdflatex đầu tiên
- **Lỗi hyperref**: Biên dịch nhiều lần để cập nhật references
