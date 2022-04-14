import datetime
import sys
import time
import ctypes
import speech_recognition as sr
import pyttsx3
import wikipedia
import webbrowser
import os
import requests
from requests import get

import smtplib
import sys
import pyjokes
import subprocess
import pyautogui






engine = pyttsx3.init('sapi5')
voices = engine.getProperty('voices')
engine.setProperty('voice', voices[0].id)

def speak(audio):
    engine.say(audio)
    engine.runAndWait()


def wishMe():
    hour = int(datetime.datetime.now().hour)
    tt = time.strftime('%I:%M %p')
    if hour >= 0 and hour < 12:
        speak(f"Good Morning, its {tt}")
    elif hour >= 12 and hour < 16:
        speak(f"Good Afternoon, its {tt}")
    elif hour >= 16 and hour < 20:
        speak(f"Good Evening, its {tt}")
    else:
        speak(f"Good Night, its {tt}")

    speak("I am Jarvis Sir . Please tell me how may I help you ")

def takeCommand():
    #IT TAKES MICROPHONE INPUT FROM THE USER AND RETURNS STRING OUTPUT

    r = sr.Recognizer()
    with sr.Microphone() as source:
        print("listening....")
        r.pause_threshold = 1
        audio = r.listen(source, timeout=5, phrase_time_limit=10)

    try:
        print("Recognizing....")
        query = r.recognize_google(audio, language='en-in')
        print(f"User said: {query}\n")

    except Exception as e:
        print("Say that again please....")
        return "None"
    return query

def sendEmail(to, content):
    server = smtplib.SMTP('smtp.gmail.com', 587)
    server.ehlo()
    server.starttls()
    server.login('aakashvasuu3@gmail.com', 'aaKA$hv1n1')
    server.sendmail('your email id', to, content)
    server.close()

def news():
    main_url = 'http://newsapi.org/v2/top-headlines?sources=the-times-of-india&apiKey=6ff24666673747f1a7942b9176a747fa'

    main_page = requests.get(main_url).json()
    articles = main_page['articles']
    head = []
    day = ['first','second','third','fourth','fifth','sixth','seventh','eighth','ninth','tenth']
    for ar in articles:
        head.append(ar['title'])
    for i in range(len(day)):
        speak(f'todays {day[i]} news is: , {head[i]}')


