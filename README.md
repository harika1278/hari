import speech_recognitions as sr
from google_trans_new import google_translator
from gtts import gTTs
from playsound import playsound
r=sr.Recognizer()
translator=google_translator()
while True:
    with sr.microphone() as source:
        print("speak now!")
        audio=r.listen(sorce)
        try:
            speech_text=r.recognize.google(audio)
            print(speech_text)
            if(speech_text == "exit"):
                break
        except sr.UnknowValueError:
            print("could not understand")
        except sr.RequestError:
            print("could not request result from google")
            translated_text=translator.translate(speech_text,lang_tgt='fr')
            print(translated_text)
            voice=gTTs(translated_text,lang='fr')
            voice.save("voice.mp3")
            playsound("voice.mp3")
            os.remove("voice.mp3")
