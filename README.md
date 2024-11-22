# frps

[![frps](http://dockeri.co/image/hazertothepast/frps)](https://hub.docker.com/r/hazertothepast/frps)

Docker Images for Frps Based on Alpine.

## Usage

```bash
docker run --restart=always --network host -d -v /etc/frp/frps.toml:/etc/frp/frps.toml --name frps hazertothepast/frps
```

## Forked from
[https://github.com/snowdreamtech/frp](https://github.com/snowdreamtech/frp)

## License

MIT
