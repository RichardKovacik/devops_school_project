# Multi-stage build docker file

# app build stage
FROM golang:alpine as builder
RUN mkdir /build
## TODO:
# Vasou ulohou je:
# 1. Skopirovat zdrojove kody aplikacie do adresara /build, ktory sa vytvoril v predchadzajucom kroku
COPY . /build
# 2. Nastavit adresar /build ako pracovny adresar (work directory)
WORKDIR /build
RUN CGO_ENABLED=0 GOOS=linux go build -a -o main .

# image build image - use scratch to get smallest possible size of an image
FROM scratch
#  1. nastavit pracovny adresar (work directory) na: /app
WORKDIR /app
## TODO:
# Prikaz COPY, ktory poznate, je mozne pouzit aj na kopirovanie suborov, ktore vznikli v predchadzajucom stage, tj:
#  2. pridat prikaz, ktory skopiruje zo stage builder subor: /builder/main do adresara /app/ (vsimnite si na riadku c.1>COPY --from=builder /build/main /app
#aaaa
#  3. pridat instrukciu, ktora zabezpeci, ze po vytvoreni kontajnera sa spusti aplikacia (tj. ./main)
CMD ["./main"]