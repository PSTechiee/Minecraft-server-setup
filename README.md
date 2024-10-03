## NOTE

All the steps have been tried on GitHub Codespaces, so they should work.

### Important Commands and Things to Know

- **Windows Subsystem for Linux (WSL)**: Ensure WSL is installed on your machine if you are using a Windows system (all steps require a Linux machine).

- **Reverse Proxy**: We will use [Localtonet](https://localtonet.com/) to get the IP address and port number of our server.

- **Cross-Platform Play**: If you want both Bedrock and Java players to play together, download the following plugins:
  - [Geyser-Spigot.jar](https://geysermc.org/download) (for Paper)
  - [Floodgate-Spigot.jar](https://geysermc.org/download?project=floodgate)

- **Temporary Email**: The best site to create a temporary email is [Eztempmail](https://www.eztempmail.com/).

### Step-by-Step Minecraft Server Installation

#### Commands for Setup

1. **Create a Folder**: Create a folder named `mc_server` in your root directory.

2. **Update and Upgrade**:
   ```sh
   sudo -s
   apt update && apt upgrade -y
   ```

3. **Download Localtonet**:
   ```sh
   wget https://localtonet.com/download/localtonet-linux-x64.zip
   ```

4. **Extract Localtonet**:
   ```sh
   unzip localtonet-linux-x64.zip
   ```
   (Remember to move the extracted `localtonet` file to the root folder.)

5. **Grant Permissions**:
   ```sh
   chmod 777 ./localtonet
   ```
   or
   ```sh
   chmod +x ./localtonet
   ```

6. **Navigate to `mc_server` Directory**:
   ```sh
   cd mc_server
   ```

7. **Install Java**:
   ```sh
   apt install openjdk-21-jre
   ```

8. **Start Minecraft Server**:
   ```sh
   java -Xmx14G -Xms2G -jar server.jar nogui
   ```

9. **Accept EULA**:
   ```sh
   echo "eula=true" > eula.txt
   ```

10. **Start Minecraft Server Again**:
    ```sh
    java -Xmx14G -Xms2G -jar server.jar nogui
    ```

11. **Get IP and Port (Free, Limited-Time)**:
    ```sh
    ./localtonet authtoken PASTE_HERE_COPIED_AUTHTOKEN
    ```
    - Log in to [Localtonet](https://localtonet.com/).
    - Go to "My Tunnel," select the TCP-UDP option, assign a port number (default Minecraft port: 25565), and select the server location (e.g., India).
    - Create the tunnel and keep the IP as `127.0.0.1`.

12. **Start Localtonet**:
    ```sh
    ./localtonet authtoken PASTE_HERE_COPIED_AUTHTOKEN
    ```
    (Copy the AuthToken from the dashboard and paste it.)

13. **Open a New Terminal in the Same Directory**:
    ```sh
    java -Xmx14G -Xms2G -jar server.jar nogui
    ```

14. **Use the Provided IP and Port to Connect to Your Minecraft Server**.

### Important Links

- [Create a temporary email using this website](https://www.eztempmail.com/)
- [For setting up a Minecraft server, take guidance from this website](https://github.com/matiassingers/awesome-readme)

## Things to remember:
1. Remember:

localtonet.com - tunnel - TCP/UDP and from there start the server you created (under the action button, click the ⏸ button).

2. After starting the server, drag the following two plugins into the `plugins` folder and restart the server:
   - [Geyser-Spigot.jar](https://geysermc.org/download) (for Paper)
   - [Floodgate-Spigot.jar](https://geysermc.org/download?project=floodgate)

   After restarting, all the required files will be installed. You will get new folders, including `Geyser-Spigot` (in my case, I selected Spigot for Paper, so the folder will be named accordingly depending on your version).

   You will need to make changes in the configuration files within the `Geyser-Spigot` folder. Open the `Geyser-Spigot` folder, go to the `config.yml` file, and replace the port accordingly. Try using the IP/URL and port or client port.

3. In mc_server folder, go to `server.properties` and find `online-mode` make it online-mode=false (Additionally you can also customise gamemode and pvp)
