## [ESX]Eclipse TattooShop

## Requirements
- [plume-esx](https://youtu.be/iGfwUCO0RZQ) (you can use different version esx)
- [esx-skin](https://github.com/esx-framework/esx_skin)
- [skinchanger](https://github.com/ESX-Org/skinchanger)


Put eclipse_TattooShop in your resource directory

Setting config `resources\eclipse_TattooShop\config.json`

  ![image](https://cdn.discordapp.com/attachments/759479979435098152/943156160901566524/unknown.png)
  
## Installation:

esx_skin:



1. Go to esx_skin/client/main.lua
2. Replace lines 260
```lua
TriggerEvent('ECLIPSE:OpenCharacterCreatioMenu')
```
![image](https://user-images.githubusercontent.com/36680471/115523567-e02ffc00-a295-11eb-952d-5c6a5979817f.png)


1. Go to esx_skin/server/main.lua
2. Replace

```lua
RegisterServerEvent('esx_skin:save')
AddEventHandler('esx_skin:save', function(skin)
	local xPlayer = ESX.GetPlayerFromId(source)
	local defaultMaxWeight = ESX.GetConfig().MaxWeight
	-- local backpackModifier = Config.BackpackWeight[skin.bags_1]

	-- if backpackModifier then
	-- 	xPlayer.setMaxWeight(defaultMaxWeight + backpackModifier)
	-- else
	-- 	xPlayer.setMaxWeight(defaultMaxWeight)
	-- end

	MySQL.Async.execute('UPDATE users SET skin = @skin WHERE identifier = @identifier', {
		['@skin'] = json.encode(skin),
		['@identifier'] = xPlayer.identifier
	})
end)

RegisterServerEvent('esx_skin:saveData')
AddEventHandler('esx_skin:saveData', function(skin)
	local xPlayer = ESX.GetPlayerFromId(source)
	local defaultMaxWeight = ESX.GetConfig().MaxWeight
	--local backpackModifier = Config.BackpackWeight[skin.bags_1]
	local playerData = json.decode(skin)
	-- if backpackModifier then
	-- xPlayer.setMaxWeight(defaultMaxWeight + backpackModifier)
	-- else
	--  	xPlayer.setMaxWeight(defaultMaxWeight)
	-- end

	MySQL.Async.execute('UPDATE users SET skin = @skin, firstname = @firstname, lastname = @lastname, dateofbirth = @dateofbirth, sex = @sex WHERE identifier = @identifier', {
		['@skin'] = skin,
		['@identifier'] = xPlayer.identifier,
		['@firstname'] = playerData.CharacterName,
		['@lastname'] = playerData.CharacterSurname,
		['@dateofbirth'] = playerData.CharacterDateBirth,
		['@sex'] = playerData.sex
	})
end)
```
![image](https://user-images.githubusercontent.com/36680471/115525598-eb842700-a297-11eb-96f0-01d883caa7e0.png)


skinchanger:
1. Go to skinchanger/client/main.lua
2. Add code 450-454
```lua
AddEventHandler('skinchanger:customizationUpdate', function(data)
	Character = json.decode(data)
	ApplySkin(Character)
end)
```
Start your server.

For more questions https://discord.gg/8nXR6rfB2C




