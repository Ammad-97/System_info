# System_info

import os
import platform
import subprocess

def get_uptime():
    try:
        with open("/proc/uptime", "r") as f:
            uptime_seconds = float(f.readline().split()[0])
            hours = int(uptime_seconds // 3600)
            minutes = int((uptime_seconds % 3600) // 60)
            return f"{hours} hours, {minutes} minutes"
    except Exception as e:
        return f"Could not determine uptime: {e}"

def main():
    print("=== System Information ===")
    print(f"User: {os.getlogin()}")
    print(f"OS: {platform.system()} {platform.release()} ({platform.version()})")
    print(f"Processor: {platform.processor()}")
    print(f"Uptime: {get_uptime()}")

if __name__ == "__main__":
    main()
