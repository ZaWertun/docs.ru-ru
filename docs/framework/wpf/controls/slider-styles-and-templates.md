---
title: "Стили и шаблоны элемента Slider | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ControlTemplate [WPF], Slider"
  - "части [WPF], Slider"
  - "Ползунок [WPF], стили и шаблоны"
  - "состояния [WPF], Slider"
  - "стили [WPF], Slider"
  - "шаблоны [WPF], Slider"
ms.assetid: d89aa97b-075a-4752-9c41-9679df65c491
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# Стили и шаблоны элемента Slider
В этом разделе описываются стили и шаблоны для элемента управления <xref:System.Windows.Controls.Slider>.  Предусмотренный по умолчанию шаблон <xref:System.Windows.Controls.ControlTemplate> можно изменить, чтобы придать элементу управления уникальный внешний вид.  Дополнительные сведения см. в разделе [Настройка внешнего вида существующего элемента управления путем создания объекта ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md).  
  
## Части Slider  
 В следующей таблице перечислены именованные части элемента управления <xref:System.Windows.Controls.Slider>.  
  
||||  
|-|-|-|  
|Часть|Тип|Описание|  
|PART\_Track|<xref:System.Windows.Controls.Primitives.Track>|Контейнер для элемента, который указывает положение элемента <xref:System.Windows.Controls.Slider>.|  
|PART\_SelectionRange|<xref:System.Windows.FrameworkElement>|Элемент, отображающий диапазон выделения в элементе управления <xref:System.Windows.Controls.Slider>.  Диапазон выделения отображается, только если значение свойства <xref:System.Windows.Controls.Slider.IsSelectionRangeEnabled%2A> равно `true`.|  
  
## Состояния Slider  
 В следующей таблице перечислены визуальные состояния элемента управления <xref:System.Windows.Controls.Slider>.  
  
|Имя VisualState|Имя VisualStateGroup|Описание|  
|---------------------|--------------------------|--------------|  
|Обычные|CommonStates|Состояние по умолчанию.|  
|MouseOver|CommonStates|Указатель мыши расположен в элементе управления.|  
|Disabled|CommonStates|Элемент управления отключен.|  
|Focused|FocusStates|Элемент управления имеет фокус.|  
|Unfocused|FocusStates|Элемент управления не имеет фокуса.|  
|Valid|ValidationStates|Элемент управления использует класс <xref:System.Windows.Controls.Validation>, и значение присоединенного свойства <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> равно `false`.|  
|InvalidFocused|ValidationStates|Значение присоединенного свойства <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> равно `true`, если элемент управления имеет фокус.|  
|InvalidUnfocused|ValidationStates|Значение присоединенного свойства <xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=fullName> равно `true`, если элемент управления не имеет фокус.|  
  
## Пример шаблона ControlTemplate "Ползунок"  
 В следующем примере показано, как определить шаблон <xref:System.Windows.Controls.ControlTemplate> для элемента управления <xref:System.Windows.Controls.Slider>.  
  
 [!code-xml[ControlTemplateExamples#Slider](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/slider.xaml#slider)]  
  
 В предыдущем примере используется один или несколько следующих ресурсов.  
  
 [!code-xml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 Полный пример см. по адресу          [Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041) .  
  
## См. также  
 <xref:System.Windows.FrameworkElement.Style%2A>   
 <xref:System.Windows.Controls.ControlTemplate>   
 [Стили и шаблоны элемента Control](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)   
 [Настройка элементов управления](../../../../docs/framework/wpf/controls/control-customization.md)   
 [Стилизация и использование шаблонов](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [Настройка внешнего вида существующего элемента управления путем создания объекта ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)