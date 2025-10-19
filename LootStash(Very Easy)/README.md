Name: LootStash
Type: Reversing CTF
Time taken: ~2hr

Downloaded the files from CTF.

Unzipped the file: 
File -> Stash
Stash was of ELF type.

Created a new project in Ghidra and and opened the file using the CodeBrowser and analysed it:
![alt text](image.png)

![alt text](image-1.png)

In CodeBrowser goto Symbol Tree -> Functions -> main
This will open up the decompiled main function.

![alt text](image-2.png)

Here we can see that the program is actually fluff that just prints 5 dots(.) in 1 second interval

![alt text](image-3.png)

This is where our focus should be. It says that whatever the flag is, it has to be a string and it is stored in gear array.
But instead of searching through the array, its easier to directly find the string value in the file.

We can try executing the file but it shows "Permission Denied"
So we have another option since we require a string, we can just use "strings" since it's a ELF file.

![alt text](image-4.png)

Run : strings stash
It returns all the string values in the stash file.

Continuing upon this we can search for a specific FLAG.

![alt text](image-5.png)

Run: strings stash | grep HTB
It provides us with the FLAG.

FLAG: HTB{n33dl3_1n_a_l00t_stack}