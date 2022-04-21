# gpublame

Want to find out who's hogging the GPU? `gpublame` gives you the proof you need to duke it out in the research group chat.

`gpublame` depends on `nvidia-smi pmon`, which means monitoring is limited to a maximum of 4 devices. You should be able to use `CUDA_VISIBLE_DEVICES` to select which devices to show. If someone with more than 4 GPUs would like to help me test code to support more than 4 devices, please reach out. :)

## installation

Go to [Releases](https://github.com/kylrth/gpublame/releases) and download the latest release for your architecture to somewhere on your PATH, e.g.:

```sh
wget 'https://github.com/kylrth/gpublame/releases/latest/download/gpublame-amd64' -O - | sudo tee /usr/bin/gpublame > /dev/null
sudo chmod +x /usr/bin/gpublame
```

Let me know if I don't build for your architecture so I can add it.

## usage

```sh
gpublame
```

Pretty simple.

### package usage

You can use some `gpublame` functionality in your own Go code:

```go
import (
    "context"

    "github.com/kylrth/gpublame"
)

func main() {
    gpublame.Pmon(context.Background())

    // ...
}
```
