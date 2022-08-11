FROM golang:1.16 AS build
RUN mkdir /app
ADD . /app
WORKDIR /app
COPY * ./
RUN go mod download github.com/gomodule/redigo
RUN CGO_ENABLED=0 GOOS=linux go build -o backend .

FROM alpine:latest as run
COPY --from=build /app/backend ./
EXPOSE 9000
CMD ["./backend"]
