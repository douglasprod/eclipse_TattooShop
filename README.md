## [ESX]Eclipse TattooShop

## Requirements
- [plume-esx](https://youtu.be/iGfwUCO0RZQ) (you can use different version esx)
- [esx-skin](https://github.com/esx-framework/esx_skin)
- [skinchanger](https://github.com/ESX-Org/skinchanger)


Put eclipse_TattooShopp in your resource directory

Setting config `resources\eclipse_TattooShop\config.json`

	Change language, add new shops, confige tattoo types in shops and etc.
  ![image](https://cdn.discordapp.com/attachments/759479979435098152/943156160901566524/unknown.png)
  
## Installation:

skinchanger:
1. Go to skinchanger/client/main.lua
2. Find function ```lua function ApplySkin(skin, clothes) ``` and add the following code to the end of the function
```lua
TriggerServerEvent("ECLIPSE:GetPlayerTattooss")
```
![image](https://user-images.githubusercontent.com/36680471/154086714-688ec972-5c49-4e8b-89d1-53f4114c7fb9.png)


Start your server.

For more questions https://discord.gg/8nXR6rfB2C




