---
title: "Функция выражения (Visual Basic) | Документы Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 9b181b18a28a8b92a392fffdc10e08690d54f545
ms.contentlocale: ru-ru
ms.lasthandoff: 03/13/2017

---
# <a name="function-expression-visual-basic"></a>Выражение Function (Visual Basic)
Объявляет параметры и код, определяющий функции лямбда-выражение.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a>Части  
  
|Термин|Определение|  
|---|---|  
|`parameterlist`|Необязательный. Список имен локальных переменных, представляющих параметры этой процедуры. Круглые скобки должны присутствовать даже в том случае, если список пуст. В разделе [список параметров](../../../visual-basic/language-reference/statements/parameter-list.md).|  
|`expression`|Обязательный. Одно выражение. Тип выражения является типом возвращаемого значения функции.|  
|`statements`|Обязательный. Список инструкций, возвращает значение, используя `Return` инструкции. (См. [оператор Return](../../../visual-basic/language-reference/statements/return-statement.md).) Тип возвращаемого значения — возвращаемый тип функции.|  
  
## <a name="remarks"></a>Примечания  
 Объект *лямбда-выражение* является функцией без имени, которая вычисляет и возвращает значение. Лямбда-выражение можно использовать везде, где можно использовать тип делегата, за исключением того, в качестве аргумента `RemoveHandler`. Дополнительные сведения о делегатах и использовании лямбда-выражений с делегатами см. в разделе [оператор Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md) и [неявное преобразование делегата](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md).  
  
## <a name="lambda-expression-syntax"></a>Синтаксис лямбда-выражений  
 Синтаксис лямбда-выражение напоминает стандартной функции. Ниже приведены различия.  
  
-   Лямбда-выражение не имеет имени.  
  
-   Лямбда-выражения не могут иметь модификаторы, такие как `Overloads` или `Overrides`.  
  
-   Лямбда-выражения не используйте `As` предложение для обозначения типом возвращаемого значения функции. Вместо этого тип выводится из, текст Однострочные лямбда-выражение, результатом которого является значение или возвращаемое значение многострочных лямбда-выражения. Например, если текст Однострочные лямбда-выражения `Where cust.City = "London"`, возвращается тип `Boolean`.  
  
-   Тело Однострочные лямбда-выражения должно быть выражением, а не оператором. Текст может состоять из вызова процедуры function, но не вызов процедуры sub.  
  
-   Все параметры должно было быть задано, что необходимо определить типы данных или все.  
  
-   Параметры необязательно и Paramarray не разрешены.  
  
-   Универсальные параметры не допускаются.  
  
## <a name="example"></a>Пример  
 В следующих примерах показано два способа создания простых лямбда-выражений. Первый использует `Dim` для предоставления имени функции. Для вызова функции, отправить значение параметра.  
  
 [!code-vb[VbVbalrLambdas&#1;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_1.vb)]  
  
 [!code-vb[VbVbalrLambdas&#2;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_2.vb)]  
  
## <a name="example"></a>Пример  
 Кроме того можно объявить и запустить функцию одновременно.  
  
 [!code-vb[VbVbalrLambdas&#3;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_3.vb)]  
  
## <a name="example"></a>Пример  
 Ниже приведен пример лямбда-выражения, которое увеличивает значение своего аргумента и возвращает значение. В этом примере синтаксис однострочные и многострочные лямбда-выражений для функции. Дополнительные примеры см. в разделе [лямбда-выражения](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 [!code-vb[VbVbalrLambdas&#14;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/function-expression_4.vb)]  
  
## <a name="example"></a>Пример  
 Лямбда-выражения лежат в основе многих операторов запроса в [!INCLUDE[vbteclinqext](../../../csharp/getting-started/includes/vbteclinqext_md.md)]и может использоваться в запросах на основе методов явным образом. В следующем примере показано типичное [!INCLUDE[vbteclinq](../../../csharp/includes/vbteclinq_md.md)] запрос, с приведением результата запроса в формат метода.  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 Дополнительные сведения о методах запросов см. в разделе [запросов](../../../visual-basic/language-reference/queries/queries.md). Дополнительные сведения о стандартных операторах запросов см. в разделе [Общие сведения о стандартных операторах запроса](http://msdn.microsoft.com/library/24cda21e-8af8-4632-b519-c404a839b9b2).  
  
## <a name="see-also"></a>См. также  
 [Оператор Function](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Лямбда-выражения](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)   
 [Операторы и выражения](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)   
 [Инструкции](../../../visual-basic/programming-guide/language-features/statements.md)   
 [Сравнение значений](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)   
 [Логические выражения](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)   
 [Если оператор](../../../visual-basic/language-reference/operators/if-operator.md)   
 [Неявное преобразование делегата](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)

