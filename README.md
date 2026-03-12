# SOC-Threat-Detection-System-
A Python-based SOC Threat Detection System that analyzes security logs and detects suspicious activities such as brute-force attacks, root login attempts, and malware indicators. This project simulates a basic Security Operations Center (SOC) monitoring environment.
# SOC Threat Detection System

A Python-based cybersecurity project that simulates a basic Security Operations Center (SOC) monitoring tool.

The system analyzes security logs and detects suspicious activities such as:

- Brute force login attempts
- Root login access
- Malware related activity

## Features

- Log monitoring
- Security alert generation
- Basic threat detection
- SOC monitoring simulation

## Technologies

Python

## How to Run

1. Clone the repository
2. Navigate to project directory
3. Run the script

python threat_monitor.py

## Example Output

[ALERT] Brute Force Attempt: Failed password for admin from 192.168.1.7


def analyze_logs():
    """
    Reads logs from security_logs.txt and generates alerts for suspicious activity.
    """
    try:
        with open("security_logs.txt", "r") as file:
            for line in file:

                # Detect brute-force attempts
                if "Failed password" in line:
                    create_alert("Brute Force Attempt", line)

                # Detect root logins
                elif "root login" in line:
                    create_alert("Root Access Alert", line)

                # Detect malware activity
                elif "malware" in line.lower():
                    create_alert("Malware Activity", line)
    except FileNotFoundError:
        print("security_logs.txt not found. Please add your log file.")


def create_alert(alert_type, log):
    """
    Writes alerts to alerts.txt and prints to console.
    """
    alert_message = f"[ALERT] {alert_type}: {log}"
    print(alert_message)

    with open("alerts.txt", "a") as alert_file:
        alert_file.write(alert_message)


def main():
    print("SOC Threat Monitoring Started...\n")
    analyze_logs()


if __name__ == "__main__":
    main()

