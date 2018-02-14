# CallHome Database Plugin

# Setup
```
# Generate pyannote mdtm files
> python parse_transcripts.py ~/Downloads/eng
# Convert audio files from mp3 to wav format
> python utils.py ~/Downloads/CABank_CallHome
# update db.yml file
> cat ~/.pyannote/db.yml
CallHome: /Users/venkatesh/Downloads/CABank_CallHome/{uri}.wav
```

## Feature Extraction
```text
# Add config.yml
> cat config.yml
feature_extraction:
   name: YaafeMFCC               # extract MFCC using Yaafe
   params:
      coefs: 11                  # 11 coefs
      D: True                    # with coefs 1st derivative
      DD: True                   # with coefs 2nd derivative
      e: False                   # without energy
      De: True                   # with energy 1st derivative
      DDe: True                  # with energy 2nd derivative
      step: 0.010                # every 10ms
      duration: 0.020            # using 20ms-long windows
> pyannote-speech-feature . CallHome.SpeakerDiarization.CallHomeProtocol
```
