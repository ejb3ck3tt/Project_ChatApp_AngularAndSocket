# Web Chat-App

This repository contains a real-time web chat application implemented using `Node.js`, `Express`, `Socket.IO`, `RxJS` and `Angular`. It contains users and admins with groups and channels.

You can find the extra [documentation here](chat_app_documentation.pdf).

## Status

This application currently holds the following functionality:  

### Group Admin

* Create groups
* Create channels within groups
* Create/invite users to a channel
* Remove groups, channels and users from channels

### Super Admin

* Assign users with Group admin or Super admin roles
* Also has group admin privileges
* Can remove users from the chat application

### Users

* Identified by username
* One persistent user called __Super__ who is a Super admin
* Can assign an email address to itself

## Git Repository Layout

The root directory of the repository contains the `README.md` file and the files necessary for `Node.js.` All of the `Node.js` logic is contained in a single file called `server.js`. The root directory also contains a sub-directory called `chat-app` which contains all the files necessary for Angular.  
  
The `chat-app` directory contains all the auto-generated files. The project's files are contained inside the `src/app` sub-directory. In here, there are four directories, each containing its respective Angular Component. It also contains TypeScript files for Angular services.  
  
The approach of using Git in this project was to commit changes at any time a new functionality was added. An example would be a task to add functionality for a user. The task would be broken down into sub-tasks and when a sub-task has been implemented, a commit would be added to Git.  

The root directory of the Git repository contains an `images` directory. This directory is where the uploaded images are saved and statically served back to the user.
  
#### Login

The Login component allows a user to log in. Any user can type any username and log in. User data will persist after they log out. If a username does not exist in the system, the server will seamlessly create the user in the background.

### Services

#### Image

The image service handles the upload of images to the server. It contains a function that performs a POST request to the server.

#### Socket

The socket service handles the web socket communications in real-time. The sockets contain three rooms:

* join
* leave
* new-message

Join notifies the server that the user has joined the channel. Leave notifies the server that the user has left the channel. New-message is used for new messages, which may be text or images.

The server responds in the message room, broadcasting only to the room which it originally received from.

#### Users

The users service contains the requests for all dashboard, groups and channel data manipulation to and from the server.

## MongoDB

### Collections

* users - Each document is the data of the users. This includes their username, their admins status, their groups and channels.
* messages - Each document is a message that was sent in a channel.

### Modules Used

* `npm init`
* `npm install express`
* `npm install socket.io`
* `npm install body-parser`
* `npm install @types/socket.io-client'`
* `npm install formidable`

*** Ensure you navigate to the chat-app and run 'npm install' in order to update the files in the node_modules ***
