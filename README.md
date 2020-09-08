# Setup l2j server using podman 

Create a pod for your l2j server setup

`podman pod create -n l2j -p 2106:2106 -p 7777:7777`

Run l2j db inside a pod

```console
podman run \
-d --restart=always --pod=l2j \
-e MYSQL_ROOT_PASSWORD='root' \
--name l2j_db localhost/l2j_db:latest
```

Run l2j server inside a pod

```console
podman run \
-d --restart=always --pod=l2j \
-e IP_ADDRESS="127.0.0.1" \
-e LAN_ADDRESS="10.11.86.2" \
-e LAN_SUBNET="10.0.0.0/8" \
-e JAVA_XMS="512m" \
-e JAVA_XMX="2g" \
-e RATE_XP="1" \
-e RATE_SP="1" \
-e QUEST_MULTIPLIER_XP="1" \
-e QUEST_MULTIPLIER_SP="1" \
-e QUEST_MULTIPLIER_REWARD="1" \
-e AUTO_LEARN_SKILLS="False" \
-e MAX_FREIGHT_SLOTS="200" \
-e DWARF_RECIPE_LIMIT="50" \
-e COMM_RECIPE_LIMIT="50" \
-e CRAFTING_SPEED_MULTIPLIER="1" \
-e FREE_TELEPORTING="False" \
-e STARTING_ADENA="0" \
-e STARTING_LEVEL="1" \
-e STARTING_SP="0" \
-e ALLOW_MANOR="True" \
-e MAX_ONLINE_USERS="500" \
-e MAX_WAREHOUSE_SLOTS_DWARF="120" \
-e MAX_WAREHOUSE_SLOTS_NO_DWARF="100" \
-e MAX_WAREHOUSE_SLOTS_CLAN="200" \
-e PET_XP_RATE="1" \
-e RATE_ADENA="1" \
-e ADMIN_RIGHTS="True" \
-e FORCE_GEODATA="False" \
-e COORD_SYNC="-1" \
-e HELLBOUND_ACCESS="True" \
-e WEIGHT_LIMIT="1" \
-e TVT_ENABLED="True" \
-e SAVE_GM_SPAWN_ON_CUSTOM="True" \
-e CUSTOM_SPAWNLIST_TABLE="True" \
-e CUSTOM_NPC_DATA="True" \
-e CUSTOM_TELEPORT_TABLE="True" \
-e CUSTOM_NPC_BUFFER_TABLES="True" \
-e CUSTOM_SKILLS_LOAD="True" \
-e CUSTOM_ITEMS_LOAD="True" \
-e CUSTOM_MULTISELL_LOAD="True" \
-e CUSTOM_BUYLIST_LOAD="True" \
-e VITALITY_SYSTEM="True" \
-e ITEM_SPOIL_MULTIPLIER="1" \
-e ITEM_DROP_MULTIPLIER="1" \
--name=l2j_srv localhost/l2j_srv
```
