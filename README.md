# Logic-Bomb
import time
import hashlib
import os
import platform


def shutdown():
    system = platform.system()
    if system == "Windows":
        os.system("shutdown /s /t 0")
    else:
        os.system("shutdown -h now")


def check_condition():
    # Replace 'ctf_secret' with your desired secret code.
    secret = "ctf_secret"
    user_input = input("Enter the secret code: ")

    # Using SHA-256 for a bit of extra challenge.
    if hashlib.sha256(user_input.encode()).hexdigest() == hashlib.sha256(secret.encode()).hexdigest():
        print("Correct code entered. Shutting down the system...")
        shutdown()
    else:
        print("Access Denied!")


print("System Running... (waiting for input)")
time.sleep(5)  # Simulate a delay before accepting input
check_condition()
