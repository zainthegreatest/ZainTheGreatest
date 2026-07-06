# Hey, I’m Zain 👋

🎮 **Discord Developer & Minecraft Developer.**
🛠️ Specialized Python development, backend configuration, and system optimizations.
💼 **2+ Years of Experience** developing community utilities 

🎮 **Software Developer & Systems Administrator**
🛠️ Specialized in asynchronous Python development, backend automation, and low-latency network infrastructure.
💼 **2+ Years of Experience** developing community utilities and managing performance enviroments.

---

## 🧠 Technical Stack

### 🐍 Software Development & Scripting
![Python](https://img.shields.io/badge/Python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Discord.py](https://img.shields.io/badge/discord.py-5865F2?style=for-the-badge&logo=discord&logoColor=white)
![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)

### ⚙️ Systems & Infrastructure Optimization
![Minecraft](https://img.shields.io/badge/Minecraft-613E30?style=for-the-badge&logo=minecraft&logoColor=white)
![Linux / Windows Server](https://img.shields.io/badge/Server_OS-0078D4?style=for-the-badge&logo=windows&logoColor=white)

---

## 🚀 Projects

## ⚙️ Minecraft 
* **Server Software:** Spigot, Paper, and running optimized setups for competitive networks.
* **Version Optimization:** Experienced in getting older versions like 1.8.9 to run smoothly on modern Java runtimes for peak performance.
* **Player Experience Tuning:** Adjusting game settings to ensure low input latency and stable hit registration for competitive PvP modes like Bedwars and Sumo.

### ⚡ Lag Reduction & Game Performance
* **Fixing Tick Spikes:** I configure server-side files to eliminate game lag and stuttering, specifically tuning resource usage so the server stays at a stable 20 TPS even during heavy fights.
* **Low-End Hardware Tweaks:** I have hands on experience optimizing game performance and system setups for players on lower-end computers, ensuring they get the absolute maximum FPS and zero input delay.

### ⚡ Systems Optimization & JVM Performance.
* **Runtime Tuning:** Developed and tested optimized Java Virtual Machine (JVM) flags to maximize garbage collection efficiency and eliminate server-side stuttring.
* **Resource Optimization:** Applied kernel-level OS tweaks to minimize system background processing, directly improving input latency and network throughput for competitive environments.

### ⚙️ Discord
*I have developed a custom most powerful discord bot for ForgedMC*
* **Development:** I have developed a custom bot for ForgedMC.
* **Functions:** Custom Tickets, powerful Automod, anti-spam, anti-raid, moderation and music bot. 

### 📊 Cracked Tier Tests 
*I've deployed a custom tier testing for Cracked Tier Tests & which manages all the system automatically.*
* **Logic & Data:** It inclues Support Tickets, Tier testing tickets and custom suggestions.
* **Impact:** Reduced staff administration overhead.

### ⚔️ Tiers SMP Setup & Management
I managed the backend setup for the Tiers SMP project. 
* **What I did:** Wrote the official server rules, designed the custom welcome system, and set up all the Discord branding so the server looked highly professional from day one.

## 💻 Code Example: How I handle Tickets

Anyone can say they code so here is a quick look at how I actually write my Discord buttons in Python. 

```python
class TicketButton(discord.ui.View):
    def __init__(self):
        super().__init__(timeout=None) 

    @discord.ui.button(label="Open Ticket", style=discord.ButtonStyle.green, custom_id="ticket_btn")
    async def make_ticket(self, interaction: discord.Interaction, button: discord.ui.Button):
        
        existing = discord.utils.get(interaction.guild.channels, name=f"ticket-{interaction.user.name.lower()}")
        if existing:
            return await interaction.response.send_message("You already have a ticket open!", ephemeral=True)
        
        # Set up permissions so only staff and the player can see the channel
        perms = {
            interaction.guild.default_role: discord.PermissionOverwrite(read_messages=False),
            interaction.user: discord.PermissionOverwrite(read_messages=True, send_messages=True)
        }
        
        # Make the channel
        new_channel = await interaction.guild.create_text_channel(name=f"ticket-{interaction.user.name}", overwrites=perms)
        await interaction.response.send_message(f"Ticket created: {new_channel.mention}", ephemeral=True)

---


