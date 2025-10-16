# Pipewire noise canceling source from copr

link : <https://hackernoon.com/enabling-instant-noise-cancellation-on-linux>
link : <https://copr.fedorainfracloud.org/coprs/uriesk/noise-suppression-for-voice>

```bash
sudo dnf install ladspa-noise-suppression-for-voice
```

## config pipewire

```bash
mkdir ~/.config/pipewire/pipewire.conf.d
```

creating file name 99-input-denoising.conf

### config

```conf
context.modules = [
{   name = libpipewire-module-filter-chain
    args = {
        node.description =  "Noise Canceling source"
        media.name =  "Noise Canceling source"
        filter.graph = {
            nodes = [
                {
                    type = ladspa
                    name = rnnoise
                    plugin = /usr/lib64/ladspa/librnnoise_ladspa.so
                    label = noise_suppressor_mono
                    control = {
                        "VAD Threshold (%)" = 60.0
                        "VAD Grace Period (ms)" = 200
                        "Retroactive VAD Grace (ms)" = 0
                    }
                }
            ]
        }
        capture.props = {
            node.name =  "capture.rnnoise_source"
            node.passive = true
            audio.rate = 48000
        }
        playback.props = {
            node.name =  "rnnoise_source"
            media.class = Audio/Source
            audio.rate = 48000
        }
    }
}
]

```
