
# Combat.lua - Explanatory Documentation

This script is a utility module for handling combat and damage in Roblox.  
It is designed to be used as a ModuleScript.

# Default Configuration
- **Combat.Defaults.BaseDamage** : 10  
- **Combat.Defaults.CriticalChance** : 0.05  
- **Combat.Defaults.CriticalMultiplier** : 2  

# Event System
- Uses **ReplicatedStorage.CombatEvents** folder for RemoteEvents (Hit, Heal)  
- **GetEvent(name)** : Creates or retrieves a RemoteEvent by name

# Functions

## Combat.CalculateDamage(amount, critChance, critMultiplier)
Calculates damage, with possible critical hit.  
- **amount** : Base damage  
- **critChance** : Optional critical chance (default 0.05)  
- **critMultiplier** : Optional critical multiplier (default 2)  
Returns **final damage** and **boolean indicating critical hit**.

## Combat.DealDamage(targetHumanoid, amount, source)
Applies damage to a Humanoid.  
- **targetHumanoid** : Humanoid object  
- **amount** : Damage amount  
- **source** : Source of the damage (player or object)  
Fires **Hit event** to all clients.  
Returns **final damage** and **critical boolean**.

## Combat.Heal(targetHumanoid, amount)
Heals a Humanoid.  
- **targetHumanoid** : Humanoid object  
- **amount** : Healing amount  
Fires **Heal event** to all clients.

## Combat.Knockback(targetHumanoid, direction, strength)
Applies force to the character.  
- **direction** : Vector3 direction  
- **strength** : Optional force magnitude (default 50)

## Combat.RaycastHit(origin, direction, range, ignoreList)
Checks if a projectile or ray hits a humanoid.  
- **origin** : Vector3 start position  
- **direction** : Vector3 direction  
- **range** : Ray range  
- **ignoreList** : Optional table of instances to ignore  
Returns **Humanoid hit** and **hit position**.

## Combat.ShootProjectile(projectileTemplate, origin, direction, speed, damage, source)
Creates a projectile that damages humanoids on touch.  
- **projectileTemplate** : BasePart template  
- **origin** : Vector3 start position  
- **direction** : Vector3 direction  
- **speed** : Optional projectile speed (default 100)  
- **damage** : Optional damage (default BaseDamage)  
- **source** : Source of damage

## Combat.AreaDamage(origin, radius, damage, ignoreList, source)
Deals damage in a radius.  
- **origin** : Vector3 center  
- **radius** : Radius of effect  
- **damage** : Optional damage (default BaseDamage)  
- **ignoreList** : Optional table of models to ignore  
- **source** : Source of damage

## Combat.IsFriendly(hum1, hum2)
Checks if two humanoids are on the same team.  
Returns **true** if friendly, **false** otherwise.

# Notes / Best Practices
- Always check that **targetHumanoid** is valid before dealing damage.  
- Use **CombatEvents** to update UI or trigger effects client-side.  
- **ShootProjectile** automatically destroys projectiles after 5 seconds.  
- **AreaDamage** ignores models listed in **ignoreList**.  
- **IsFriendly** can be integrated into a team-based damage system.

# Example Usage
local dmg, crit = Combat.DealDamage(humanoid, 15, player)
Combat.Heal(humanoid, 10)
Combat.Knockback(humanoid, Vector3.new(1,0,0), 100)
local hitHum, hitPos = Combat.RaycastHit(origin, direction, 50)
Combat.ShootProjectile(projTemplate, origin, direction, 120, 20, player)
Combat.AreaDamage(Vector3.new(0,0,0), 10, 25)
local friendly = Combat.IsFriendly(hum1, hum2)
