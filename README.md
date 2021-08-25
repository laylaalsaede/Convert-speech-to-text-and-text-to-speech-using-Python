# Convert-speech-to-text-and-text-to-speech-using-Python

This repository the fourth task for internship in smart methods
It is about convert the speech to text and vice versa by using IBM WATSON and Python language.

### Built With:
- Python language
- Speech to text IBM WATSON
- Text to Speech IBM WATSON

### Prerequisites
* [Python](https://www.python.org/downloads/)
* Account in [IBM Cloud](https://cloud.ibm.com)

### Setup
* Setup Watson STT Service: cloud.ibm.com/catalog 
  * Speech to Text. 
  * Text to Speech.
* Clone Live STT Code: https://github.com/IBM/watson-streaming-stt 

### Install
```
pip3 install pyaudio
pip3 install websocket-client
``` 

### Speech to Text 
* In [speech.cfg](https://github.com/AsmaAbdullah1998/Live--Speech-to-Text-and-Text-to-Speech-/blob/main/speech.cfg) file
``` 
apikey = 'YD3YBUw2Cv3CRQUZ7OGDzLpXNy-5HIr9LtSEV2OrCXAZ' #Your apikey
```
* Create [output.text](https://github.com/AsmaAbdullah1998/Live--Speech-to-Text-and-Text-to-Speech-/blob/main/output.txt) file by writing this code below in [transcribe.py](https://github.com/AsmaAbdullah1998/Live--Speech-to-Text-and-Text-to-Speech-/blob/main/transcribe.py) file.
```
with open('output.txt', 'w') as out:
            out.writelines(data['results'][0]['alternatives'][0]['transcript'])
```
> inside the on_message function. 


### Text to Speech
* In [transcribe.py](https://github.com/AsmaAbdullah1998/Live--Speech-to-Text-and-Text-to-Speech-/blob/main/transcribe.py) file write the code: 
```
authenticator = IAMAuthenticator('vYI9rkcSWl_wELYNt2Y-5uxAuNDmPKL9XkMLal4R0Vn1') #Your apikey
tts = TextToSpeechV1(authenticator=authenticator)
tts.set_service_url('https://api.us-south.text-to-speech.watson.cloud.ibm.com/instances/4afce834-c1d1-4edf-ba89-dafcd89544a0') #Your url
```
* Create [output.mp3](https://github.com/AsmaAbdullah1998/Live--Speech-to-Text-and-Text-to-Speech-/blob/main/output.mp3) file write the code 
```
with open('output.txt', 'r') as f:
            text = f.readlines()
    text = [line.replace('\n','') for line in text]
    text = ''.join(str(line) for line in text)
    with open('./output.mp3', 'wb') as audio_file:
        res = tts.synthesize(text, accept='audio/mp3', voice='en-GB_JamesV3Voice').get_result()
        audio_file.write(res.content)
```




***Note: I used two codes to convert text to speech and they both work***
