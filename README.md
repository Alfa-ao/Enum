# Enum

Фабрика для создания перечислений - Enum. Allods Online.

## Установка

- Скачать архив - `Code` - `Download ZIP`.
- Поместить содержимое архива `Enum-main.zip\Enum-main\*` в папку `\data\Mods\Addons\_ИмяАддона_\Libs\Enum\`.
- Отредактировать `AddonDesc.(UIAddon).xdb` дополнив в содержимое атрибута `ScriptFileRefs` скрипты:
```xml
<Item href="/Mods/SampleCommon/CoreScripts/ClassesImplementation.lua" /> <!-- CoreScripts OOP -->
<Item href="Libs/Enum/src/EnumFactory.lua" /> <!-- Фабрика для Enums -->
<Item href="Libs/Enum/src/Definitions/<___name___>.lua" /> <!-- Пользовательский Enum, нужные файлы для работы -->
```

## Примеры

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

## Создание перечислений

```lua
Global( "EnumSortOrder", EnumFactory:create( {
	ASC = true,
	DESC = false,
} ) )
```
