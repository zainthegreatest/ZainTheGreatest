# Hey, I’m Zain 👋

🎮 **Minecraft Developer & Discord Bot Developer**
💼 **2+ Years of Experience** building community utilities, managing servers, and optimizing performance.

I build custom tools that make managing Minecraft networks easier. I focus on writing clean Discord bots for staff teams, configuring server files correctly, and lowering lag so competitive players get a smooth experience.

---

## 🧠 Technical Stack

### 🐍 Software Development & Scripting
![Python](https://img.shields.io/badge/Python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Discord.py](https://img.shields.io/badge/discord.py-5865F2?style=for-the-badge&logo=discord&logoColor=white)
![Java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)

### ⚙️ Server & System Tweaks
![Minecraft](https://img.shields.io/badge/Minecraft-613E30?style=for-the-badge&logo=minecraft&logoColor=white)
![Spigot](https://img.shields.io/badge/Spigot-F25E22?style=for-the-badge&logo=spigot&logoColor=white)
![Windows](https://img.shields.io/badge/Windows-0078D4?style=for-the-badge&logo=windows&logoColor=white)

---

## 🚀 Projects

### ⚙️ Minecraft Optimization & Setup
* **Server Software:** Experienced with Spigot, Paper, and running optimized setups for competitive networks.
* **Version Optimization:** I specialize in getting older versions like 1.8.9 to run smoothly on modern Java runtimes for peak performance.
* **Player Experience Tuning:** Adjusting game configurations to ensure low input latency and stable hit registration for competitive PvP modes like Bedwars and Sumo.
* **Lag Reduction:** I configure server-side files to eliminate game lag and stuttering, tuning resource usage so the server stays at a stable 20 TPS even during heavy fights.
* **Low-End Hardware Tweaks:** I have hands-on experience optimizing game performance and system setups to cut down on background processes, ensuring players get the maximum FPS possible.

### ⚙️ Discord Bot Development
* **ForgedMC System Bot:** Developed a custom, feature-rich infrastructure bot using Python. It handles custom support tickets, server moderation, anti-spam, anti-raid protection, and a music playback system.
* **Cracked Tier Tests Automation:** Deployed an automated system that manages the entire tier testing workflow. It automatically handles support tickets, tier testing queues, and custom user suggestions, which massively cut down on manual staff work.
* **Tiers SMP Management:** Managed the technical backend setup for the Tiers SMP project. I drafted the official server rules, designed the custom welcome system, and set up all the Discord branding to make the community look professional from day one.

---

## 💻 Code Example: How I Handle Tickets

Anyone can say they code, so here is a quick look at how I actually write my Discord buttons in Python using `discord.py`. This logic checks if a user already has an active ticket open so they can't spam the server with channels:

```python
class TicketButton(discord.ui.View):
    def __init__(self):
        super().__init__(timeout=None) # Keeps the button working even if the bot restarts

    @discord.ui.button(label="Open Ticket", style=discord.ButtonStyle.green, custom_id="ticket_btn")
    async def make_ticket(self, interaction: discord.Interaction, button: discord.ui.Button):
        
        # Check if the player already has a channel open
        existing = discord.utils.get(interaction.guild.channels, name=f"ticket-{interaction.user.name.lower()}")
        if existing:
            return await interaction.response.send_message("You already have a ticket open!", ephemeral=True)
        
        # Set up permissions so only staff and the player can see the channel
        perms = {
            interaction.guild.default_role: discord.PermissionOverwrite(read_messages=False),
            interaction.user: discord.PermissionOverwrite(read_messages=True, send_messages=True)
        }
        
        # Create the private channel
        new_channel = await interaction.guild.create_text_channel(name=f"ticket-{interaction.user.name}", overwrites=perms)
        await interaction.response.send_message(f"Ticket created: {new_channel.mention}", ephemeral=True)


        ---
