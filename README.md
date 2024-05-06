# hfd.sh

Modified from [hf-mirror.com][1].

## Installation

```shell
cat > /usr/local/bin/hfd << EOF
#!/usr/bin/env bash
FILE=/tmp/$RANDOM.sh
curl 'https://cdn.jsdelivr.net/gh/LucienShui/hfd@main/hfd.sh' > ${FILE}
export HF_ENDPOINT=https://hf-mirror.com
bash ${FILE} "${@}"
EOF
chmod +x /usr/local/bin/hfd
```

### aria2c

You can hack a aria2c using docker.

```shell
cat > /usr/local/bin/aria2c << EOF
#!/usr/bin/env bash
docker run -u $(id -u):$(id -g) -v $(pwd):/w --workdir /w --rm -ti --entrypoint aria2c p3terx/aria2-pro:test "${@}"
EOF
chmod +x /usr/local/bin/aria2c
```

## Usage

```shell
hfd gpt2 --tool aria2c -x 4  # Download model
hfd wikitext --dataset --tool aria2c -x 4  # Download dataset
hfd meta-llama/Llama-2-7b --hf_username YOUR_HF_USERNAME --hf_token hf_***  # Download with authorization
```

[1]: https://hf-mirror.com/
