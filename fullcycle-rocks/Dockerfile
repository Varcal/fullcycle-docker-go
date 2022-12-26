FROM golang:1.16-alpine AS build

WORKDIR /app
COPY go.mod .

RUN go mod download

COPY *.go .

RUN go build -o /fullcycle main.go


FROM scratch
WORKDIR /
COPY --from=build /fullcycle /fullcycle

ENTRYPOINT ["/fullcycle"]