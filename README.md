# simple_diarizer
Simplified diarization pipeline using some pretrained models.

### Install

Simplified diarization is available on PyPI:

```
pip install simple-diarizer
```

### Usage

Made to be a simple as possible to go from an input audio file to diarized segments.

```python
import soundfile as sf
import matplotlib.pyplot as plt

from simple_diarizer.diarizer import Diarizer
from simple_diarizer.utils import combined_waveplot

diar = Diarizer(
                  embed_model='xvec', # 'xvec' and 'ecapa' supported
                  cluster_method='sc' # 'ahc' and 'sc' supported
               )

segments = diar.diarize(WAV_FILE, num_speakers=NUM_SPEAKERS)

signal, fs = sf.read(WAV_FILE)
combined_waveplot(signal, fs, segments)
plt.show()
```

<p align="center">
  <img src="media/diarized_waveplot.png?raw=true">
</p>


# Pre-trained Models

The following pretrained models are used:

 - Voice Activity Detection (VAD)
     - [Silero VAD](https://github.com/snakers4/silero-vad)
 - Deep speaker embedding extraction
     - [SpeechBrain](https://github.com/speechbrain/speechbrain)
        - [X-Vector](https://huggingface.co/speechbrain/spkrec-xvect-voxceleb)
        - [ECAPA-TDNN](https://huggingface.co/speechbrain/spkrec-ecapa-voxceleb)
 - (Optional/Experimental) Speech-to-text
     - [ESPnet Model Zoo](https://github.com/espnet/espnet_model_zoo)
        - English ASR model

# Demo
## Diarize any input Youtube URL

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1cIUbyyZfOU7AsTpwEdSozATo9QCS14fz)

## Diarize any input wav file

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1tG8TXxPDv9211bZcxhH6CTRKS6bsTRjA#scrollTo=R2kKRXLo9mJr)

# Other References

- Spectral clustering methods lifted from [https://github.com/wq2012/SpectralCluster](https://github.com/wq2012/SpectralCluster)


# Planned Features

[![](https://shields.io/badge/simple__diarizer-Trello-blue?logo=Trello&style=flat)](https://trello.com/b/2ZN9ybC1/simplediarizer)
