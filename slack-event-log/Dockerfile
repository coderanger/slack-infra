FROM golang:1 as build

ADD . /src
WORKDIR /src

RUN go build -o /slack-event-log sigs.k8s.io/slack-infra/slack-event-log

FROM gcr.io/distroless/base
COPY --from=build /slack-event-log /slack-event-log
USER 65534
ENTRYPOINT ["/slack-event-log"]
