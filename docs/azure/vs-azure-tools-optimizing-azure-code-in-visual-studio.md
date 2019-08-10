---
title: Optymalizacja kodu platformy Azure
description: Dowiedz się o kodzie jak usługa Azure pomóc sprawić, że kod bardziej niezawodnego i lepszego wykonywania optymalizacji narzędzi w programie Visual Studio.
author: ghogen
manager: jillfra
ms.assetid: ed48ee06-e2d2-4322-af22-07200fb16987
ms.topic: conceptual
ms.custom: seodec18
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 3f9094b4d668df37c25da075d0cee590052f910d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919815"
---
# <a name="optimizing-your-azure-code"></a>Optymalizacja kodu platformy Azure
Podczas programowania używasz aplikacje korzystające z Microsoft Azure, istnieją pewne praktyk kodowania, które należy wykonać, aby pomóc uniknąć problemów z skalowalność aplikacji, zachowanie i wydajność w środowisku chmury. Firma Microsoft udostępnia narzędzia do analizy kodu platformy Azure, rozpoznaje i identyfikuje kilka z tych problemów często napotykanych i pomoże Ci je rozwiązać. Możesz pobrać narzędzia w programie Visual Studio za pomocą narzędzia NuGet.

## <a name="azure-code-analysis-rules"></a>Usługa Azure reguł analizy kodu
Narzędzie do analizy kodu Azure używa następujących reguł do automatycznie Flaga kodu platformy Azure w przypadku znalezienia znanych problemów wpływających na wydajność. Wykryto problemy są wyświetlane jako ostrzeżenia lub błędy kompilatora. Poprawki kodu lub sugestie, aby rozwiązać ostrzeżenia lub błędu, często znajdują się za pomocą ikony żarówki.

## <a name="avoid-using-default-in-process-session-state-mode"></a>Unikaj używania domyślny tryb stanu sesji (w procesie)
### <a name="id"></a>ID
AP0000

### <a name="description"></a>Opis
Jeśli używasz domyślny tryb stanu sesji (w procesie) dla aplikacji w chmurze może utracić stanu sesji.

