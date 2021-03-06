---
title: "Настраиваемое действие SendMail | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# Настраиваемое действие SendMail
В образце описывается создание настраиваемого действия, которое является производным от <xref:System.Activities.AsyncCodeActivity>, для отправки почты с помощью SMTP для работы в приложении рабочего процесса.В настраиваемом действии для асинхронной отправки электронной почты и отправки почты с проверкой подлинности используются функции <xref:System.Net.Mail.SmtpClient>.При этом также обеспечивается возможность использования таких функций конечных пользователей, как тестовый режим, замена маркеров, шаблоны файлов и тестовый путь размещения файла.  
  
 В следующей таблице представлены аргументы для действия `SendMail`.  
  
||||  
|-|-|-|  
|Имя|Тип|Описание|  
|Host|String|Адрес узла SMTP\-сервера.|  
|Port|String|Порт службы SMTP на узле.|  
|EnableSsl|bool|Указывает, использует ли <xref:System.Net.Mail.SmtpClient> протокол SSL для шифрования соединения.|  
|UserName|String|Имя пользователя для настройки учетных данных для проверки подлинности свойства <xref:System.Net.Mail.SmtpClient.Credentials%2A> отправителя.|  
|Password|String|Пароль для настройки учетных данных для проверки подлинности свойства <xref:System.Net.Mail.SmtpClient.Credentials%2A> отправителя.|  
|Subject|<xref:System.Activities.InArgument%601>\<string\>|Тема сообщения.|  
|Body|<xref:System.Activities.InArgument%601>\<string\>|Текст сообщения.|  
|Attachments|<xref:System.Activities.InArgument%601>\<string\>|Коллекция вложений, используемая для хранения данных, вложенных в это сообщение электронной почты.|  
|From|<xref:System.Net.Mail.MailAddress>|Адрес электронной почты отправителя для этого сообщения.|  
|To|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>\>|Коллекция адресов получателей данного сообщения электронной почты.|  
|CC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>\>|Коллекция адресов получателей копии \(CC\) данного сообщения электронной почты.|  
|BCC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>\>|Коллекция адресов получателей скрытой копии \(BCC\) данного сообщения электронной почты.|  
|Tokens|<xref:System.Activities.InArgument%601>\<IDictionary\<string, string\>\>|Маркеры для замены в тексте.Эта функция позволяет пользователям указывать определенные значением в тексте сообщения, которые можно позднее заменить маркерами, предоставляемыми при использовании этого свойства.|  
|BodyTemplateFilePath|String|Путь к шаблону текста.Действие `SendMail` копирует содержимое этого файла в свойство текста.<br /><br /> Этот шаблон может содержать токены, которые заменяются на содержимое свойства Tokens.|  
|TestMailTo|<xref:System.Net.Mail.MailAddress>|Если задано это свойство, все сообщения электронной почты отправляются на адрес, указанный в этом свойстве.<br /><br /> Это свойство планируется использовать при тестировании рабочих процессов.Например, оно используется, если необходимо убедиться в отправке всех сообщений электронной почты без фактического выполнения отправки адресатам.|  
|TestDropPath|String|Если это свойство задано, все сообщения электронной почты сохраняются в указанном файле.<br /><br /> Это свойство планируется использовать при тестировании или отладке рабочих процессов в ситуациях, когда необходимо убедиться, что для исходящих сообщений электронной почты выбран правильный формат и содержимое.|  
  
## Содержимое решения  
 Решение содержит два проекта.  
  
|Проект|Описание|Важные файлы|  
|------------|--------------|------------------|  
|SendMail|Действие SendMail|1.  SendMail.cs: реализация для основных действий<br />2.  SendMailDesigner.xaml и SendMailDesigner.xaml.cs:конструктор для действия SendMail<br />3.  MailTemplateBody.htm: шаблон для исходящих сообщений электронной почты.|  
|SendMailTestClient|Клиент для тестирования действий SendMail.В этом проекте описываются два способа вызова действия SendMail: декларативно и программно.|1.  Sequence1.xaml: рабочий процесс, вызывающий действие SendMail.<br />2.  Program.cs: вызывает Sequence1, а также программно создает рабочий процесс, который использует SendMail.|  
  
