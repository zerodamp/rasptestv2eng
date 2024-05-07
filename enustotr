import speech_recognition as sr
import deepl

AUTH_KEY = "2896b57c-fedb-4768-bb2d-446a14b3bfef:fx"

def transcribe():
    recognizer = sr.Recognizer()
    microphone = sr.Microphone()

    with microphone as source:
        recognizer.adjust_for_ambient_noise(source)
        print("Lütfen konuşun...")
        while True:
            try:
                audio = recognizer.listen(source)
                text = recognizer.recognize_google(audio, language="en-US")
                print("Siz:", text)
                translated_text = translate(text)
                print("Çeviri:", translated_text)
            except sr.UnknownValueError:
                print("Anlaşılamadı")
            except sr.RequestError as e:
                print("Google Ses tanımlama servisine erişilemiyor; {0}".format(e))

def translate(text: str):
    translator = deepl.Translator(AUTH_KEY)

    return translator.translate_text(text, target_lang="TR").text

def main_menu():
    while True:
        print("\n------ Ana Menü ------")
        print("1. Canlı Transkripsiyon Başlat")
        print("2. Çıkış")

        choice = input("Seçiminizi girin: ")

        if choice == "1":
            transcribe()
        elif choice == "2":
            print("Programdan çıkılıyor...")
            break
        else:
            print("Geçersiz seçim. Lütfen tekrar deneyin.")

if __name__ == "__main__":
    main_menu()
