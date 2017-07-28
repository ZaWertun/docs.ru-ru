---
title: "Безопасность сообщений при использовании клиентом сертификата | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 99770573-c815-4428-a38c-e4335c8bd7ce
caps.latest.revision: 16
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 16
---
# Безопасность сообщений при использовании клиентом сертификата
В следующем сценарии показаны служба и клиент [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], защищенные с помощью режима безопасности сообщений.Проверка подлинности клиента и службы выполняется с помощью сертификатов.[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Защита распределенных приложений](../../../../docs/framework/wcf/feature-details/distributed-application-security.md).  
  
 Пример приложения см. в разделе [Сертификат безопасности сообщений](../../../../docs/framework/wcf/samples/message-security-certificate.md).  
  
 ![Клиент с сертификатом](../../../../docs/framework/wcf/feature-details/media/clientwithcertificate.gif "ClientWithCertificate")  
  
|Характеристика|Описание|  
|--------------------|--------------|  
|Режим безопасности|Сообщение|  
|Взаимодействие|Только [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]|  
|Проверка подлинности \(сервера\)|Использование сертификатов служб|  
|Проверка подлинности \(клиента\)|Использование сертификатов клиента|  
|Целостность|Да|  
|Конфиденциальность|Да|  
|Транспорт|HTTP|  
|Привязка|<xref:System.ServiceModel.WSHttpBinding>|  
  
## Служба  
 Предполагается, что представленные ниже код и конфигурация выполняются независимо.Выполните одно из следующих действий.  
  
-   Создайте автономную службу, используя код без конфигурации.  
  
-   Создайте службу, используя предоставленную конфигурацию, но не определяйте конечные точки.  
  
### Код  
 В следующем коде показано создание конечной точки службы, которая использует безопасность сообщений для установления защищенного контекста.  
  
 [!code-csharp[C_SecurityScenarios#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#10)]
 [!code-vb[C_SecurityScenarios#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#10)]  
  
### Конфигурация  
 Вместо кода можно использовать следующую конфигурацию.  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="ServiceCredentialsBehavior">  
          <serviceCredentials>  
            <serviceCertificate findValue="Contoso.com"  
                                x509FindType="FindBySubjectName" />  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service behaviorConfiguration="ServiceCredentialsBehavior"   
               name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="MessageAndCerficiateClient"   
                  name="SecuredByClientCertificate"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator">  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## Клиент  
 Предполагается, что представленные ниже код и конфигурация выполняются независимо.Выполните одно из следующих действий.  
  
-   Создайте автономный клиент, используя код \(и код клиента\).  
  
-   Создайте клиент, который не определяет никаких адресов конечных точек.Вместо этого используйте конструктор клиента, который принимает в качестве аргумента имя конфигурации.Пример:  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### Код  
 Следующий код служит для создания клиента.Привязка осуществляется к безопасности режима сообщений, и типу учетных данных клиента присваивается значение `Certificate`.  
  
 [!code-csharp[C_SecurityScenarios#17](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#17)]
 [!code-vb[C_SecurityScenarios#17](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#17)]  
  
### Конфигурация  
 В следующей конфигурации задается сертификат клиента с помощью поведения конечной точки.Дополнительные сведения о сертификатах см. в разделе [Работа с сертификатами](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).В коде также используется элемент \<`identity`\>, определяющий службу доменных имен \(DNS\) ожидаемой идентификации сервера.[!INCLUDE[crabout](../../../../includes/crabout-md.md)] удостоверениях см. в разделе [Идентификация и проверка подлинности службы](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="endpointCredentialsBehavior">  
          <clientCredentials>  
            <clientCertificate findValue="Cohowinery.com"   
               storeLocation="LocalMachine"  
              x509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>  
      </endpointBehaviors>  
    </behaviors>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Message">  
            <message clientCredentialType="Certificate" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="http://machineName/Calculator"   
                behaviorConfiguration="endpointCredentialsBehavior"  
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"  
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator">  
        <identity>  
          <dns value="Contoso.com" />  
        </identity>  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## См. также  
 [Общие сведения о безопасности](../../../../docs/framework/wcf/feature-details/security-overview.md)   
 [Идентификация и проверка подлинности службы](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)   
 [Работа с сертификатами](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [Модель безопасности для Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x419)