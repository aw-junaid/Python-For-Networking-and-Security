In Python, you can use the `subprocess` module to execute system commands, including the `ping` command. Here's an example of how you can use Python to run the `ping` command:

```python
import subprocess

def ping(host):
    try:
        # Run the ping command with the specified host
        result = subprocess.run(['ping', '-c', '4', host], stdout=subprocess.PIPE, stderr=subprocess.PIPE, text=True, timeout=5)

        # Check if the command was successful (return code 0)
        if result.returncode == 0:
            print(f"Ping to {host} successful:\n{result.stdout}")
        else:
            print(f"Ping to {host} failed:\n{result.stderr}")

    except subprocess.TimeoutExpired:
        print(f"Timeout: Unable to ping {host}")

# Example usage
ping('awjunaid.com')
```

In this example:
- The `subprocess.run` function is used to run the `ping` command with the specified host (`example.com` in this case).
- The `-c 4` option specifies to send four packets.
- The `stdout=subprocess.PIPE` and `stderr=subprocess.PIPE` parameters capture the standard output and standard error of the command.
- The `text=True` parameter ensures that the output is returned as a string (assuming you're using Python 3.7 or later).
- The `timeout=5` parameter sets a timeout for the command execution (in seconds).

This script will attempt to ping the specified host, and it will print the output if the ping is successful. If the ping fails or if there's a timeout, appropriate messages will be printed.
