                                     _    _ _______ __  __ _         _____ _           _   
                                    | |  | |__   __|  \/  | |       / ____| |         | |  
                                    | |__| |  | |  | \  / | |      | |    | |__   __ _| |_ 
                                    |  __  |  | |  | |\/| | |      | |    | '_ \ / _` | __|
                                    | |  | |  | |  | |  | | |____  | |____| | | | (_| | |_ 
                                    |_|  |_|  |_|  |_|  |_|______|  \_____|_| |_|\__,_|\__|
                                                        


# What is it?

HTML Chat is a simple chat client developed by me solo.
It also uses Firebase to store rooms.
There is chat, and private chat rooms (password or passwordless).

---

# How do I use it?

Click on the link in the repo description!

---

# Features

• #general | Chat

• Private chat rooms, all rooms shown on sidebar, you can set a password for the room

• Nicknames (stored anonymously)

• Room Lock

• AI

• Images

• Link support

• Currently typing

• Stickers

• GIF's

And more!
---

# How do I make a client?

Yes, you read that right, you can make your own HTML chat client. And here is how.
But first some info. there is two types of HTML Chat clients, Modified Clients, and Clients. A Modified Client, is when you just edit the styling of the main client (adding animations, editing colors, fonts, etc.), but you don't change the Database. A Client, is when you change the Firebase database, and you can also edit stuff. Now, here is how you make one.

---

## Modified Client

Clone the GitHub repo:

```git clone https://github.com/LGYTreal/html-chat.git```

And open index.html

Now, find ```<style>```, and edit it.

That's all for Modified Client, just make sure to credit me! And you can change more, just not the database.

---

## Client

This one is WAY more complicated!

Clone the GitHub repo:

```git clone https://github.com/LGYTreal/html-chat.git```

And open index.html

Find the following:
```
const firebaseConfig = {
        apiKey: "",
        authDomain: "",
        projectId: "",
        storageBucket: "",
        messagingSenderId: "",
        appId: "",
        databaseURL: ""
    };
```
    Now go to https://firebase.google.com. Sign in, create a new Firebase project, add and configure your app. Then, copy your config in SDK setup, and replace the current config in index.html with yours. Now, in Firebase, add Authentication, and select anonymous, and add it. Next up, set up realtime database. Just press get started, and configure it, and your done! You can also change the client's styling.

    Oh and one more thing, go into your realtime database, find rules, and paste this:
    ```
    {
  "rules": {
    ".read": "auth != null",
    "rooms": {
      "$room_id": {
        ".write": "auth != null && (!data.exists() || data.child('owner').val() === auth.uid || root.child('admins').child(auth.uid).exists())"
      }
    },
    "messages": {
      "$room_id": {
        "$msg_id": {
          ".write": "auth != null && (!data.exists() || data.child('userId').val() === auth.uid || root.child('admins').child(auth.uid).exists())"
        }
      }
    },
    "admins": {
      ".read": "auth != null",
      ".write": false
    },
    "admin_config": {
      ".read": "auth != null",
      ".write": false
    }
  }
}
```



## That is all for creating a client!

# Thanks for using HTML Chat!

> Note - This README was NOT made with ai! I spent 10 minutes typing this lmao
