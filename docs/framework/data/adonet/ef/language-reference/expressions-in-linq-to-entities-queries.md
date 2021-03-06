---
title: "Выражения в запросах LINQ to Entities | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
ms.assetid: d70b502f-6a15-4120-b4fe-500b173ad9cc
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Выражения в запросах LINQ to Entities
Выражение представляет собой фрагмент кода, результатом вычисления которого является единственное значение, объект, метод или пространство имен.  Выражение может содержать литеральное значение, вызов метода, оператор с операндами или простое имя.  Простые имена могут быть именами переменной, элемента типа, параметра метода, пространства имен или типа.  В выражениях могут использоваться операторы, которые, в свою очередь, используют в качестве параметров другие выражения или вызовы методов, параметрами которых являются другие вызовы методов.  Таким образом, выражения могут быть как простыми, так и очень сложными.  
  
 Выражения в запросах [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] могут содержать любые объекты, допустимые типами в пространстве имен <xref:System.Linq.Expressions>, включая лямбда\-выражения.  Набор выражений, используемых в запросах [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)], является надмножеством выражений, которые могут использоваться в запросах [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)].  Выражения, входящие в запросы к [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)], ограничены набором операций, поддерживаемых `ObjectQuery<T>` и базовым источником данных.  
  
 В следующем примере сравнение в предложении `Where` является следующим выражением.  
  
 [!code-csharp[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Conceptual Examples/CS/Program.cs#whereexpression)]
 [!code-vb[DP L2E Conceptual Examples#WhereExpression](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Conceptual Examples/VB/Module1.vb#whereexpression)]  
  
> [!NOTE]
>  Особые языковые конструкции, такие как `unchecked` в C\#, в [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] значения не имеют.  
  
## Содержание  
 [Константные выражения](../../../../../../docs/framework/data/adonet/ef/language-reference/constant-expressions.md)  
  
 [Выражения сравнения ](../../../../../../docs/framework/data/adonet/ef/language-reference/comparison-expressions.md)  
  
 [Сравнения со значением Null](../../../../../../docs/framework/data/adonet/ef/language-reference/null-comparisons.md)  
  
 [Выражения инициализации](../../../../../../docs/framework/data/adonet/ef/language-reference/initialization-expressions.md)  
  
 [Navigation Properties](http://msdn.microsoft.com/ru-ru/41e1e6b9-8a57-467d-99d9-1857d2ca2ea5)  
  
## См. также  
 [Платформа ADO.NET Entity Framework](../../../../../../docs/framework/data/adonet/ef/index.md)