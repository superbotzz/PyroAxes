package me.veryawkwardperla;

import java.util.ArrayList;
import org.bukkit.*;
import org.bukkit.enchantments.Enchantment;
import org.bukkit.event.Listener;
import org.bukkit.inventory.ItemStack;
import org.bukkit.inventory.meta.ItemMeta;
import org.bukkit.plugin.PluginManager;

// Referenced classes of package me.veryawkwareperla:
//            PyroAxe

public class PyroItem
    implements Listener {

    public PyroItem(PyroAxe plugin) {
        plugin.getServer().getPluginManager().registerEvents(this, plugin);
    }

    public static ItemStack makeAxe() {
        ItemStack item = new ItemStack(Material.DIAMOND_AXE);
        ItemMeta itemMeta = item.getItemMeta();
        itemMeta.setDisplayName((new StringBuilder()).append(ChatColor.DARK_RED).append("Pyro Axe").toString());
        ArrayList itemLore = new ArrayList();
        itemLore.add((new StringBuilder()).append(ChatColor.DARK_RED).append("I Come From The Iron Hills.").toString());
        itemMeta.addEnchant(Enchantment.DAMAGE_ALL, 5, true);
        itemMeta.addEnchant(Enchantment.FIRE_ASPECT, 2, true);
        itemMeta.setLore(itemLore);
        item.setItemMeta(itemMeta);
        return item;
    }
}
