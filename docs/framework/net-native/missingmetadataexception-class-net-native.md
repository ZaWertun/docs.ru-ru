---
title: "Класс MissingMetadataException (машинный код .NET) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 408f25c4-6d60-475c-92b1-7b52b777c6db
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# Класс MissingMetadataException (машинный код .NET)
**Приложения .NET для Windows 10, только [!INCLUDE[net_native](../../../includes/net-native-md.md)]**  
  
 Исключение, возникающее при использовании отражения для извлечения метаданных, которые не существуют.  
  
 **Пространство имен:** System.Reflection  
  
> [!IMPORTANT]
>  Класс `MissingMetadataException` предназначен исключительно для внутреннего использования цепочкой инструментов [!INCLUDE[net_native](../../../includes/net-native-md.md)].  Он не предназначен для использования в стороннем коде. Вам также не следует обрабатывать исключение в коде своего приложения.  Вместо этого исключение устраняется путем добавления записей в [файл директив времени выполнения](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  Дополнительные сведения см. в разделе "Примечания".  
  
## Синтаксис  
 [!code-csharp[ProjectN#4](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/missingmetadataexception_syntax1.cs#4)]  
  
 Обратите внимание на то, что класс `MissingMetadataException` является производным от <xref:System.TypeAccessException>.  
  
 В классе `MissingMetadataException`представлены следующие члены:  
  
## Конструкторы  
  
|Конструктор|Описание|  
|-----------------|--------------|  
|`public MissingMetadataException()`|Инициализирует новый экземпляр класса `MissingMetadataException`, используя системное сообщение, содержащее описание ошибки.<br /><br /> Этот конструктор предназначен только для внутреннего использования цепочки инструментов [!INCLUDE[net_native](../../../includes/net-native-md.md)].|  
|`public MissingMetadataException(String message)`|Инициализирует новый экземпляр класса `MissingMetadataException` с указанным сообщением об ошибке.<br /><br /> Этот конструктор предназначен только для внутреннего использования цепочкой инструментов [!INCLUDE[net_native](../../../includes/net-native-md.md)].|  
  
## Свойства  
  
|Свойство|Описание|  
|--------------|--------------|  
|`public IDictionary Data { get; }`|Возвращает коллекцию пар ключ\/значение, предоставляющие дополнительные сведения об исключении, определяемые пользователем.  \(Является наследником <xref:System.Exception?displayProperty=fullName>\)|  
|`public string HelpLink { get; set; }`|Получает или задает ссылку на файл справки, связанный с этим исключением.  \(Является наследником <xref:System.Exception?displayProperty=fullName>\)|  
|`public int HResult { get; protected set; }`|Получает или задает `HRESULT`, закодированное числовое значение, присвоенное определенному исключению.  \(Является наследником <xref:System.Exception?displayProperty=fullName>\)|  
|`public Exception InnerException { get; }`|Получает исключение, которое вызвало текущее исключение.  \(Является наследником <xref:System.Exception?displayProperty=fullName>\)|  
|`public string Message { get; }`|Получает сообщение, описывающее текущее исключение.  \(Является наследником <xref:System.TypeLoadException>\)|  
|`public string Source { get; set; }`|Возвращает или задает имя приложения или объекта, вызвавшего ошибку.  \(Является наследником <xref:System.Exception?displayProperty=fullName>\)|  
|`public string StackTrace { get; }`|Получает строковое представление непосредственных кадров в стеке вызова.  \(Является наследником <xref:System.Exception?displayProperty=fullName>\)|  
|`public MethodBase TargetSite { get; }`|Возвращает метод, который вызвал текущее исключение.  \(Является наследником <xref:System.Exception?displayProperty=fullName>\)|  
|`public string TypeName { get; ]`|Получает полное имя типа, метаданные которого отсутствует.  \(Является наследником <xref:System.TypeLoadException>\)|  
  
## Методы  
  
|Метод|Описание|  
|-----------|--------------|  
|`public bool Equals(Object obj)`|Определяет, равен ли заданный объект текущему объекту.  \(Является наследником <xref:System.Exception?displayProperty=fullName>\)|  
|`protected void Finalize()`|Позволяет объекту попытаться освободить ресурсы и выполнить другие операции очистки, перед тем как он будет уничтожен во время сборки мусора.  \(Является наследником <xref:System.Object>\)|  
|`public Exception GetBaseException()`|Возвращает исключение, которое является корневой причиной одного или нескольких исключений.  \(Является наследником <xref:System.Exception?displayProperty=fullName>\)|  
|`public int GetHashCode()`|Возвращает хэш\-код для экземпляра`MissingMetadataException`.  \(Является наследником <xref:System.Object>\)|  
|`public void GetObjectData(SerializationInfo info, StreamingContext context)`|Задает объект <xref:System.Runtime.Serialization.SerializationInfo>, содержащий информацию об исключении.  \(Является наследником <xref:System.TypeLoadException>\)|  
|`public Type GetType()`|Возвращает тип среды выполнения текущего экземпляра.  \(Является наследником <xref:System.Exception?displayProperty=fullName>\)|  
|`protected Object MemberwiseClone()`|Создает неполную копию текущего объекта.  \(Является наследником <xref:System.Object>\)|  
|`public string ToString()`|Возвращает строковое представление текущего исключения.  \(Является наследником <xref:System.Exception?displayProperty=fullName>\)|  
  
## События  
  
|Событие|Описание|  
|-------------|--------------|  
|`protected event EventHandler<SafeSerializationEventArgs> SerializeObjectState`|Возникает, когда исключение сериализовано для создания объекта состояния исключения, содержащего сериализованные данные об исключении.  \(Является наследником <xref:System.Exception?displayProperty=fullName>\)|  
  
## Сведения об использовании  
 Исключение`MissingMetadataException` возникает, если использовать отражение для доступа к метаданным, которые не доступны в сборке.  
  
 Метаданные, доступные для приложения во время выполнения определяются файлом директив среды выполнения \(XML\-файл конфигурации\), \*. rd.xml.  Чтобы избежать возникновения этого исключения приложения, необходимо изменить \*. rd.xml, чтобы определить метаданные, которые должны присутствовать во время выполнения.  Информацию о формате файла \*.rd.xml см. в разделе [Ссылка на файл конфигурации директив среды выполнения \(rd.xml\)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
> [!IMPORTANT]
>  Так как это исключение указывает, что метаданные, необходимые для приложения, недоступны во время выполнения, не не следует обрабатывать это исключение в блоке `try`и`catch`.  Вместо этого следует выяснить причины возникновения исключения и устранить ее с помощью файла директив среды выполнения.  Чтобы получить запись, которую можно добавить в файл директив среды выполнения, устраняющий исключение, можно использовать одно из двух средств устранения неполадок.  
>   
>  -   [Средство устранения неполадок MissingMetadataException](http://dotnet.github.io/native/troubleshooter/type.html) для типов.  
> -   [Средство устранения неполадок MissingMetadataException](http://dotnet.github.io/native/troubleshooter/method.html) для методов.  
  
 Класс `MissingMetadataException` не содержит уникальных членов; все его члены наследуются от базового класса, <xref:System.TypeAccessException>.  
  
## См. также  
 <xref:System.Exception?displayProperty=fullName>   
 <xref:System.TypeAccessException>   
 [Класс MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)   
 [Класс MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)   
 [Ссылка на файл конфигурации директив среды выполнения \(rd.xml\)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)