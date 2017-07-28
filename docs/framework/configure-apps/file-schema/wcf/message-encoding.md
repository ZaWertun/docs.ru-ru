---
title: "Message Encoding | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: f30ee941-aca9-4c67-82a5-421568496f07
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# Message Encoding
Кодирование \- это процесс преобразования набора символов Юникода в последовательность байтов.  Декодирование представляет собой обратный процесс.  В Windows Communication Foundation \(WCF\) имеется три типа кодирования для сообщений SOAP: Text, Binary и MTOM.  
  
 В разделе конфигурации `binaryMessageEncoding` указывается кодировка символов и управление версиями сообщений, используемые для двоичных сообщений XML.  Кодировщик двоичных сообщений кодирует сообщения Windows Communication Foundation \(WCF\) в двоичном формате в сети.  Результатом этой кодировки является очень быстрая передача сообщений, однако вследствие этого теряются возможности взаимодействия, основанные на стандартах WS\-\*.  
  
 В разделе конфигурации `mtomMessageEncoding` указывается кодировка символов и управление версиями сообщений, используемые для сообщения с помощью кодирования MTOM \(Message Transmission Optimization Mechanism\).  MTOM \- это эффективная технология для передачи двоичных данных в сообщениях Windows Communication Foundation.  Кодировщик MTOM предпринимает попытку соблюсти баланс между эффективностью и взаимодействием.  Кодирование MTOM передает большую часть XML\-данных в текстовой форме, но оптимизирует большие блоки двоичных данных путем передачи их в исходном виде, без преобразования в текст.  
  
 В разделе конфигурации `textMessageEncoding` указывается кодировщик текста, используемый для создания текстовых сообщений в сети.  Сообщения, созданные этим кодировщиком, подходят для взаимодействия на базе \+WS\-\*.  Веб\-служба или клиент веб\-службы в общем могут понимать XML в текстовом виде.  Однако передача больших блоков двоичных данных в виде текста является наименее эффективным методом для кодировки сообщений XML.  
  
## См. также  
 <xref:System.ServiceModel.Channels.CustomBinding>   
 <xref:System.ServiceModel.Channels.MessageEncodingBindingElement>   
 [Привязки](../../../../../docs/framework/wcf/bindings.md)   
 [Расширение привязок](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
 [Пользовательские привязки](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [\<customBinding\>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)   
 [Выбор кодировщика сообщений](../../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)