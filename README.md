# Enum

Фабрика для создания перечислений - Enum. Allods Online.

### Примеры

```lua
log( "ENUM_TakeItemActionType_Money" == EnumTakeItemActionType.MONEY ) -- true
```

```lua
function OnItemTaken( params )
    if params.actionType == EnumTakeItemActionType.CRAFT then
		-- params.actionType == "ENUM_TakeItemActionType_Craft" предмет (скрафчен).
	end
end

common.RegisterEventHandler( OnItemTaken, "EVENT_AVATAR_ITEM_TAKEN" )
```

Попытка присвоить значение:

```lua
EnumTakeItemActionType.CRAFT = "Enum_set_value" -- Error: Enum is read-only
```

Обращение к неизвестному ключу:

```lua
local val = EnumTakeItemActionType.TEST -- Error: Invalid enum key: TEST
```