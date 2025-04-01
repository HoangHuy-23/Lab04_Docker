# Sử dụng Go phiên bản mới nhất làm base image để build ứng dụng
FROM golang:latest AS build

# Thiết lập thư mục làm việc trong container
WORKDIR /app

# Sao chép toàn bộ mã nguồn vào container
COPY . .

# Tải xuống các dependencies và build ứng dụng
RUN go build -o main .

# Tạo một lightweight image chỉ để chạy ứng dụng
FROM alpine:latest

WORKDIR /root/

# Sao chép file thực thi từ build stage trước đó
COPY --from=build /app/main .

# Cấp quyền thực thi cho file
RUN chmod +x main

EXPOSE 8080

CMD ["./main"]

