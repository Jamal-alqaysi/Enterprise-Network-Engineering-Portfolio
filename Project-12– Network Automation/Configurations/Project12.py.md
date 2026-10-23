
```
from netmiko import ConnectHandler
from getpass import getpass

devices = [
    {
        "device_type": "cisco_ios",
        "host": "192.168.99.1",
        "username": "admin"
    },
    {
        "device_type": "cisco_ios",
        "host": "10.0.0.9",
        "username": "admin"
    }
]

for device in devices:
    print(device["host"])
    device["password"] = getpass("SSH Password: ")

    connection = None

    try:
        connection = ConnectHandler(**device)
        print("SSH Connected:", connection.is_alive())

        interface_output = connection.send_command_timing(
            "show ip interface brief"
        )
        print(interface_output)

    except Exception as error:
        print("Automation Failed:", error)

    finally:
        if connection is not None:
            connection.disconnect()
```
