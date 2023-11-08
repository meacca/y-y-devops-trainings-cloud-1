FROM golang:1.21 as build

WORKDIR /go/src/app
COPY . .

RUN go mod download
RUN CGO_ENABLED=0 go build -o /go/bin/app

# Now copy it into our base image.
FROM gcr.io/distroless/static-debian12:latest-amd64
COPY --from=build /go/bin/app /
CMD ["/app"]
