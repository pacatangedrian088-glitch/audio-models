# audio-models

Pre-converted audio models for on-device use on Apple platforms. They're published as release assets.

## htdemucs_6s_fp16 (release `htdemucs-6s-v1`)

[HT-Demucs](https://github.com/facebookresearch/demucs) 6-source music separation (drums, bass, other, vocals, guitar, piano), converted to Core ML (mlprogram, mixed fp16, iOS 17+).

- `htdemucs_6s_fp16.aar`: the compiled `.mlmodelc`, packed with Apple Archive (lzfse). 53,447,653 bytes.
- SHA-256: `a4459311505d150ff0702d80a96d99b413b3932f5ca63e27890725a02d72c1f1`
- 60.7 dB SNR against the PyTorch reference.
- The model runs only the network core. STFT/iSTFT (n_fft 4096, hop 1024, Hann, normalised), input normalisation and 7.8 s chunking with a triangular cross-fade run outside the model.
- Inputs: `mix` 1×2×343980 and `spec` 1×4×2048×336. Outputs: `spec_out` 1×6×4×2048×336 and `wave_out` 1×6×2×343980.
- Unpack with `aa extract -i htdemucs_6s_fp16.aar -d htdemucs_6s_fp16.mlmodelc`.

## Licence

HT-Demucs is © Meta Platforms, Inc. and affiliates, released under the MIT licence (see [LICENSE](LICENSE)). These converted files are redistributed under the same licence.
