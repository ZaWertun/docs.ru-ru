---
title: "XML Character Entities and XAML | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "&"
  - "&amp"
  - "&gt"
  - "&lt"
helpviewer_keywords: 
  - "XAML [XAML Services], special characters"
  - "ampersand (&) [XAML Services]"
  - "special characters [XAML Services]"
  - "apostrophe (') [XAML Services]"
  - "greater-than (>) character [XAML Services]"
  - "XAML [XAML Services], quotation mark (")"
  - "XAML [XAML Services], apostrophe (')"
  - "& (ampersand) [XAML Services]"
  - "XAML [XAML Services], & (ampersand)"
  - "XAML [XAML Services], escape sequence"
  - "quotation mark (") [XAML Services]"
  - "less-than (<) character [XAML Services]"
ms.assetid: 6896d0ce-74f7-420a-9ab4-de9bbf390e8d
caps.latest.revision: 23
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 21
---
# XML Character Entities and XAML
XAML использует сущности символов, определенные в XML для специальных символов.  В этом разделе описываются некоторые особые сущности знаков и общие вопросы, связанные с другими концепциями XML в XAML.  
  
<a name="character_entities_and_escaping_issues_that_are_unique_to_xaml"></a>   
## Сущности символов и проблемы экранирования, уникальные для XAML  
 Разметка XAML обычно использует же сущности символов и escape\-последовательности, которые определены в XML.  
  
 Главной особенностью является то, фигурные скобки \({ и }\) в XAML имеют значение, так как эти они информируют обработчика XAML о том, что последовательность символов, заключенных в фигурные скобки, должна интерпретироваться как расширение разметки.  Подробнее о расширениях разметки см. в разделе [Markup Extensions for XAML Overview](../../../docs/framework/xaml-services/markup-extensions-for-xaml-overview.md).  
  
 Однако можно по\-прежнему отобразить фигурные скобки как литеральные символы, используя escape\-последовательности, определенные в языке XAML, а не в XML.  Подробнее см. в разделе [{} Escape Sequence \/ Markup Extension](../../../docs/framework/xaml-services/escape-sequence-markup-extension.md).  
  
 Обратите внимание, что обратная косая черта \(\\\) не требует escape\-последовательности при обработке в виде строки.  
  
<a name="xml_character_entities"></a>   
## Сущности символов XML  
 Как упоминалось ранее, большинство сущностей символов и escape\-последовательностей, которые обычно используются для написания разметки XAML, определяются XML.  Этот раздел не содержит полного списка этих сущностей. Подробные сведения о них можно найти во внешней документации, например в спецификациях XML.  Однако для удобства в этом разделе перечислены некоторые из определенных сущностей символов XML, которые обычно используются в разметке XAML.  
  
|Знак|Сущность|Примечания|  
|----------|--------------|----------------|  
|& \(амперсанд\)|&amp;|Должен использоваться для значений атрибутов и содержимого элемента.|  
|\> \(знак "больше"\)|&gt;|Должен использоваться для значения атрибута, но "\>" допустим в качестве содержимого элемента, если ему не предшествует "\<".|  
|\< \(знак "меньше"\)|&lt;|Должен использоваться для значения атрибута, но "\<" допустим в качестве содержимого элемента, если после него не идет "\>".|  
|"\(прямая кавычка\)|&quot;|Должен использоваться для значения атрибута, но прямая кавычка \("\) допустима в качестве содержимого элемента.  Обратите внимание, что значения атрибутов могут быть заключены в прямые одиночные кавычки \('\) или прямые двойные кавычки \(""\). Первый символ определяет оболочку значения атрибута, а альтернативный знак кавычек можно затем использовать в качестве литерала в значении.|  
|' \(одиночная прямая кавычка\)|&apos;|Должен использоваться для значения атрибута, но прямая одиночная кавычка \('\) допустима в качестве содержимого элемента.  Обратите внимание, что значения атрибутов могут быть заключены в прямые одиночные кавычки \('\) или прямые двойные кавычки \(""\). Первый символ определяет оболочку значения атрибута, а альтернативный знак кавычек можно затем использовать в качестве литерала в значении.|  
|\(сопоставления цифровых символов\)|&\#*\[целое число\]*; или &\#x*\[шестнадцатеричное число\]*;|XAML поддерживает сопоставления числовых символов с активной кодировкой.|  
|\(неразрывный пробел\)|&\#160; \(предполагается кодировка UTF\-8\)|Для элементов потокового документа или элементы, которые принимают текст, например <xref:System.Windows.Controls.TextBox> в WPF, неразрывные пробелы не нормализуются в разметке даже для `xml:space="default"`.  \(Подробнее: [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md).\)|  
  
<a name="xml_comment_format"></a>   
## Формат комментариев XML  
 XAML использует формат комментариев XML: начало комментария — `<!--`, конец комментария — `-->,`, при этом последовательность `--` не должна входить в комментарий.  
  
<a name="xml_processing_instructions"></a>   
## Инструкции по обработке XML  
 XAML обрабатывает инструкции по обработке XML в соответствии со спецификациями XML, в которых указано, что инструкции должны передаваться.  Обработка XAML в службах XAML .NET Framework XAML не использует инструкции по обработке.  Другие существующие платформы, использующие XAML, также не применяют инструкции по обработке из XAML.  
  
## См. также  
 [{} Escape Sequence \/ Markup Extension](../../../docs/framework/xaml-services/escape-sequence-markup-extension.md)   
 [Общие сведения о языке XAML \(WPF\)](../../../ocs/framework/wpf/advanced/xaml-overview-wpf.md)   
 [Расширения разметки и XAML WPF](../../../ocs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)   
 [Грамматика XamlName](../../../docs/framework/xaml-services/xamlname-grammar.md)   
 [Whitespace Processing in XAML](../../../docs/framework/xaml-services/whitespace-processing-in-xaml.md)