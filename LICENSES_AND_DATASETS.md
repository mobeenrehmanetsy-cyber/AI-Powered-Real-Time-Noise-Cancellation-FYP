# Dataset and License Notes

This file records the dataset choices used by the Colab notebook. Always review the current license terms and citation requirements before redistribution or publication.

| Dataset | Project role | Source | License / note |
| --- | --- | --- | --- |
| Mini LibriSpeech `train-clean-5` | Clean speech | [OpenSLR 31](https://www.openslr.org/31/) | LibriSpeech is released under CC BY 4.0; cite the LibriSpeech paper and source page |
| ESC-50 | Environmental noise | [Official GitHub repository](https://github.com/karolpiczak/ESC-50) | CC BY-NC 3.0; non-commercial academic use should follow the license and citation requirements |

## Why these sources are used

Mini LibriSpeech gives the project a manageable starting corpus with multiple speakers. ESC-50 provides labelled everyday sound categories that can be used as environmental noise. They address different parts of the three-class problem and are small enough for a first Colab pipeline check.

## Dataset overlap decision

The notebook does not concatenate Mini LibriSpeech with LibriSpeech `train-clean-100`. Mini LibriSpeech is part of the LibriSpeech family, so combining the subsets without a verified file and speaker overlap audit could duplicate material or speakers. That would make the speaker-independent test score unreliable.

## Considered but not silently downloaded

MUSAN, DEMAND, DNS Challenge data, WHAM/WHAMR, LibriMix, and OpenSLR room impulse-response resources may improve future robustness or multi-speaker experiments. They are not automatically added because each requires separate download size, license, metadata, split, and validation decisions. In particular, the notebook only uses room impulse responses that have been manually verified and placed in its configured RIR directory; it does not assume every WAV file from a room/noise archive is an RIR.

## Citation reminder

Keep the original dataset citations with the final FYP report. Dataset license metadata is descriptive project documentation, not legal advice.
