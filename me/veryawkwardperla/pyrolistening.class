package me.veryawkwardperla;

import java.util.Iterator;
import java.util.List;
import org.bukkit.*;
import org.bukkit.entity.Player;
import org.bukkit.event.Listener;
import org.bukkit.event.entity.EntityDamageByEntityEvent;
import org.bukkit.inventory.ItemStack;
import org.bukkit.inventory.meta.ItemMeta;
import org.bukkit.plugin.PluginManager;

// Referenced classes of package me.veryawkwardperla:
//            PyroAxe

public class PyroListener
    implements Listener {

    public PyroListener(PyroAxe plugin) {
        plugin.getServer().getPluginManager().registerEvents(this, plugin);
    }

    public void onDamage(EntityDamageByEntityEvent e) {
        if(!(e.getDamager() instanceof Player))
            return;
        Player p = (Player)e.getDamager();
        ItemStack item = p.getItemInHand();
        if(item.hasItemMeta() && item.getItemMeta().hasLore()) {
            for(Iterator iterator = item.getItemMeta().getLore().iterator(); iterator.hasNext();) {
                String s = (String)iterator.next();
                if(ChatColor.stripColor(s).contains("Hills")) {
                    p.playSound(p.getLocation(), Sound.ANVIL_BREAK, 1.0F, 1.0F);
                    p.playSound(p.getLocation(), Sound.ANVIL_BREAK, 1.0F, 1.0F);
                    e.setDamage(e.getDamage() * 3D);
                }
            }

        }
    }
}
