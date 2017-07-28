---
title: "Результаты вывода XslTransform | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 8e149d32-4b2f-493f-9e4b-d0d93475acde
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# Результаты вывода XslTransform
Поскольку таблицы стилей могут определять формат вывода с помощью инструкции `<xsl:output>` с атрибутом `method`, в следующей таблице описан формат вывода при использовании для записи вывода метода <xref:System.Xml.Xsl.XslTransform.Transform%2A> и объявлении этого формата как <xref:System.IO.Stream> или <xref:System.IO.TextWriter>.  
  
> [!NOTE]
>  Класс <xref:System.Xml.Xsl.XslTransform> в версии [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] устарел.  Можно выполнять XSLT\-преобразование, используя класс <xref:System.Xml.Xsl.XslCompiledTransform>.  Дополнительные сведения см. в разделах [Использование класса XslCompiledTransform](../../../../docs/standard/data/xml/using-the-xslcompiledtransform-class.md) и [Миграция с класса XslTransform](../../../../docs/standard/data/xml/migrating-from-the-xsltransform-class.md).  
  
 Поскольку таблицы стилей могут определять формат вывода с помощью инструкции `<xsl:output>` с атрибутом `method`, в следующей таблице описан формат вывода при использовании для записи вывода метода <xref:System.Xml.Xsl.XslTransform.Transform%2A> и объявлении этого формата как <xref:System.IO.Stream> или <xref:System.IO.TextWriter>.  В следующей таблице показано, что происходит, если тип вывода декларирован методом <xref:System.Xml.Xsl.XslTransform.Transform%2A> в сочетании с инструкцией `<xsl:output>`.  
  
|\<xsl:output method \= \> атрибут|Формат результата|  
|---------------------------------------|-----------------------|  
|method\="xml"|XML|  
|method\="html"|HTML|  
|method\="text"|Text|  
  
> [!NOTE]
>  Примечание. Инструкция `<xsl:output>` не выполняется, если метод <xref:System.Xml.Xsl.XslTransform.Transform%2A> возвращает <xref:System.Xml.XmlReader> или <xref:System.Xml.XmlWriter>.  
  
 Следующие атрибуты поддерживаются, если выходными данными метода <xref:System.Xml.Xsl.XslTransform.Transform%2A> является объект <xref:System.IO.Stream> или <xref:System.IO.TextWriter>:  
  
-   encoding\*  
  
-   omit\-xml\-declaration  
  
-   Автономный  
  
-   doctype\-public  
  
-   doctype\-system  
  
-   cdata\-section\-elements  
  
-   indent  
  
    > [!NOTE]
    >  \*Атрибут encoding пропускается, если метод <xref:System.Xml.Xsl.XslTransform.Transform%2A> отправляет выходные данные в объект <xref:System.IO.TextWriter>.  Вместо него в объекте <xref:System.IO.TextWriter> используется свойство encoding.  
  
 Следующий атрибут пропускается, если выходом метода <xref:System.Xml.Xsl.XslTransform.Transform%2A> является <xref:System.IO.Stream>.  
  
-   Версия: всегда используется версия 1.0  
  
-   Тип носителя: используемый тип носителя  
  
## Экранирование специальных символов  
 Тег `<xsl:text disable-output-escaping>` используется для указания, следует ли экранировать специальные символы в XML\-формате \(например, использовать `<&lt>` вместо `"<"`\) или оставлять их в текущем состоянии.  Атрибут `disable-output-escaping` не учитывать при преобразовании в объект <xref:System.Xml.XmlReader> или <xref:System.Xml.XmlWriter> и не влияет на специальные символы.  
  
## См. также  
 [Реализация классом XslTransform XSLT\-процессора](../../../../docs/standard/data/xml/xsltransform-class-implements-the-xslt-processor.md)