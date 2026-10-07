# Enum

Фабрика для создания перечислений - Enum. Аллоды Онлайн.

## Подключение

[**ForgePackage**](https://github.com/Alfa-ao/ForgePackage)

```
require Alfa-ao/Enum
```

## Примеры

```lua
log( EnumTakeItemActionType.MONEY:Equals( "ENUM_TakeItemActionType_Money" ) ) -- true
```

```lua
function OnItemTaken( params )
    if EnumTakeItemActionType.CRAFT:Equals( params.actionType ) then
        -- params.actionType == "ENUM_TakeItemActionType_Craft" предмет (скрафчен).
    end
end

common.RegisterEventHandler( OnItemTaken, "EVENT_AVATAR_ITEM_TAKEN" )
```

```lua
-- Создание стандартного перечисления
EnumTakeItemActionType = EnumFactory:create {
    CRAFT = "ENUM_TakeItemActionType_Craft",
    LOOT  = "ENUM_TakeItemActionType_Loot",
}

-- Создание гибридного перечисления из несколько допустимых значений
EnumStatus = EnumFactory:create {
    ACTIVE = { "STATUS_ACTIVE", 1 },
}

-- Прямой и обратный доступ к элементам
local craftObj = EnumTakeItemActionType.CRAFT
local sameObj  = EnumTakeItemActionType[ "ENUM_TakeItemActionType_Craft" ]

-- Сравнение с внешними значениями через метод :Equals()
if EnumTakeItemActionType.CRAFT:Equals( "ENUM_TakeItemActionType_Craft" ) then
    -- Обработка действия
end
if EnumStatus.ACTIVE:Equals( 1 ) then
    -- Обработка статуса
end

-- Неявное приведение типов при конкатенации и арифметике
local logMsg = "Current action: " .. EnumTakeItemActionType.CRAFT

-- Сравнение двух объектов перечисления через оператор ==
if EnumTakeItemActionType.CRAFT == EnumTakeItemActionType.CRAFT then
    -- Объекты идентичны
end
```