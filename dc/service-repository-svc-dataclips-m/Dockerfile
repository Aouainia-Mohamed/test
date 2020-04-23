FROM golang:1.13.7-alpine AS builder


ENV GO111MODULE=on \
    CGO_ENABLED=0 \
    GOOS=windows \
    GOARCH=amd64
    
WORKDIR /Users/med/Desktop/pfe/app

# Copy and download dependency using go mod
COPY go.mod .
COPY go.sum .
RUN go mod download

COPY . .
RUN go-wrapper download
RUN go-wrapper install

RUN go build -v

FROM alpine:3.5

#add SSL root certificates
RUN apk --no-cache add ca-certificates

WORKDIR /usr/local/bin

COPY --from=builder /usr/src/app/app .
CMD ["./main"]
