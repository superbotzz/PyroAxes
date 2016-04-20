package me.veryawkwardperla;

import java.util.logging.Logger;
import org.bukkit.Bukkit;
import org.bukkit.Server;
import org.bukkit.command.*;
import org.bukkit.entity.Player;
import org.bukkit.event.Listener;
import org.bukkit.inventory.ItemStack;
import org.bukkit.inventory.PlayerInventory;
import org.bukkit.permissions.Permission;
import org.bukkit.plugin.PluginManager;
import org.bukkit.plugin.java.JavaPlugin;

// Referenced classes of package me.veryawkwardperla:
//            PyroListener, PyroItem

public class PyroAxe extends JavaPlugin
    implements Listener {

    public PyroAxe() {
        pyroCmd = new Permission("pyroaxe.make");
    }

    public static PyroAxe getInstance() {
        return instance;
    }

    public void onEnable() {
        getLogger().info("#  PyroAxe coded by: Joel  #");
        getLogger().info("#  Join my friends server! Overloadpvp.serv.nu! #");
        instance = this;
        PyroListener pyrolistener = new PyroListener(this);
        PyroItem pyroitem = new PyroItem(this);
        Bukkit.getServer().getPluginManager().registerEvents(this, this);
        PluginManager pm = getServer().getPluginManager();
        pm.addPermission(pyroCmd);
    }

    public void onDisable() {
        getLogger().info("#  PyroAxe coded by: Joel  #");
        getLogger().info("#  Join my friends server! Overloadpvp.serv.nu! #");
    }

    public boolean onCommand(CommandSender sender, Command cmd, String label, String args[]) {
        if(cmd.getName().equalsIgnoreCase("pyroaxe")) {
            if(sender instanceof ConsoleCommandSender)
                return true;
            if(!sender.hasPermission("pyroaxe.make")) {
                return true;
            } else {
                Player p = (Player)sender;
                p.getInventory().addItem(new ItemStack[] {
                    PyroItem.makeAxe()
                });
                return true;
            }
        } else {
            return false;
        }
    }

    private static PyroAxe instance;
    public Permission pyroCmd;
}
