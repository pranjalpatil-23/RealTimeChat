# Flask Socket.IO Chatroom

A real-time chatroom application built with **Flask** and **Flask-SocketIO**. Users can join predefined rooms, send messages, and see live user counts.

---

## Features

* Predefined chat rooms: `general`, `tech`, `sports`, `music`, `gaming`
* Real-time messaging using WebSockets
* Room user counts and live updates
* System notifications when users join or leave

---

## Prerequisites

* Python 3.7 or higher
* `pip` package manager

---

## Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/your-username/flask-socketio-chatroom.git
   cd flask-socketio-chatroom
   ```

2. **Create and activate a virtual environment**

   ```bash
   python3 -m venv venv
   source venv/bin/activate      # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

   > **requirements.txt** should include:
   >
   > ```text
   > Flask>=2.0.0
   > Flask-SocketIO>=5.0.0
   > python-socketio>=5.0.0
   > python-engineio>=4.0.0
   > ```

---

## Configuration

The application uses a secret key for session management. You can override the default in `app.py` or set it via an environment variable:

```bash
export SECRET_KEY="your-secure-secret"
```

On Windows (PowerShell):

```powershell
$env:SECRET_KEY = "your-secure-secret"
```

---

## Running the Server

Start the Flask-SocketIO server:

```bash
python app.py
```

By default, the server listens on `0.0.0.0:5000`. You can change the host or port in the last line of `app.py`:

```python
socketio.run(app, host='0.0.0.0', port=5000, debug=True)
```

---

## Client Usage

1. Open your web client or use a Socket.IO client library.
2. Connect to `http://<server-address>:5000`.
3. Listen for events:

   * `room_list`: initial list of rooms and user counts
   * `room_update`: broadcast when room counts change
   * `join_confirm`: confirmation of successful room join
   * `system_message`: notifications of user join/leave
   * `receive_message`: incoming chat messages
4. Emit events:

   * `join_room` with payload `{ room_name: "tech", username: "Alice" }`
   * `send_message` with payload `{ text: "Hello, world!" }`

---

## Project Structure

```
├── app.py            # Main Flask-SocketIO server
├── requirements.txt  # Python dependencies
└── README.md         # This documentation file
```


