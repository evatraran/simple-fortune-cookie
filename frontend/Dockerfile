FROM golang:1.16 AS build
RUN mkdir /app
ADD . /app
WORKDIR /app
COPY * ./

RUN CGO_ENABLED=0 GOOS=linux go build -o frontend .
FROM alpine:latest as run
COPY --from=build /app/ ./
EXPOSE 9000
CMD ["./frontend"]
