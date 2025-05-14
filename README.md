# Flag Hunters - PICOCTF

## Challenge Overview :

### Challenge Name: Flag Hunters
### Difficulty: Easy
### Categories: Reverse Engineering, picoCTF 2025, browser_webshell_solvable
### Description: The challenge involves analyzing lyrics where a hidden refrain is mentioned, which doesn't print by default. The goal is to figure out how to get this hidden refrain, as it might contain the flag. 
 * The source code is available for download, and there's a hint to connect via netcat to verbal-sleep.picoctf.net on port 50812.

![Screenshot 2025-05-14 105829](https://github.com/user-attachments/assets/9dd04587-f794-4a9b-becc-a7cdda6d712a)

![Screenshot 2025-05-14 105649](https://github.com/user-attachments/assets/211e2285-c9e0-40c4-b74e-7eadf69ff089)

## Downloaded Files :

### lyric-reader.py: 
 * This is probably the source code mentioned in the challenge description. It's a Python script.
   
![Screenshot 2025-05-14 105747](https://github.com/user-attachments/assets/7400afff-6262-4fe5-a0ed-f3b9464859d3)

![Screenshot 2025-05-14 105946](https://github.com/user-attachments/assets/89b34cff-e157-42e8-974f-bdbe262b9de1)

## Source Code Analysis :
### Finding the Hidden Part ('REFRAIN'):
 * If a line starts with the word 'REFRAIN', the script does something special. It takes the part of the line that comes after the words 'RETURN '.
 * It then adds a number to this part (based on a counter called lip). This combined piece of text is stored under the label 'refrain_return'. This looks like where the hidden flag is manipulated or stored.

### Interacting with the User ('CROWD'):
 * The script also looks for lines that start with 'CROWD: '.
 * When it finds such a line, it asks the user to type something (this is what input('Crowd: ') does).
 * It then checks if what the user typed exactly matches the text that comes after 'CROWD: ' in the lyric line.
 * If the user's input matches, it stores the user's input in a specific place (related to the counter lip). This suggests that interacting with the program by correctly responding to the "Crowd" prompts might be necessary.

![Screenshot 2025-05-14 110031](https://github.com/user-attachments/assets/0830147d-d9ab-4d83-bf3f-2067daf60c63)

## Netcat Interaction :
 * The user connected to verbal-sleep.picoctf.net on port 50812 using the nc command.
 * The server output shows lyrics, including lines like "Command line wizards, we're starting it right...", "We're flag hunters in the ether, lighting up the grid...", and "Crowd: ;RETURN 0".

![Screenshot 2025-05-14 110335](https://github.com/user-attachments/assets/1fd3f4ab-328f-4a7b-af91-8283410314cd)

## Flag Found:
 * The hidden refrain within the lyrics contained the flag: picoCTF{70637h3r_f0r3v3r_62666df2}. This flag was successfully submitted to the picoCTF platform to solve the challenge.

![Screenshot 2025-05-14 110349](https://github.com/user-attachments/assets/c339cd67-ad9a-4136-8228-1cf92f67748a)

## Summary:

### The user successfully solved the "Flag Hunters" challenge by:
 * Downloading the provided source code (lyric-reader.py).
 * Likely analyzing the Python script to understand how it processes lyrics and the significance of the "REFRAIN" and "CROWD" sections.
 * Connecting to the netcat service (verbal-sleep.picoctf.net 50812).
 * Interacting with the service, possibly by providing input based on the "CROWD" prompts.
 * Identifying the hidden refrain which contained the flag: picoCTF{70637h3r_f0r3v3r_62666df2}.
 * Submitting the flag to the picoCTF platform.

![Screenshot 2025-05-14 110418](https://github.com/user-attachments/assets/0981d755-c95d-4b35-a41d-219c270b873a)

