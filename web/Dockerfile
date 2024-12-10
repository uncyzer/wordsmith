FROM golang:alpine AS build
WORKDIR /app
COPY ./dispatcher.go .
RUN go build dispatcher.go

# STAGE 2 - Start app
FROM alpine:latest AS app-prod
COPY ./static /static
COPY --from=build /app/dispatcher .
CMD ["./dispatcher"]