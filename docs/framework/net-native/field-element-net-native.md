---
title: "Элемент &lt;Field&gt; (машинный код .NET) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# Элемент &lt;Field&gt; (машинный код .NET)
Применяет политику отражения среды выполнения к полю.  
  
## <a name="syntax"></a>Синтаксис  
  
```xml  
  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Тип атрибута|Описание|  
|---------------|--------------------|-----------------|  
|`Name`|Общие правила|Обязательный атрибут. Определяет имя поля.|  
|`Browse`|Отражение|Необязательный атрибут. Определяет запрос для получения сведений о поле или перечисляет поле, но не включает динамический доступ во время выполнения.|  
|`Dynamic`|Отражение|Необязательный атрибут. Управляет доступом среды выполнения к полю для включения динамического программирования. Эта политика гарантирует, что поле можно задать или получить динамически во время выполнения.|  
|`Serialize`|Сериализация|Необязательный атрибут. Управляет доступом среды выполнения к полю, чтобы включить экземпляры типов, предназначенных для сериализации в таких библиотеках, как, например, сериализатор Newtonsoft JSON или для привязки данных.|  
  
## <a name="name-attribute"></a>Name - атрибут  
  
|Значение|Описание|  
|-----------|-----------------|  
|*имя_метода*|Имя поля. Тип поля определяется родительским [ <> \> ](../../../docs/framework/net-native/type-element-net-native.md) или [ <> \> ](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) элемента.|  
  
## <a name="all-other-attributes"></a>Все остальные атрибуты  
  
|Значение|Описание|  
|-----------|-----------------|  
|*policy_setting*|Параметр, применяемый к этому типу политики для поля. Допустимые значения: `Auto`, `Excluded`, `Included` и `Required`. Дополнительные сведения см. в разделе [параметры политики директив среды выполнения](../../../docs/framework/net-native/runtime-directive-policy-settings.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
 Отсутствует.  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[<>\>](../../../docs/framework/net-native/type-element-net-native.md)|Применяет политику отражения к типу и всем его членам.|  
|[<>\>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|Применяет политику отражения к сконструированному универсальному типу и всем его членам.|  
  
## <a name="remarks"></a>Примечания  
 Если политика поля не определена явно, оно наследует политику среды выполнения своего родительского элемента.  
  
## <a name="see-also"></a>См. также  
 [Элементы директив среды выполнения](../../../docs/framework/net-native/runtime-directive-elements.md)   
 [Ссылка на файл конфигурации директив (rd.xml) среды выполнения](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [Параметры политики директив среды выполнения](../../../docs/framework/net-native/runtime-directive-policy-settings.md)