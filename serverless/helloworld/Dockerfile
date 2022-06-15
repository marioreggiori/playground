FROM golang:1.18 as builder

WORKDIR /app

COPY go.* ./
RUN go mod download

COPY . ./

RUN CGO_ENABLED=0 GOOS=linux go build -mod=readonly -v -o server

FROM scratch
COPY --from=builder /app/server /server
CMD ["/server"]
