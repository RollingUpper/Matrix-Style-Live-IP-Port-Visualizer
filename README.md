# Matrix-Style-Live-IP-Port-Visualizer
A Python-based live network visualizer that captures real-time IP:PORT traffic using tshark and renders it as falling text streams in the terminal — like the Matrix rain effect.

This tool listens to a network interface, extracts destination IP addresses and port numbers from TCP/UDP packets, and dynamically displays them in a color-coded terminal animation. Optionally, it can fill unused columns with random numeric streams for extra Matrix aesthetic.


Features

    Live capture of destination IP and port numbers via tshark

    Dynamic Matrix-style falling streams per terminal column

    Adjustable stream speed, matrix size, and random filler settings

    Real-time key controls:

        p → pause/resume animation

        q → quit program

    Safe multithreaded rendering with live screen refreshes

    Defensive parsing and validation of packet data

📐 Configuration Parameters

You can tweak these variables near the top of the script:
Variable	Purpose	Example Value
COLS	Number of columns in the Matrix display	30
ROWS	Number of rows (height) of the Matrix display	30
GREEN	ANSI color code for active characters	'\033[32m'
RESET	ANSI code to reset terminal text formatting	'\033[0m'
USE_RANDOM_FILLER	Enable/disable random filler streams in unused columns	False (or True)
stream['speed']	Per-column random falling speed range for active streams	0.1 - 0.3 (set in code)
process = subprocess.Popen(...)	Modify the tshark capture parameters (like interface, fields)	'-i wlan0' or '-i eth0'
📖 Usage

    Install tshark if you haven’t:

sudo apt-get install tshark

Run the script:

    sudo python3 matrix_rain_capture.py

    (You’ll likely need sudo to capture network packets.)

🎛️ Key Bindings

    p → Pause/resume animation

    q → Quit program

🔒 Notes

    Requires tshark in PATH

    Assumes your network interface is wlan0 — update in the subprocess.Popen() call if needed

    Designed for Unix-like systems (uses termios and fcntl)

📌 Known Limitations

    No Windows support (due to Unix-specific terminal control)

    Will hang if tshark isn’t installed or permissions are denied

    No packet content inspection — just destination IP and ports

📈 Ideas for Future Features

    Customizable colors and speeds via CLI arguments

    Support for IPv6 addresses

    Packet count statistics overlay

    Export logs to file

    Optional stream density control