## Дополнительная настройка действия SendMail  
 Хотя она не показана в образце, пользователи могут выполнять дополнительную настройку действия SendMail.Эта дополнительная настройка описывается в следующих трех разделах.  
  
### Отправка сообщения электронной почты с использованием маркеров, указанных в тексте сообщения  
 В этом фрагменте кода описывается отправка сообщения электронной почты с маркеров в тексте сообщения.Обратите внимание на то, как маркеры включены в текст сообщения.Значения для этих маркеров предоставлены для свойства маркеров.  
  
```html  
IDictionary<string, string> tokens = new Dictionary<string, string>();  
tokens.Add("@name", "John Doe");  
tokens.Add("@date", DateTime.Now.ToString());  
tokens.Add("@server", "localhost");  
  
new SendMail  
{  
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Body = "Hello @name. This is a test email sent from @server. Current date is @date",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens)  
};  
  
```  
  
### Отправка сообщения электронной почты с использованием шаблона  
 В этом фрагменте описывается отправка сообщения электронной почты с использованием токенов шаблона в тексте.Обратите внимание, что при задании свойства `BodyTemplateFilePath` не нужно указывать значение для свойства Body \(содержимое файла шаблона будет скопировано в текст\).  
  
```  
new SendMail  
{    
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
    BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",   
};  
  
```  
  
### Отправка сообщений в тестовом режиме  
 В этом фрагменте кода описано задание двух свойств тестирования: при задании `TestMailTo` все сообщения будут отправляться на адрес john.doe@contoso.con \(независимо от значений To, Cc, Bcc\).При задании TestDropPath все исходящие сообщения электронной почты будут также записываться по указанному пути.Эти свойства могут быть заданы независимо \(они не связаны друг с другом\).  
  
```  
new SendMail  
{    
   From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
   Subject = "Test email",  
   Host = "localhost",  
   Port = 25,  
   Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
   BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",  
   TestMailTo= new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   TestDropPath = @"c:\Samples\SendMail\TestDropPath\",  
};  
  
```  
  
## Инструкции по установке  
 В этом образце необходим доступ к SMTP\-серверу.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]настройке SMTP\-сервера см. на следующих страницах:  
  
-   [Microsoft Technet](http://go.microsoft.com/fwlink/?LinkId=166060)  
  
-   [Настройка службы SMTP \(IIS 6.0\)](http://go.microsoft.com/fwlink/?LinkId=150456)  
  
-   [IIS 7.0: настройка протокола электронной почты SMTP](http://go.microsoft.com/fwlink/?LinkId=150457)  
  
-   [Установка службы SMTP](http://go.microsoft.com/fwlink/?LinkId=150458)  
  
 Эмуляторы SMTP разработки сторонних производителей можно загрузить из Интернета.  
  
##### Запуск образца  
  
1.  С помощью [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] откройте файл решения SendMail.sln.  
  
2.  Убедитесь, что имеется доступ к работающему SMTP\-серверу.См. инструкции по настройке.  
  
3.  Настройте программу, задав адрес сервера и указав адреса электронной почты отправителя и адресата.  
  
     Чтобы правильно выполнить этот образец, может потребоваться настройка значений адресов электронной почты отправителя и адресата, а также адреса SMTP\-сервера в Program.cs и Sequence.xaml.Потребуется изменение адреса в обоих расположениях, поскольку программа отправляет сообщения двумя различными способами  
  
4.  Для построения решения нажмите CTRL\+SHIFT\+B.  
  
5.  Чтобы запустить решение, нажмите клавиши CTRL\+F5.  
  
> [!IMPORTANT]
>  Образцы уже могут быть установлены на компьютере.Перед продолжением проверьте следующий каталог \(по умолчанию\).  
>   
>  `<диск_установки>:\WF_WCF_Samples`  
>   
>  Если этот каталог не существует, перейдите на страницу [Образцы Windows Communication Foundation \(WCF\) и Windows Workflow Foundation \(WF\) для .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780), чтобы загрузить все образцы [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] и [!INCLUDE[wf1](../../../../includes/wf1-md.md)].Этот образец расположен в следующем каталоге.  
>   
>  `<диск_установки>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`  
  
## См. также