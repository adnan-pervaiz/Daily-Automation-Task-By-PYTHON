# Daily-Automation-Task-By-PYTHON

Generating a QR code for the data

import qrcode

def generate_qr_code(data):

    qr = qrcode.QRCode(version=1, box_size=10, border=5)
    
    qr.add_data(data)
    
    qr.make(fit=True)
    
    img = qr.make_image(fill_color="black", back_color="white")
    
    img.save("qr_code.png")
    
    print("QR code generated!")
    

data = 'Data to be encoded'

generate_qr_code(data)


""""Text to Speech"""""

from gtts import gTTS
import os

def say(text):
  tts = gTTS(text=text, lang='en')
  tts.save("geeks.mp3")

  os.system("mpg321 geeks.mp3")
  
say("Hello, Automation!")


"""Convert jpg to png (and vice-versa)"""

from PIL import Image

# To convert the Image From JPG to PNG
def jpg_to_png(IMG_PATH):
  img = Image.open(IMG_PATH).convert('RGB')
  img.save("Image_1.png", "PNG")
 
# To convert the Image From PNG to JPG
def png_to_img(PNG_PATH):
  img = Image.open(PNG_PATH).convert('RGB')
  img.save("Image_1.jpg", "JPEG")


"""GeoCoding and Reverse GeoCoding"""

from geopy.geocoders import Nominatim

def print_data(location):
  print("Address: ",location.address)
  print("Latitude: ", location.latitude)
  print("Longitude: ",location.longitude)

geolocator = Nominatim(user_agent="gfg_app")

def geocoding(address):
  location = geolocator.geocode(address)
  print_data(location)

def rev_geocoding(latitude_longitude):
  location = geolocator.reverse(latitude_longitude)
  print_data(location)

geocoding("Oman,Muscat")
rev_geocoding("51.509669, 11.376294")



"""Sending Emails"""

import smtplib

def send_email(sender, receiver, password, subject, message):

    server = smtplib.SMTP('smtp.gmail.com', 587)
    
    server.ehlo()
    
    server.starttls()
    
    server.ehlo()
    
    server.login(sender, password)
    
    message = f"Subject: {subject}\n\n{message}"
    
    server.sendmail(sender, receiver, message)
    
    print("Email sent!")
    
    server.quit()

sender = "SENDER_ADDRESS"

receiver = "RECEIVER_ADDRESS"

password = "APP_PASSWORD"

subject = "Hello From GFG"

message = "Message Body"






