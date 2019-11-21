# Attentional ASR Models Misbehave on Out-of-domain Utterances

This repo describes artifacts for the paper:
```
@article{keung2020attentional,
  title={Attentional {ASR} Models Misbehave on Out-of-domain Utterances},
  author={Keung, Phillip and Niu, Wei and Lu, Yichao and Salazar, Julian and Bhardwaj, Vikas},
  journal={CoRR},
  year={2020}
}
```
This project is made available under the CC-BY-3.0 license. See the LICENSE file.

## Filtered Audio BNC dataset

This utterance dataset was extracted from [Audio BNC](http://www.phon.ox.ac.uk/AudioBNC).

### Source

- The transcripts are extracted from TextGrid files [released by Oxford University](https://ora.ox.ac.uk/objects/uuid:e0cd66cc-32cf-41b9-962e-416361e41c93) and made available under a Creative Commons Attribution License, [CC BY 3.0](https://creativecommons.org/licenses/by/3.0/).
- The referenced `.wav` files are from [Audio BNC](http://www.phon.ox.ac.uk/AudioBNC) (the audio edition of the Spoken British National Corpus) and made available under the [BNC User Licence](http://www.natcorp.ox.ac.uk/docs/licence.pdf), which permits use for scientific research and study only; see both links for details.

### Processing

1. The transcripts come in the form of words and timestamps. We created utterances by labeling words with gaps of less than 0.25 secs as part of the same 'long' utterance.
2. For each 'long' utterance, we draw a 5- to 15-word span at random and consider its start/end stamps.
3. We extend these start and end times by 0.15 secs before and after.
4. This gives 40,858 utterances in `bnc_dataset.json`, described in newline-delimited JSON format.
5. We cap utterance duration to 15 secs, keeping 39,320 utterances as in the paper.
6. Using our sequence-to-sequence ASR model, we identified 170 utterances which gave 200+ characters of output, and 1,607 utterances which had a WER of <50%.
