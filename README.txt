/*
	HS Blackmarket
	by Halv & Suppe
*/

The HS Blackmarket is a 'new' Trader-system for A3 Epoch, it was created in collaboration with Halv, he wrote 90% of the scripts, Halv is the true genius.

Features:
- Trader with Custom Dialog (Menu)
- Trader with unlimited supply
- Trader will spawn random over the Map
- Trader will spawn in 5 different "Camps"
- Easily edit/add Prices,Items,Vehicles,Weapons
- Easily Blacklist Items,Vehicles,Weapons
- Easily control about Vehicleammo
- Vehicleammo count over restart (10 bullets left for the restart = 10 bullets left after restart)
- Static and Random Traders
- Work with stock Epoch AH and infistar
- Work without emod !
- Work on every Map

Install:
- Copy the "trader" Folder and the Stringtable.xml in your epoch.Mission

- Add to your init:
  [] execVM "trader\init.sqf";
  [] execVM "trader\HALV_takegive_crypto_init.sqf";
  [] execVM "trader\resetvehicleammo.sqf";
  
- Add to your description.ext
  #include "trader\tradedialog.hpp"
  #include "trader\HSPricing.hpp"
  
- (optional) Open epoch.Mission/trader/init.sqf to configurate the HS Blackmarket

- (optional) Open epoch.Mission/trader/HSPricing.hpp to configurate prices, or to add Items,Vehicles,Weapons and so on

- (optional) Open epoch.Mission/trader/settings.sqf and resetvehicleammo.sqf to configurate the Vehicleammo

- (optional) Remove 1 Epoch Trader for every Blackmarket Trader you added (remove Epoch Trader: \Arma 3\@epochhive\epochconfig.hpp  ,search for NPCSlotsLimit)

- (optional) to get all messages of the traders (like the vehicleworldlimit check) you need: http://epochmod.com/forum/index.php?/topic/34570-easy-kill-feedmessages-wstudy-bury-body-function-beta/
  
- Edit your BE Filter:
createvehicle.txt   Line 1   add:
!="M_AT" !="SmokeLauncherAmmo" !="B_AssaultPack_cbr" !="B_AssaultPack_dgtl" !="B_AssaultPack_khk" !="B_AssaultPack_mcamo" !="B_AssaultPack_ocamo" !="B_AssaultPack_rgr" !="B_AssaultPack_sgg" !="B_Carryall_cbr" !="B_Carryall_khk" !="B_Carryall_mcamo" !="B_Carryall_ocamo" !="B_Carryall_oli" !="B_Carryall_oucamo" !="B_FieldPack_blk" !="B_FieldPack_cbr" !="B_FieldPack_khk" !="B_FieldPack_ocamo" !="B_FieldPack_oli" !="B_FieldPack_oucamo" !="B_Kitbag_cbr" !="B_Kitbag_mcamo" !="B_Kitbag_rgr" !="B_Kitbag_sgg" !="B_Parachute" !="B_TacticalPack_blk" !="B_TacticalPack_mcamo" !="B_TacticalPack_ocamo" !="B_TacticalPack_oli" !="B_TacticalPack_rgr"
createvehicle.txt   Line 2   add:
!="smallbackpack_red_epoch" !="smallbackpack_green_epoch" !="smallbackpack_teal_epoch" !="smallbackpack_pink_epoch"

publicvariable.txt    Line 1   add:
!="BIS_fnc_objectVar_obj2_1288" !="HALV_takegive" !="HSPV_traderrequest"

setvariable.txt   Line 1   add:
!="bis_fnc_objectvar_var" !="BIS_fnc_objectVar_obj2_1280"

scripts.txt      7 createDialog    add:
!="createDialog "HS_trader_dialog";"
scripts.txt      7 addMagazine    add:
!="if !(player canAdd (_x select 0)) exitWith {};\nplayer addMagazine[_x select 0, _x select 1];"
scripts.txt      7 setVelocity    add:
!="_smokeg setVelocity _Gvel;"
scripts.txt      7 addItem    add:
!="_this call HS_additemtolb;false"
scripts.txt      7 exec    add:
!="trader\init.sqf";"

- for infistar
add these: 9999,9980 to the allowedDialogs.
like this: _allowedDialogs = [-1,602,7777,7778,9999,9980];