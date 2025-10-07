FROM golang:1.25-bookworm as Develop

# 必要なパッケージのインストール
RUN apt update && \
    apt install -y git curl wget

# ワーキングディレクトリ取得
WORKDIR /go/src/app

# ファイルをコピー
COPY ./src .

# デプロイメント環境の作成
RUN go install github.com/air-verse/air@latest

ENTRYPOINT [ "air","-c","./.air.toml" ]