Udostępnij swoje pomysły i opinie na [opinii analizy kodu Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Przyczyna
Domyślnie tryb stanu sesji, które są określone w pliku web.config jest w trakcie. Ponadto jeśli żadnego wpisu określone w pliku konfiguracji, tryb stanu sesji domyślnie w procesie. Tryb w procesie przechowuje stanu sesji w pamięci na serwerze sieci web. Po ponownym uruchomieniu wystąpienia lub nowe wystąpienie jest używany do równoważenia obciążenia lub obsługę trybu failover, stan sesji, przechowywane w pamięci na serwerze sieci web nie są zapisywane. Ta sytuacja zapobiega aplikację jest skalowalna w chmurze.

Stan sesji ASP.NET obsługuje kilka różnych opcji magazynu dla danych stanu sesji: InProc, StateServer, SQLServer, Custom i off. Zaleca się używać trybu niestandardowego do przechowywania danych na zewnętrznego magazynu stanu sesji, takie jak [dostawcy stanu sesji usługi Azure redis Cache](http://go.microsoft.com/fwlink/?LinkId=401521).

### <a name="solution"></a>Rozwiązanie
Jedno rozwiązanie zalecane jest przechowywanie stanu sesji usługi zarządzana pamięć podręczna. Dowiedz się, jak używać [dostawcy stanu sesji usługi Azure redis Cache](http://go.microsoft.com/fwlink/?LinkId=401521) do przechowywania Twojego stanu sesji. Można również przechowywanie stanu sesji w innych miejscach, aby upewnić się, że aplikacja jest skalowalna w chmurze. Aby dowiedzieć się więcej na temat rozwiązań alternatywnych, przeczytaj [trybów stanu sesji](https://msdn.microsoft.com/library/ms178586).

## <a name="run-method-should-not-be-async"></a>Uruchom metody nie powinny być asynchroniczne
### <a name="id"></a>ID
AP1000

### <a name="description"></a>Opis
Tworzenie metod asynchronicznych (takie jak [await](https://msdn.microsoft.com/library/hh156528.aspx)) poza [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) metody, a następnie wywołać metody asynchroniczne z [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx). Deklarowanie [ [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) metody async powoduje, że rola procesu roboczego wprowadzić w pętli ponownego uruchamiania.

Udostępnij swoje pomysły i opinie na [opinii analizy kodu Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Przyczyna
Wywołanie metod asynchronicznych wewnątrz [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) metoda powoduje odtwarzanie roli procesu roboczego środowiska uruchomieniowego usługi chmury. Podczas uruchamiania roli proces roboczy, wszystkie wykonywania programu odbywa się wewnątrz [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) metody. Kończenie [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) metoda powoduje ponowne uruchomienie roli procesu roboczego. Gdy środowisko uruchomieniowe roli procesu roboczego osiągnie metody asynchronicznej, wysyła wszystkie operacje po metody asynchronicznej, a następnie zwraca. Powoduje to, że rola procesu roboczego wyjść z [ [ [ [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) metody i ponowne uruchomienie. W następnej iteracji wykonywania roli procesu roboczego osiągnie metody asynchronicznej ponownie i powoduje ponowne uruchomienie, co powoduje także ponownie odtwarzanie roli procesu roboczego.

### <a name="solution"></a>Rozwiązanie
Umieść wszystkie operacje asynchroniczne poza [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) metody. Następnie wywołaj metodę async wycofany z wewnątrz [ [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) ](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) metody, takiej jak .wait () RunAsync. Narzędzie do analizy kodu platformy Azure może pomóc rozwiązać ten problem.

Poniższy fragment kodu przedstawia poprawki kodu dla tego problemu:

```csharp
public override void Run()
{
    RunAsync().Wait();
}

public async Task RunAsync()
{
    //Asynchronous operations code logic
    // This is a sample worker implementation. Replace with your logic.

    Trace.TraceInformation("WorkerRole1 entry point called");

    HttpClient client = new HttpClient();

    Task<string> urlString = client.GetStringAsync("https://msdn.microsoft.com");

    while (true)
    {
        Thread.Sleep(10000);
        Trace.TraceInformation("Working");

        string stream = await urlString;
    }

}
```

## <a name="use-service-bus-shared-access-signature-authentication"></a>Korzystanie z uwierzytelniania usługi Service Bus Shared Access Signature
### <a name="id"></a>ID
AP2000

### <a name="description"></a>Opis
Sygnatury dostępu współdzielonego (SAS) używany do uwierzytelniania. Access Control Service (ACS) jest przestarzałe i zastępowane przez uwierzytelniania w usłudze service bus.

Udostępnij swoje pomysły i opinie na [opinii analizy kodu Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Przyczyna
Aby zwiększyć bezpieczeństwo usługi Azure Active Directory zastępuje ACS uwierzytelniania przy użyciu uwierzytelniania sygnatury dostępu Współdzielonego. Zobacz [usługi Azure Active Directory to przyszłość ACS](https://cloudblogs.microsoft.com/enterprisemobility/2013/06/22/azure-active-directory-is-the-future-of-acs/) uzyskać informacji na temat planu migracji.

### <a name="solution"></a>Rozwiązanie
Korzystanie z uwierzytelniania sygnatury dostępu Współdzielonego w aplikacjach. Poniższy przykład pokazuje, jak uzyskać dostęp do przestrzeni nazw usługi service bus lub jednostki za pomocą istniejącego tokenu sygnatury dostępu Współdzielonego.

```csharp
MessagingFactory listenMF = MessagingFactory.Create(endpoints, new StaticSASTokenProvider(subscriptionToken));
SubscriptionClient sc = listenMF.CreateSubscriptionClient(topicPath, subscriptionName);
BrokeredMessage receivedMessage = sc.Receive();
```

Zobacz następujące tematy, aby uzyskać więcej informacji.

* Aby uzyskać przegląd, zobacz [udostępnione uwierzytelniania sygnatury dostępu za pomocą usługi Service Bus](https://msdn.microsoft.com/library/dn170477.aspx)
* [Jak używać udostępnionego uwierzytelniania sygnatury dostępu z usługi Service Bus](https://msdn.microsoft.com/library/dn205161.aspx)
* Aby uzyskać przykładowy projekt, zobacz [uwierzytelniania przy użyciu sygnatury dostępu współdzielonego (SAS) za pomocą subskrypcji magistrali usług](http://code.msdn.microsoft.com/windowsazure/Using-Shared-Access-e605b37c)

## <a name="consider-using-onmessage-method-to-avoid-receive-loop"></a>Należy wziąć pod uwagę przy użyciu metody OnMessage, aby uniknąć "otrzymywać pętli"
### <a name="id"></a>ID
AP2002

### <a name="description"></a>Opis
Aby uniknąć "otrzymywać pętli" wywoływania **OnMessage** metodą jest lepszym rozwiązaniem do odbierania wiadomości od wywołania **Receive** metody. Jednakże jeśli musisz użyć **Receive** metody i określić czas oczekiwania serwera innych niż domyślne, upewnij się, czas oczekiwania serwera jest więcej niż jedną minutę.

Udostępnij swoje pomysły i opinie na [opinii analizy kodu Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Przyczyna
Podczas wywoływania **OnMessage**, klient uruchamia wewnętrznego "pompy komunikatów" sondujący stale kolejki lub subskrypcji. Ta "pompy komunikatów" zawiera wejścia w nieskończoną pętlę, która generuje wywołanie w celu odbierania komunikatów. Jeśli upłynie limit czasu wywołania, wystawia nowe połączenie. Interwał limitu czasu jest określany przez wartość [OperationTimeout](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactorysettings.operationtimeout.aspx) właściwość [MessagingFactory](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactory.aspx)jest on używany.

Zaletą korzystania z **OnMessage** w porównaniu do **Receive** jest, że użytkownicy nie musieli ręcznie sondowania pod kątem komunikatów, obsługa wyjątków, przetwarzanie wielu komunikatów jednocześnie i ukończyć komunikaty.

Jeśli wywołasz **Receive** bez użycia jego wartość domyślną, upewnij się, *ServerWaitTime* wartość jest więcej niż jedną minutę. Ustawienie *ServerWaitTime* na więcej niż jedną minutę zapobiega serwera limit czasu, zanim pełni odebraniu komunikatu.

### <a name="solution"></a>Rozwiązanie
Zobacz poniższe przykłady kodu dla zalecanych użycia. Aby uzyskać więcej informacji, zobacz [QueueClient. OnMessage Metoda (Microsoft. ServiceBus. Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.onmessage.aspx) i [QueueClient. Receive — Metoda (Microsoft. ServiceBus. Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.receive.aspx).

Aby zwiększyć wydajność platformy Azure infrastruktura obsługi komunikatów, zobacz wzorzec projektowy [asynchronicznej obsługi komunikatów Elementarz](https://msdn.microsoft.com/library/dn589781.aspx).

Oto przykład użycia **OnMessage** do odbierania komunikatów.

```csharp
void ReceiveMessages()
{
    // Initialize message pump options.
    OnMessageOptions options = new OnMessageOptions();
    options.AutoComplete = true; // Indicates if the message-pump should call complete on messages after the callback has completed processing.
    options.MaxConcurrentCalls = 1; // Indicates the maximum number of concurrent calls to the callback the pump should initiate.
    options.ExceptionReceived += LogErrors; // Enables you to get notified of any errors encountered by the message pump.

    // Start receiving messages.
    QueueClient client = QueueClient.Create("myQueue");
    client.OnMessage((receivedMessage) => // Initiates the message pump and callback is invoked for each message that is received, calling close on the client will stop the pump.
    {
        // Process the message.
    }, options);
    Console.WriteLine("Press any key to exit.");
    Console.ReadKey();
```

Oto przykład użycia **Receive** czas oczekiwania, serwer domyślny.

```csharp
string connectionString =
CloudConfigurationManager.GetSetting("Microsoft.ServiceBus.ConnectionString");

QueueClient Client =
    QueueClient.CreateFromConnectionString(connectionString, "TestQueue");

while (true)
{
   BrokeredMessage message = Client.Receive();
   if (message != null)
   {
      try
      {
         Console.WriteLine("Body: " + message.GetBody<string>());
         Console.WriteLine("MessageID: " + message.MessageId);
         Console.WriteLine("Test Property: " +
            message.Properties["TestProperty"]);

         // Remove message from queue
         message.Complete();
      }

      catch (Exception)
      {
         // Indicate a problem, unlock message in queue
         message.Abandon();
      }
   }
```

Oto przykład użycia **Receive** czas oczekiwania, serwer inny niż domyślny.

```csharp
while (true)
{
   BrokeredMessage message = Client.Receive(new TimeSpan(0,1,0));

   if (message != null)
   {
      try
      {
         Console.WriteLine("Body: " + message.GetBody<string>());
         Console.WriteLine("MessageID: " + message.MessageId);
         Console.WriteLine("Test Property: " +
            message.Properties["TestProperty"]);

         // Remove message from queue
         message.Complete();
      }

      catch (Exception)
      {
         // Indicate a problem, unlock message in queue
         message.Abandon();
      }
   }
}
```

## <a name="consider-using-asynchronous-service-bus-methods"></a>Należy rozważyć użycie metod asynchronicznych usługi Service Bus
### <a name="id"></a>ID
AP2003

### <a name="description"></a>Opis
Użyj metod asynchronicznych usługi Service Bus, aby zwiększyć wydajność przy użyciu komunikatów obsługiwanych przez brokera.

Udostępnij swoje pomysły i opinie na [opinii analizy kodu Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Przyczyna
Używanie metod asynchronicznych umożliwia aplikacji program współbieżność, ponieważ wykonywania każdego wywołania nie blokuje wątku głównego. Korzystając z usługi Service Bus messaging metod, wykonywania operacji (wysyłanie, odbieranie, usunąć itp.) zajmuje trochę czasu. Teraz obejmuje przetwarzanie operacji w usłudze Service Bus, poza tym zwiększa opóźnienia żądania i odpowiedzi. Aby zwiększyć liczbę operacji na czas, jednocześnie muszą wykonać operacje. Aby uzyskać więcej informacji można znaleźć [najlepsze rozwiązania dotyczące wydajności ulepszenia przy użyciu brokera komunikatów usługi Service Bus](https://msdn.microsoft.com/library/azure/hh528527.aspx).

### <a name="solution"></a>Rozwiązanie
Zobacz [QueueClient klasy (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.aspx) informacji o sposobie używania zalecaną metodą asynchroniczną.

Aby zwiększyć wydajność platformy Azure infrastruktura obsługi komunikatów, zobacz wzorzec projektowy [asynchronicznej obsługi komunikatów Elementarz](https://msdn.microsoft.com/library/dn589781.aspx).

## <a name="consider-partitioning-service-bus-queues-and-topics"></a>Należy wziąć pod uwagę partycjonowania tematów i kolejek usługi Service Bus
### <a name="id"></a>ID
AP2004

### <a name="description"></a>Opis
Kolejki usługi Service Bus partycji i tematów w celu zapewnienia lepszej wydajności przy użyciu komunikatów usługi Service Bus.

Udostępnij swoje pomysły i opinie na [opinii analizy kodu Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Przyczyna
Partycjonowanie tematów i kolejek usługi Service Bus, ponieważ ogólną przepływność podzieleniu kolejki lub tematu nie jest już ograniczone przez wydajności pojedynczego brokera lub magazynu komunikatów zwiększa to dostępność przepływności i usługi wydajności. Ponadto tymczasowe awarii magazynu komunikatów nie czyni podzieleniu kolejki lub tematu niedostępny. Aby uzyskać więcej informacji, zobacz [partycjonowanie jednostki obsługi komunikatów](https://msdn.microsoft.com/library/azure/dn520246.aspx).

### <a name="solution"></a>Rozwiązanie
Poniższy fragment kodu przedstawia sposób partycjonowanie jednostki do obsługi komunikatów.

```csharp
// Create partitioned topic.
NamespaceManager ns = NamespaceManager.CreateFromConnectionString(myConnectionString);
TopicDescription td = new TopicDescription(TopicName);
td.EnablePartitioning = true;
ns.CreateTopic(td);
```

Aby uzyskać więcej informacji, zobacz [partycjonowane kolejki usługi Service Bus i tematy | Blog platformy Microsoft Azure](https://azure.microsoft.com/blog/2013/10/29/partitioned-service-bus-queues-and-topics/) i zapoznaj się z [Microsoft Azure partycjonowane kolejki usługi Service Bus](https://code.msdn.microsoft.com/windowsazure/Service-Bus-Partitioned-7dfd3f1f) próbki.

## <a name="do-not-set-sharedaccessstarttime"></a>Nie należy ustawiać SharedAccessStartTime
### <a name="id"></a>ID
AP3001

### <a name="description"></a>Opis
Należy unikać używania SharedAccessStartTimeset bieżący czas, aby natychmiast uruchomić zasady dostęp współdzielony. Należy ustawić tę właściwość, jeśli chcesz uruchomić zasady dostępu udostępnione w późniejszym czasie.

Udostępnij swoje pomysły i opinie na [opinii analizy kodu Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Przyczyna
Synchronizacja zegara powoduje, że różnica czasu nieznaczne między centrami danych. Na przykład logicznie myślisz, ustawienie czas rozpoczęcia magazynu zasad sygnatury dostępu Współdzielonego jako bieżący czas przy użyciu DateTime.Now lub podobnej metody spowoduje, że zasady sygnatury dostępu Współdzielonego i zaczynają obowiązywać natychmiast. Jednak czas niewielkie różnice między centrami danych może spowodować problemy z tym, ponieważ sytuacje centrum danych mogą być nieco później niż czas rozpoczęcia, podczas gdy inne wcześniej go. Co w efekcie zasad sygnatury dostępu Współdzielonego można unieważnić szybko (lub nawet natychmiast) Jeśli okres istnienia zasad ustawiono zbyt krótki.

Aby uzyskać więcej wskazówek na temat używania sygnatura dostępu współdzielonego w usłudze Azure storage, zobacz [wprowadzenie do tabeli SAS (Shared Access Signature) sygnatury dostępu Współdzielonego kolejki i przeprowadź aktualizację do połączenie SAS obiektu Blob - Storage Blog zespołu Microsoft Azure — strona główna — lokacji blogi MSDN](http://blogs.msdn.com/b/windowsazurestorage/archive/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas.aspx).

### <a name="solution"></a>Rozwiązanie
Usuń instrukcję, która ustawia czas rozpoczęcia zasady dostępu współdzielonego. Narzędzia analizy kodu platformy Azure zawiera poprawkę rozwiązującą ten problem. Aby uzyskać więcej informacji na temat zarządzania zabezpieczeniami, zobacz wzorzec projektowy [wzorzec klucza Portiera](https://msdn.microsoft.com/library/dn568102.aspx).

Poniższy fragment kodu pokazuje poprawki kodu dla tego problemu.

```csharp
// The shared access policy provides
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
   SharedAccessExpiryTime = DateTime.UtcNow.AddHours(10),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

## <a name="shared-access-policy-expiry-time-must-be-more-than-five-minutes"></a>Udostępnione zasady dostępu, czas wygaśnięcia musi być więcej niż pięć minut
### <a name="id"></a>ID
AP3002

### <a name="description"></a>Opis
Może być jak pięciu minut różnica w zegary między centrami danych w różnych lokalizacjach z powodu warunku, znane jako "zegara." Aby zapobiec sygnatury dostępu Współdzielonego tokenu zasad przed wygaśnięciem wcześniej, niż planowano, ustaw czas wygaśnięcia to więcej niż pięć minut.

Udostępnij swoje pomysły i opinie na [opinii analizy kodu Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Przyczyna
Centra danych w różnych lokalizacjach na całym świecie synchronizować sygnał zegara. Ponieważ zajmuje trochę czasu sygnał zegara przechodzić do różnych lokalizacji, może istnieć odchylenie czasu między centrami danych w różnych lokalizacjach geograficznych mimo, że wszystko, co prawdopodobnie jest zsynchronizowany. Ta różnica czasu może mieć wpływ na dostęp współdzielony zasad początek godziny i wygaśnięcia interwału. W związku z tym aby upewnić się, że zasady dostęp współdzielony ma efekt natychmiastowy, nie określić godzinę rozpoczęcia. Ponadto upewnij się, że czas wygaśnięcia jest więcej niż 5 minut, aby zapobiec wczesne limitu czasu.

Aby uzyskać więcej informacji o używaniu sygnatura dostępu współdzielonego dla usługi Azure storage, zobacz [wprowadzenie do tabeli SAS (Shared Access Signature) sygnatury dostępu Współdzielonego kolejki i przeprowadź aktualizację do połączenie SAS obiektu Blob - Storage Blog zespołu Microsoft Azure — strona główna — lokacji blogi MSDN](http://blogs.msdn.com/b/windowsazurestorage/archive/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas.aspx).

### <a name="solution"></a>Rozwiązanie
Aby uzyskać więcej informacji na temat zarządzania zabezpieczeniami, zobacz wzorzec projektowy [wzorzec klucza Portiera](https://msdn.microsoft.com/library/dn568102.aspx).

Oto przykład nie określając godziny rozpoczęcia zasady dostęp współdzielony.

```csharp
// The shared access policy provides
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
   SharedAccessExpiryTime = DateTime.UtcNow.AddHours(10),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

Oto przykład określenia godziny rozpoczęcia dostęp współdzielony zasad z okresem ważności zasad więcej niż pięć minut.

```csharp
// The shared access policy provides
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
  SharedAccessStartTime = new DateTime(2014,1,20),
 SharedAccessExpiryTime = new DateTime(2014, 1, 21),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

Aby uzyskać więcej informacji, zobacz [tworzenie i używanie sygnaturę dostępu współdzielonego](https://msdn.microsoft.com/library/azure/jj721951.aspx).

## <a name="use-cloudconfigurationmanager"></a>Użyj CloudConfigurationManager
### <a name="id"></a>ID
AP4000

### <a name="description"></a>Opis
Za pomocą [ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) klasy dla projektów, takich jak witryny sieci Web platformy Azure i usług Azure mobile services nie wprowadzić problemów w czasie wykonywania. Najlepszym rozwiązaniem jest jednak to dobry pomysł, aby używać chmury[ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) jako zunifikowany sposób zarządzania konfiguracjami dla wszystkich aplikacji w chmurze platformy Azure.

Udostępnij swoje pomysły i opinie na [opinii analizy kodu Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Przyczyna
CloudConfigurationManager odczytuje plik konfiguracyjny odpowiednie do środowiska aplikacji.

[CloudConfigurationManager](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx)

### <a name="solution"></a>Rozwiązanie
Refaktoryzacja kodu, aby użyć [klasa CloudConfigurationManager](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx). Kod poprawkę rozwiązującą ten problem jest zapewniana przez narzędzia analizy kodu platformy Azure.

Poniższy fragment kodu pokazuje poprawki kodu dla tego problemu. Zastąp

`var settings = ConfigurationManager.AppSettings["mySettings"];`

with

`var settings = CloudConfigurationManager.GetSetting("mySettings");`

Poniżej przedstawiono przykładowy sposób zapisać ustawienia konfiguracji w pliku App.config lub Web.config. Dodaj ustawienia w sekcji appSettings pliku konfiguracji. Poniżej znajduje się plik Web.config w poprzednim przykładzie kodu.

```xml
<appSettings>
    <add key="webpages:Version" value="3.0.0.0" />
    <add key="webpages:Enabled" value="false" />
    <add key="ClientValidationEnabled" value="true" />
    <add key="UnobtrusiveJavaScriptEnabled" value="true" />
    <add key="mySettings" value="[put_your_setting_here]"/>
  </appSettings>
```

## <a name="avoid-using-hard-coded-connection-strings"></a>Należy unikać używania ciągów połączeń zakodowanych
### <a name="id"></a>ID
AP4001

### <a name="description"></a>Opis
Jeśli musisz zaktualizować je później użyć ciągów połączeń zakodowanych, musisz wprowadzić zmiany do kodu źródłowego i ponownie skompilować aplikację. Jednak jeśli parametry połączenia są przechowywane w pliku konfiguracji, możesz zmienić je później, po prostu aktualizując plik konfiguracji.

Udostępnij swoje pomysły i opinie na [opinii analizy kodu Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Przyczyna
Trwałe kodowanie parametrów połączenia jest złym zwyczajem, ponieważ wprowadza ona problemy, gdy parametry połączenia muszą szybką zmianę. Ponadto jeśli projekt musi zostać zaewidencjonowane do kontroli źródła, ciągów połączeń zakodowanych wprowadzić luki w zabezpieczeniach, ponieważ ciągi mogą być wyświetlane w kodzie źródłowym.

### <a name="solution"></a>Rozwiązanie
Store parametry połączenia w środowiskach platformy Azure i plików konfiguracji.

* Dla aplikacji autonomicznej należy użyć pliku app.config do przechowywania ustawień parametrów połączenia.
* W przypadku aplikacji sieci web obsługiwane przez usługi IIS umożliwiają przechowywanie parametrów połączenia pliku web.config.
* W przypadku aplikacji ASP.NET vNext configuration.json do przechowywania używa parametrów połączenia.

Aby uzyskać informacje na temat korzystania z plików konfiguracji, takich jak plik web.config lub app.config, zobacz [wskazówki dotyczące konfigurowania sieci Web platformy ASP.NET](https://msdn.microsoft.com/library/vstudio/ff400235\(v=vs.100\).aspx). Aby dowiedzieć się, jak działają zmienne środowiskowe [platformy Azure, zobacz witryny sieci Web systemu Azure: Sposób działania](https://azure.microsoft.com/blog/2013/07/17/windows-azure-web-sites-how-application-strings-and-connection-strings-work/)ciągów aplikacji i parametrów połączenia. Aby uzyskać informacje na przechowywanie parametrów połączenia w kontroli źródła, zobacz [należy unikać umieszczania poufne informacje, takie jak parametry połączenia w plikach, które są przechowywane w repozytorium kodu źródłowego](http://www.asp.net/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control).

## <a name="use-diagnostics-configuration-file"></a>Użyj pliku konfiguracji diagnostyki
### <a name="id"></a>ID
AP5000

### <a name="description"></a>Opis
Zamiast konfigurować ustawienia diagnostyki w kodzie, takie jak za pomocą Microsoft.WindowsAzure.Diagnostics programowania interfejsu API, należy skonfigurować ustawienia diagnostyki, w pliku diagnostics.wadcfg. (Lub diagnostics.wadcfgx, jeśli używasz zestawu SDK Azure 2.5). Dzięki temu możesz zmienić ustawienia diagnostyki, bez konieczności ponownego kompilowania kodu.

Udostępnij swoje pomysły i opinie na [opinii analizy kodu Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Przyczyna
Przed Azure SDK 2.5, (która korzysta z usługi Diagnostyka Azure 1.3), usługi Azure Diagnostics (WAD) może zostać skonfigurowany przy użyciu kilku różnych metod: dodanie go do obiektu blob konfiguracji w magazynie, przy użyciu kodu imperatywnego, konfiguracja deklaratywne lub wartość domyślną Konfiguracja. Jednak preferowanym sposobem skonfigurowania diagnostyki jest użycie pliku konfiguracji XML (Diagnostics. wadcfg lub Diagnostics. wadcfgx dla zestawu SDK 2,5 i nowszego) w projekcie aplikacji. W tym podejściu pliku diagnostics.wadcfg całkowicie definiuje konfigurację można zaktualizować i ponownie wdrażana w momencie. Mieszanie korzystanie z pliku konfiguracji diagnostics.wadcfg przy użyciu metody programowe ustawienia konfiguracji za pomocą [DiagnosticMonitor](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.diagnosticmonitor.aspx)lub [RoleInstanceDiagnosticManager](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.management.roleinstancediagnosticmanager.aspx)można klas wprowadzać w błąd. Zobacz [inicjowania lub zmiana konfiguracji diagnostyki Azure](https://msdn.microsoft.com/library/azure/hh411537.aspx) Aby uzyskać więcej informacji.

Począwszy od 1.3 WAD (dołączone do zestawu SDK Azure 2.5), już nie jest możliwe użycie kodu, aby skonfigurować diagnostykę. Co w efekcie można podać tylko konfiguracji podczas stosowania lub aktualizowania rozszerzenie diagnostyki.

### <a name="solution"></a>Rozwiązanie
Użyj projektanta konfiguracji diagnostyki do przenoszenia ustawień diagnostycznych do pliku konfiguracji diagnostyki (Diagnostics. wadcfg lub Diagnostics. wadcfgx dla zestawu SDK 2,5 i nowszego). Zalecane jest również, że instalujesz program [Azure SDK 2.5](http://go.microsoft.com/fwlink/?LinkId=513188) i korzystać z najnowszych funkcji diagnostyki.

1. W menu skrótów dla roli, który chcesz skonfigurować wybierz polecenie Właściwości, a następnie wybierz kartę Konfiguracja.
2. W **diagnostyki** sekcji, upewnij się, że **Włącz diagnostykę** pole wyboru jest zaznaczone.
3. Wybierz **Konfiguruj** przycisku.

   ![Uzyskiwanie dostępu do opcji Włącz diagnostykę](./media/vs-azure-tools-optimizing-azure-code-in-visual-studio/IC796660.png)

   Zobacz [Konfigurowanie diagnostyki dla usług Azure Cloud Services i Virtual Machines](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md) Aby uzyskać więcej informacji.

## <a name="avoid-declaring-dbcontext-objects-as-static"></a>Należy unikać deklarowania obiektów typu DbContext jako statyczne
### <a name="id"></a>ID
AP6000

### <a name="description"></a>Opis
Aby zapisać pamięci, należy unikać deklarowania obiektów typu DBContext jako statyczne.

Udostępnij swoje pomysły i opinie na [opinii analizy kodu Azure](http://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Przyczyna
Obiekty typu DBContext przechowywania wyników zapytania, z każdym wywołaniu. Obiektów statycznych typu DBContext nie są usuwane, dopóki domena aplikacji jest zwalniana. W związku z tym statycznego obiektu DBContext może zużywać znacznej ilości pamięci.

### <a name="solution"></a>Rozwiązanie
Zadeklarować typu DBContext jako zmienna lokalna lub pole wystąpienia niestatycznej, używać go w ramach zadania, a następnie przejdź do niego usuwane po użyciu.

Poniższy przykład klasa kontrolera MVC pokazano, jak używać obiektu DBContext.

```csharp
public class BlogsController : Controller
    {
        //BloggingContext is a subclass to DbContext
        private BloggingContext db = new BloggingContext();
        // GET: Blogs
        public ActionResult Index()
        {
            //business logics…
            return View();
        }
        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                db.Dispose();
            }
            base.Dispose(disposing);
        }
    }
```

## <a name="next-steps"></a>Następne kroki
Aby dowiedzieć się więcej na temat optymalizowania i rozwiązywanie problemów z aplikacjami platformy Azure, zobacz [Rozwiązywanie problemów z aplikacją sieci web w usłudze Azure App Service przy użyciu programu Visual Studio](/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio).