if _name_ == "__main__":
    wishMe()
    while True:
        query = takeCommand().lower()

    #logic for executing tasks based on query

        if 'open youtube' in query:
            webbrowser.open("youtube.com")
            speak("Opening youtube sir")

        elif 'the time' in query:
            tt = time.strftime('%I:%M %p')
            speak(f"Sir, the time is {tt}")

        elif 'open google' in query:
            speak("Sir, what should I search on google")
            cm = takeCommand().lower()
            webbrowser.open(f"{cm}")
            speak("Searching sir")

        elif 'open instagram' in query:
            webbrowser.open("instagram.com")
            speak("Opening instagram sir")

        elif 'wikipedia' in query:
            speak('Searching Wikipedia....')
            query = query.replace('wikipedia', '')
            results = wikipedia.summary(query, sentences=3)
            speak("According to Wikipedia")
            speak(results)
            print(results)


        elif 'open notepad' in query:
            npath = "C:\\Windows\\system32\\notepad.exe"
            os.startfile(npath)
            speak('Opening Notepad Sir')

        elif 'close notepad' in query:
            speak('closing notepad sir')
            os.system('taskkill /f /im notepad.exe')

        elif 'open vs code' in query:
            vpath = "D:\\Software\\Microsoft VS Code\\code.exe"
            os.startfile(vpath)
            speak("Opening vs Code sir")

        elif 'close vs code' in query:
            speak('closing vs code sir')
            os.system('taskkill /f /im code.exe')

        elif 'open pycharm' in query:
            ppath = "C:\\Program Files\\JetBrains\\PyCharm Community Edition 2021.3.1\\bin\\pycharm64.exe"
            os.startfile(ppath)
            speak("Opening Pycharm sir")

        elif 'close pycharm' in query:
            speak('closing pycharm sir')
            os.system('taskkill /f /im pycharm64.exe')

        elif 'open libreoffice' in query:
            lpath = "C:\\Program Files\\LibreOffice\\program\\soffice.exe"
            os.startfile(lpath)
            speak("opening Libreoffice sir")

        elif 'close libreoffice' in query:
            speak('closing libreoffice sir')
            os.system('taskkill /f /im soffice.exe')

        elif 'open command prompt' in query:
            os.system("start cmd")
            speak("Opening command prompt sir")

        elif 'close command prompt' in query:
            speak('closing command prompt sir')
            os.system('taskkill /f /im cmd.exe')

        elif 'ip address' in query:
            ip = get('https://api.ipify.org').text
            speak(f'Your IP address is {ip}')
            print(f'Your ip Address is {ip} ')

        


        elif 'email to raja' in query:
            try:
                speak("what should I send sir?")
                content = takeCommand().lower()
                to = "ekaliraja@gmail.com"
                sendEmail(to,content)
                speak('Email has been sent sir')

            except Exception as e:
                print(e)
                speak('sorry sir, I am not able to send this mail')


        elif 'email to vinitha' in query:
            try:
                speak("what should I send sir?")
                content = takeCommand().lower()
                to = "vvinitha1994@gmail.com"
                sendEmail(to,content)
                speak('Email has been sent sir')

            except Exception as e:
                print(e)
                speak('sorry sir, I am not able to send this mail')

        elif 'send email' in query:
            try:
                speak("What should I say sir?")
                content = takeCommand()
                speak("to whome should i send sir")
                to = input()
                sendEmail(to, content)
                speak("Email has been sent !")
            except Exception as e:
                print(e)
                speak("I am not able to send this email")


        elif 'how are you' in query:
            speak("I am fine sir, Thank you")

        elif "what's your name" in query or "What is your name" in query:
            assname = 'Jarvis'
            speak("My friends call me")
            speak(assname)
            print("My friends call me", assname)

        elif "who made you" in query or "who created you" in query:
            speak("I have been created by Aakash.")

        elif 'joke' in query:
            joke = pyjokes.get_joke()
            speak(joke)

        elif 'search' in query or 'play' in query:

            query = query.replace("search", "")
            query = query.replace("play", "")
            webbrowser.open(query)

        elif "who i am" in query:
            speak("If you talk then definitely your human.")

        elif "why you came to the world" in query:
            speak("Thanks to Aakash. further It's a secret")

        elif 'is love' in query:
            speak("It is 7th sense that destroy all other senses")

        elif "who are you" in query:
            speak("I am your virtual assistant created by Arjun")

        elif 'reason for creating you' in query:
            speak("I was created as a Minor project by Mister Aakash ")

        elif 'lock window' in query:
            speak("locking the device")
            ctypes.windll.user32.LockWorkStation()

        elif 'shutdown the system' in query:
            speak("Hold On a Sec ! Your system is on its way to shut down")
            os.system('shutdown /s /t 5')

        elif "where is" in query:
            query = query.replace("where is", "")
            location = query
            speak("User asked to Locate")
            speak(location)
            webbrowser.open("https://www.google.nl / maps / place/" + location + "")

        elif "restart the system" in query:
            speak('restarting the system sir')
            os.system('shutdown /r /t 5 ')

        elif 'sleep the system' in query:
            speak('hold on a sec sir')
            os.system('rundl132.exe powrprof.dl1,SetSuspendState 0,1,0')

        elif "write a note" in query:
            speak("What should i write, sir")
            note = takeCommand()
            file = open('jarvis.txt', 'w')
            speak("Sir, Should i include date and time")
            snfm = takeCommand()
            if 'yes' in snfm or 'sure' in snfm:
                strTime = datetime.datetime.now().strftime("%I:%M %p")
                file.write(strTime)
                file.write(" :- ")
                file.write(note)
            else:
                file.write(note)

        elif "show note" in query:
            speak("Showing Notes")
            file = open("jarvis.txt", "r")
            print(file.read())
            speak(file.read(6))

        elif "will you be my gf" in query or "will you be my bf" in query:
            speak("I'm not sure about, may be you should give me some time")

        elif 'no jarvis' or 'go to sleep' in query:
            speak('thank you for using me sir, have a good day!')
            sys.exit()

        elif "i love you" in query:
            speak("love you too sir")

        elif 'the window':
            speak('switching windows sir')
            pyautogui.keyDown("alt")
            pyautogui.press("tab")
            time.sleep(1)
            pyautogui.keyUp("alt")

        elif 'news' or 'headlines' in query:
            speak('please wait sir, fetching the latest news')
            news()



        speak("sir, do you have any other work")
