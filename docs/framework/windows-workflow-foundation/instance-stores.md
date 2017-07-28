---
title: "Хранилища экземпляров | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2629668-0923-4987-b943-67477131c1e0
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# Хранилища экземпляров
Хранилище экземпляров — это логический контейнер для экземпляров.Здесь хранятся данные и метаданные экземпляра.Хранилище экземпляров не предполагает выделения физического пространства.Хранилище экземпляра может содержать постоянные сведения в базе данных SQL Server или непостоянные сведения о состоянии в памяти.[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] поставляется с хранилищем экземпляров рабочего процесса SQL — конкретной реализацией хранилища экземпляров, которая позволяет рабочему процессу хранить данные и метаданные в базе данных SQL Server 2005 или SQL Server 2008.Кроме того, Windows Server App Fabric также предоставляет конкретную реализацию хранилища экземпляров.[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Хранилище экземпляров фабрики приложений Windows Server, запрос и поставщики управления](http://go.microsoft.com/fwlink/?LinkID=201201&clcid=0x419).  
  
 API сохраняемости — это интерфейс между узлом и хранилищем экземпляров, позволяющим узлу отправлять запросы на команды \(например, <xref:System.Activities.DurableInstancing.LoadWorkflowCommand> и <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>\) в хранилище экземпляров.Конкретная реализация данного API\-интерфейса называется поставщиком сохраняемости.Поставщик сохраняемости получает запросы от узла и изменяет хранилище экземпляров.  
  
 Узлы и хранилища экземпляров являются подключаемыми; узел можно использовать с несколькими хранилищами экземпляров, хранилище экземпляров можно использовать с несколькими узлами.Хранилище экземпляров обычно оптимизируется под шаблоны использования определенного узла, хотя хранилище экземпляров и узел могут обрести независимые жизненные циклы.Например, **WorkflowServiceHost** и **SqlWorkflowInstanceStore** предназначены для совместной работы.Можно создать собственное хранилище экземпляров для сохранения данных и метаданных экземпляров службы рабочего процесса и использовать это хранилище экземпляров совместно с **WorkflowServiceHost**.Например, можно создать хранилище OracleWorkflowInstanceStore, позволяющее рабочему процессу хранить данные в базе данных Oracle, а не в базе данных SQL Server.  
  
 Узлы обычно снабжаются дополнительными функциями, которые модифицируют сохраненные объекты.Например, в системе хранения экземпляров может находиться узел рабочего процесса, расширение, поддерживающее операцию «Suspend», и хранилище экземпляров SQL.Узел рабочего процесса может отправить стандартную команду, например «Save» или «Load», для сохранения рабочего процесса в хранилище экземпляров или для его загрузки соответственно.Расширение для приостановки может добавить командам сохранения или загрузки экземпляров рабочего процесса такую дополнительную семантику, что приостановленный экземпляр рабочего процесса нельзя будет загрузить.Поставщик сохраняемости для хранилища экземпляров SQL понимает команды сохранения или загрузки экземпляров рабочего процесса и применяет команды путем вызова соответствующих хранимых процедур, которые вносят изменения в таблицы сохраненных объектов в базе данных SQL Server.  
  
 В хранилище экземпляров узел является владельцем экземпляра.Одновременно узел может владеть несколькими экземплярами из нескольких разных хранилищ.Узел предоставляет идентификаторы GUID для ключей экземпляров, связанных с экземплярами.Ключ экземпляра — это уникальный псевдоним, определяющий экземпляр.Система сохраняемости создает, обновляет и удаляет сведения о владельце экземпляра, когда выполняет команды, запрошенные узлами.  
  
 Следующий список содержит важные этапы взаимодействия узла с хранилищем экземпляров.  
  
1.  Получите **InstanceStore** от поставщика сохраняемости.  
  
2.  Получите дескриптор экземпляра, вызвав метод <xref:System.Runtime.Persistence.InstanceStore.CreateInstanceHandle%2A> на **InstanceStore**.  
  
3.  Вызовите команды для дескриптора экземпляра, вызвав метод <xref:System.Runtime.Persistence.InstanceStore.Execute%2A> на **InstanceStore**.  
  
4.  Изучите <xref:System.Runtime.Persistence.InstanceView>, полученный от **InstanceStore.Execute**, чтобы определить результаты команд.