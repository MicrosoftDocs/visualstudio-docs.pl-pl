---
title: Optymalizacja kodu platformy Azure
description: Dowiedz się o kodzie jak usługa Azure pomóc sprawić, że kod bardziej niezawodnego i lepszego wykonywania optymalizacji narzędzi w programie Visual Studio.
author: ghogen
manager: jillfra
ms.assetid: ed48ee06-e2d2-4322-af22-07200fb16987
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: ghogen
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.openlocfilehash: b5deb4a3abc944d40fdf94f6d9b6aaf3237e6be7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298981"
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

Podziel się swoimi pomysłami i opiniami na temat [opinii o analizie kodu platformy Azure](https://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Przyczyna
Domyślnie tryb stanu sesji, które są określone w pliku web.config jest w trakcie. Ponadto jeśli żadnego wpisu określone w pliku konfiguracji, tryb stanu sesji domyślnie w procesie. Tryb w procesie przechowuje stanu sesji w pamięci na serwerze sieci web. Po ponownym uruchomieniu wystąpienia lub nowe wystąpienie jest używany do równoważenia obciążenia lub obsługę trybu failover, stan sesji, przechowywane w pamięci na serwerze sieci web nie są zapisywane. Ta sytuacja zapobiega aplikację jest skalowalna w chmurze.

Stanu sesji programu ASP.NET obsługuje kilka opcji innego magazynu dla danych stanu sesji: InProc, StateServer, SQLServer, niestandardowe i Off. Zalecane jest używanie trybu niestandardowego do hostowania danych w zewnętrznym magazynie stanów sesji, takim jak [dostawca stanu sesji platformy Azure dla Redis](https://go.microsoft.com/fwlink/?LinkId=401521).

### <a name="solution"></a>Rozwiązanie
Jedno rozwiązanie zalecane jest przechowywanie stanu sesji usługi zarządzana pamięć podręczna. Dowiedz się, jak przechowywać stan sesji [przy użyciu dostawcy stanu sesji platformy Azure dla usługi Redis](https://go.microsoft.com/fwlink/?LinkId=401521) . Można również przechowywanie stanu sesji w innych miejscach, aby upewnić się, że aplikacja jest skalowalna w chmurze. Aby dowiedzieć się więcej na temat rozwiązań alternatywnych, należy odczytać [tryby stanu sesji](https://msdn.microsoft.com/library/ms178586).

## <a name="run-method-should-not-be-async"></a>Uruchom metody nie powinny być asynchroniczne
### <a name="id"></a>ID
AP1000

### <a name="description"></a>Opis
Utwórz metody asynchroniczne (takie jak [await](https://msdn.microsoft.com/library/hh156528.aspx)) poza metodą [Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) , a następnie wywołaj metody asynchroniczne z [przebiegu ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx). Deklarowanie metody [[Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) jako asynchronicznej powoduje, że rola proces roboczy wprowadza pętlę ponownego uruchomienia.

Podziel się swoimi pomysłami i opiniami na temat [opinii o analizie kodu platformy Azure](https://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Przyczyna
Wywoływanie metod asynchronicznych wewnątrz metody [Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) powoduje, że środowisko uruchomieniowe usługi w chmurze odtwarza rolę procesu roboczego. Po uruchomieniu roli procesu roboczego wszystkie wykonywanie programu odbywa się wewnątrz metody [Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) . Wyjście z metody [Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) powoduje ponowne uruchomienie roli procesu roboczego. Gdy środowisko uruchomieniowe roli procesu roboczego osiągnie metody asynchronicznej, wysyła wszystkie operacje po metody asynchronicznej, a następnie zwraca. Powoduje to, że rola proces roboczy może wyjść z metody [[[[Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) i uruchomić ponownie. W następnej iteracji wykonywania roli procesu roboczego osiągnie metody asynchronicznej ponownie i powoduje ponowne uruchomienie, co powoduje także ponownie odtwarzanie roli procesu roboczego.

### <a name="solution"></a>Rozwiązanie
Umieść wszystkie operacje asynchroniczne poza metodą [Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) . Następnie Wywołaj metodę Async refaktoryzacji z wewnątrz metody [[Run ()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) , np. RunAsync (). Poczekaj. Narzędzie do analizy kodu platformy Azure może pomóc rozwiązać ten problem.

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

Podziel się swoimi pomysłami i opiniami na temat [opinii o analizie kodu platformy Azure](https://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Przyczyna
Aby zwiększyć bezpieczeństwo usługi Azure Active Directory zastępuje ACS uwierzytelniania przy użyciu uwierzytelniania sygnatury dostępu Współdzielonego. Zobacz [, Azure Active Directory to przyszłość usługi ACS,](https://cloudblogs.microsoft.com/enterprisemobility/2013/06/22/azure-active-directory-is-the-future-of-acs/) Aby uzyskać informacje na temat planu przejścia.

### <a name="solution"></a>Rozwiązanie
Korzystanie z uwierzytelniania sygnatury dostępu Współdzielonego w aplikacjach. Poniższy przykład pokazuje, jak uzyskać dostęp do przestrzeni nazw usługi service bus lub jednostki za pomocą istniejącego tokenu sygnatury dostępu Współdzielonego.

```csharp
MessagingFactory listenMF = MessagingFactory.Create(endpoints, new StaticSASTokenProvider(subscriptionToken));
SubscriptionClient sc = listenMF.CreateSubscriptionClient(topicPath, subscriptionName);
BrokeredMessage receivedMessage = sc.Receive();
```

Zobacz następujące tematy, aby uzyskać więcej informacji.

* Aby zapoznać się z omówieniem, zobacz [uwierzytelnianie sygnatury dostępu współdzielonego za pomocą Service Bus](https://msdn.microsoft.com/library/dn170477.aspx)
* [Jak używać uwierzytelniania sygnatury dostępu współdzielonego z Service Bus](https://msdn.microsoft.com/library/dn205161.aspx)

## <a name="consider-using-onmessage-method-to-avoid-receive-loop"></a>Należy wziąć pod uwagę przy użyciu metody OnMessage, aby uniknąć "otrzymywać pętli"
### <a name="id"></a>ID
AP2002

### <a name="description"></a>Opis
Aby uniknąć przechodzenia do "pętli odbioru", wywołanie metody **OnMessage** jest lepszym rozwiązaniem do odbierania komunikatów niż wywoływanie metody **Receive** . Jeśli jednak musisz użyć metody **Receive** i określić niedomyślny czas oczekiwania serwera, upewnij się, że czas oczekiwania serwera wynosi więcej niż minutę.

Podziel się swoimi pomysłami i opiniami na temat [opinii o analizie kodu platformy Azure](https://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Przyczyna
Podczas wywoływania **OnMessage**klient uruchamia wewnętrzną pompę komunikatów, która stale sonduje kolejkę lub subskrypcję. Ta "pompy komunikatów" zawiera wejścia w nieskończoną pętlę, która generuje wywołanie w celu odbierania komunikatów. Jeśli upłynie limit czasu wywołania, wystawia nowe połączenie. Interwał limitu czasu zależy od wartości właściwości [OperationTimeout](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactorysettings.operationtimeout.aspx) [MessagingFactory](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactory.aspx), która jest używana.

Zaletą korzystania z funkcji **OnMessage** w porównaniu do **odbierania** jest to, że użytkownicy nie muszą ręcznie sondować o komunikaty, obsługiwać wyjątki, przetwarzać wiele komunikatów równolegle i kończyć komunikaty.

Jeśli wywołasz metodę **Receive** bez używania jej wartości domyślnej, upewnij się, że wartość *ServerWaitTime* jest większa niż jedna minuta. Ustawienie *ServerWaitTime* na więcej niż jedną minutę uniemożliwia serwerowi przekroczenie limitu czasu, zanim komunikat zostanie w pełni odebrany.

### <a name="solution"></a>Rozwiązanie
Zobacz poniższe przykłady kodu dla zalecanych użycia. Aby uzyskać więcej informacji, zobacz [QueueClient. OnMessage Metoda (Microsoft. ServiceBus. Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.onmessage.aspx)i [QueueClient. Receive — Metoda (Microsoft. ServiceBus. Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.receive.aspx).

Aby zwiększyć wydajność infrastruktury usługi Azure Messaging, zapoznaj się z podręcznikiem [obsługi komunikatów](https://msdn.microsoft.com/library/dn589781.aspx)w ramach wzorca projektowego.

Poniżej przedstawiono przykład użycia funkcji **OnMessage** do odbierania wiadomości.

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

Poniżej przedstawiono przykład użycia opcji **odbieranie** z domyślnym czasem oczekiwania serwera.

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

Poniżej przedstawiono przykład użycia opcji **odbieranie** z niedomyślnym czasem oczekiwania na serwer.

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

Podziel się swoimi pomysłami i opiniami na temat [opinii o analizie kodu platformy Azure](https://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Przyczyna
Używanie metod asynchronicznych umożliwia aplikacji program współbieżność, ponieważ wykonywania każdego wywołania nie blokuje wątku głównego. Korzystając z usługi Service Bus messaging metod, wykonywania operacji (wysyłanie, odbieranie, usunąć itp.) zajmuje trochę czasu. Teraz obejmuje przetwarzanie operacji w usłudze Service Bus, poza tym zwiększa opóźnienia żądania i odpowiedzi. Aby zwiększyć liczbę operacji na czas, jednocześnie muszą wykonać operacje. Aby uzyskać więcej informacji, zobacz [najlepsze rozwiązania dotyczące ulepszeń wydajności przy użyciu Service Bus komunikatów obsługiwanych przez brokera](https://msdn.microsoft.com/library/azure/hh528527.aspx).

### <a name="solution"></a>Rozwiązanie
Aby uzyskać informacje dotyczące sposobu korzystania z zalecanej metody asynchronicznej, zobacz [QueueClient Class (Microsoft. ServiceBus. Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.aspx) .

Aby zwiększyć wydajność infrastruktury usługi Azure Messaging, zapoznaj się z podręcznikiem [obsługi komunikatów](https://msdn.microsoft.com/library/dn589781.aspx)w ramach wzorca projektowego.

## <a name="consider-partitioning-service-bus-queues-and-topics"></a>Należy wziąć pod uwagę partycjonowania tematów i kolejek usługi Service Bus
### <a name="id"></a>ID
AP2004

### <a name="description"></a>Opis
Kolejki usługi Service Bus partycji i tematów w celu zapewnienia lepszej wydajności przy użyciu komunikatów usługi Service Bus.

Podziel się swoimi pomysłami i opiniami na temat [opinii o analizie kodu platformy Azure](https://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Przyczyna
Partycjonowanie tematów i kolejek usługi Service Bus, ponieważ ogólną przepływność podzieleniu kolejki lub tematu nie jest już ograniczone przez wydajności pojedynczego brokera lub magazynu komunikatów zwiększa to dostępność przepływności i usługi wydajności. Ponadto tymczasowe awarii magazynu komunikatów nie czyni podzieleniu kolejki lub tematu niedostępny. Aby uzyskać więcej informacji, zobacz [partycjonowanie jednostek komunikatów](https://msdn.microsoft.com/library/azure/dn520246.aspx).

### <a name="solution"></a>Rozwiązanie
Poniższy fragment kodu przedstawia sposób partycjonowanie jednostki do obsługi komunikatów.

```csharp
// Create partitioned topic.
NamespaceManager ns = NamespaceManager.CreateFromConnectionString(myConnectionString);
TopicDescription td = new TopicDescription(TopicName);
td.EnablePartitioning = true;
ns.CreateTopic(td);
```

Aby uzyskać więcej informacji, zobacz [partycjonowane Service Bus kolejki i tematy | Microsoft Azure blog](https://azure.microsoft.com/blog/2013/10/29/partitioned-service-bus-queues-and-topics/) i zapoznaj się z przykładem [kolejki Microsoft Azure Service Bus z podziałem na partycje](https://code.msdn.microsoft.com/windowsazure/Service-Bus-Partitioned-7dfd3f1f) .

## <a name="do-not-set-sharedaccessstarttime"></a>Nie należy ustawiać SharedAccessStartTime
### <a name="id"></a>ID
AP3001

### <a name="description"></a>Opis
Należy unikać używania SharedAccessStartTimeset bieżący czas, aby natychmiast uruchomić zasady dostęp współdzielony. Należy ustawić tę właściwość, jeśli chcesz uruchomić zasady dostępu udostępnione w późniejszym czasie.

Podziel się swoimi pomysłami i opiniami na temat [opinii o analizie kodu platformy Azure](https://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Przyczyna
Synchronizacja zegara powoduje, że różnica czasu nieznaczne między centrami danych. Na przykład logicznie myślisz, ustawienie czas rozpoczęcia magazynu zasad sygnatury dostępu Współdzielonego jako bieżący czas przy użyciu DateTime.Now lub podobnej metody spowoduje, że zasady sygnatury dostępu Współdzielonego i zaczynają obowiązywać natychmiast. Jednak czas niewielkie różnice między centrami danych może spowodować problemy z tym, ponieważ sytuacje centrum danych mogą być nieco później niż czas rozpoczęcia, podczas gdy inne wcześniej go. Co w efekcie zasad sygnatury dostępu Współdzielonego można unieważnić szybko (lub nawet natychmiast) Jeśli okres istnienia zasad ustawiono zbyt krótki.

Aby uzyskać więcej wskazówek na temat korzystania z sygnatury dostępu współdzielonego w usłudze Azure Storage, zobacz [wprowadzenie do tworzenia sygnatury Microsoft Azure Storage dostępu współdzielonego tabeli](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/)

### <a name="solution"></a>Rozwiązanie
Usuń instrukcję, która ustawia czas rozpoczęcia zasady dostępu współdzielonego. Narzędzia analizy kodu platformy Azure zawiera poprawkę rozwiązującą ten problem. Aby uzyskać więcej informacji na temat zarządzania zabezpieczeniami, zobacz wzorzec projektowania wzorca [portiera](https://msdn.microsoft.com/library/dn568102.aspx).

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

Podziel się swoimi pomysłami i opiniami na temat [opinii o analizie kodu platformy Azure](https://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Przyczyna
Centra danych w różnych lokalizacjach na całym świecie synchronizować sygnał zegara. Ponieważ zajmuje trochę czasu sygnał zegara przechodzić do różnych lokalizacji, może istnieć odchylenie czasu między centrami danych w różnych lokalizacjach geograficznych mimo, że wszystko, co prawdopodobnie jest zsynchronizowany. Ta różnica czasu może mieć wpływ na dostęp współdzielony zasad początek godziny i wygaśnięcia interwału. W związku z tym aby upewnić się, że zasady dostęp współdzielony ma efekt natychmiastowy, nie określić godzinę rozpoczęcia. Ponadto upewnij się, że czas wygaśnięcia jest więcej niż 5 minut, aby zapobiec wczesne limitu czasu.

Aby uzyskać więcej informacji o korzystaniu z sygnatury dostępu współdzielonego w usłudze Azure Storage, zobacz [wprowadzenie do tworzenia sygnatury Microsoft Azure Storage dostępu współdzielonego tabeli](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/)

### <a name="solution"></a>Rozwiązanie
Aby uzyskać więcej informacji na temat zarządzania zabezpieczeniami, zobacz wzorzec projektowania wzorca [portiera](https://msdn.microsoft.com/library/dn568102.aspx).

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

Aby uzyskać więcej informacji, zobacz [Tworzenie i używanie sygnatury dostępu współdzielonego](https://msdn.microsoft.com/library/azure/jj721951.aspx).

## <a name="use-cloudconfigurationmanager"></a>Użyj CloudConfigurationManager
### <a name="id"></a>ID
AP4000

### <a name="description"></a>Opis
Korzystanie z klasy [ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) dla projektów, takich jak witryna sieci Web platformy Azure i usługi Azure Mobile Services, nie spowoduje problemów ze środowiskiem uruchomieniowym. Najlepszym rozwiązaniem jest jednak użycie usługi Cloud[ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) jako ujednoliconej metody zarządzania konfiguracjami dla wszystkich aplikacji w chmurze platformy Azure.

Podziel się swoimi pomysłami i opiniami na temat [opinii o analizie kodu platformy Azure](https://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Przyczyna
CloudConfigurationManager odczytuje plik konfiguracyjny odpowiednie do środowiska aplikacji.

[CloudConfigurationManager](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx)

### <a name="solution"></a>Rozwiązanie
Refaktoryzacja kodu, aby użyć [klasy CloudConfigurationManager](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx). Kod poprawkę rozwiązującą ten problem jest zapewniana przez narzędzia analizy kodu platformy Azure.

Poniższy fragment kodu pokazuje poprawki kodu dla tego problemu. Replace

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

Podziel się swoimi pomysłami i opiniami na temat [opinii o analizie kodu platformy Azure](https://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Przyczyna
Trwałe kodowanie parametrów połączenia jest złym zwyczajem, ponieważ wprowadza ona problemy, gdy parametry połączenia muszą szybką zmianę. Ponadto jeśli projekt musi zostać zaewidencjonowane do kontroli źródła, ciągów połączeń zakodowanych wprowadzić luki w zabezpieczeniach, ponieważ ciągi mogą być wyświetlane w kodzie źródłowym.

### <a name="solution"></a>Rozwiązanie
Store parametry połączenia w środowiskach platformy Azure i plików konfiguracji.

* Dla aplikacji autonomicznej należy użyć pliku app.config do przechowywania ustawień parametrów połączenia.
* W przypadku aplikacji sieci web obsługiwane przez usługi IIS umożliwiają przechowywanie parametrów połączenia pliku web.config.
* W przypadku aplikacji ASP.NET vNext configuration.json do przechowywania używa parametrów połączenia.

Aby uzyskać informacje na temat korzystania z plików konfiguracji, takich jak Web. config lub App. config, zobacz [ASP.NET Web Configuration wytycznych](https://msdn.microsoft.com/library/vstudio/ff400235\(v=vs.100\).aspx). Aby dowiedzieć się, jak działają zmienne środowiskowe platformy Azure, zobacz [witryny sieci Web systemu Azure: jak działają ciągi aplikacji i parametry połączenia](https://azure.microsoft.com/blog/2013/07/17/windows-azure-web-sites-how-application-strings-and-connection-strings-work/). Aby uzyskać informacje na temat przechowywania parametrów połączenia w kontroli źródła, zobacz [unikanie umieszczania poufnych informacji, takich jak parametry połączenia w plikach przechowywanych w repozytorium kodu źródłowego](https://docs.microsoft.com/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control).

## <a name="use-diagnostics-configuration-file"></a>Użyj pliku konfiguracji diagnostyki
### <a name="id"></a>ID
AP5000

### <a name="description"></a>Opis
Zamiast konfigurować ustawienia diagnostyki w kodzie, takie jak za pomocą Microsoft.WindowsAzure.Diagnostics programowania interfejsu API, należy skonfigurować ustawienia diagnostyki, w pliku diagnostics.wadcfg. (Lub diagnostics.wadcfgx, jeśli używasz zestawu SDK Azure 2.5). Dzięki temu możesz zmienić ustawienia diagnostyki, bez konieczności ponownego kompilowania kodu.

Podziel się swoimi pomysłami i opiniami na temat [opinii o analizie kodu platformy Azure](https://go.microsoft.com/fwlink/?LinkId=403771).

### <a name="reason"></a>Przyczyna
Przed Azure SDK 2.5, (która korzysta z usługi Diagnostyka Azure 1.3), usługi Azure Diagnostics (WAD) może zostać skonfigurowany przy użyciu kilku różnych metod: dodanie go do obiektu blob konfiguracji w magazynie, przy użyciu kodu imperatywnego, konfiguracja deklaratywne lub wartość domyślną Konfiguracja. Jednak preferowanym sposobem skonfigurowania diagnostyki jest użycie pliku konfiguracji XML (Diagnostics. wadcfg lub Diagnostics. wadcfgx dla zestawu SDK 2,5 i nowszego) w projekcie aplikacji. W tym podejściu pliku diagnostics.wadcfg całkowicie definiuje konfigurację można zaktualizować i ponownie wdrażana w momencie. Mieszanie użycia pliku konfiguracji Diagnostics. wadcfg z metodami programistycznymi ustawień konfiguracji za pomocą klasy [DiagnosticMonitor](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.diagnosticmonitor.aspx)lub [RoleInstanceDiagnosticManager](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.management.roleinstancediagnosticmanager.aspx) może prowadzić do nieporozumień. Aby uzyskać więcej informacji, zobacz temat [Inicjowanie lub zmiana konfiguracji Diagnostyka Azure](https://msdn.microsoft.com/library/azure/hh411537.aspx) .

Począwszy od 1.3 WAD (dołączone do zestawu SDK Azure 2.5), już nie jest możliwe użycie kodu, aby skonfigurować diagnostykę. Co w efekcie można podać tylko konfiguracji podczas stosowania lub aktualizowania rozszerzenie diagnostyki.

### <a name="solution"></a>Rozwiązanie
Użyj projektanta konfiguracji diagnostyki do przenoszenia ustawień diagnostycznych do pliku konfiguracji diagnostyki (Diagnostics. wadcfg lub Diagnostics. wadcfgx dla zestawu SDK 2,5 i nowszego). Zalecane jest również zainstalowanie [zestawu Azure SDK 2,5](https://go.microsoft.com/fwlink/?LinkId=513188) i użycie najnowszej funkcji diagnostyki.

1. W menu skrótów dla roli, który chcesz skonfigurować wybierz polecenie Właściwości, a następnie wybierz kartę Konfiguracja.
2. W sekcji **Diagnostyka** upewnij się, że zaznaczone jest pole wyboru **Włącz diagnostykę** .
3. Wybierz przycisk **Konfiguruj** .

   ![Uzyskiwanie dostępu do opcji Włącz diagnostykę](./media/vs-azure-tools-optimizing-azure-code-in-visual-studio/IC796660.png)

   Aby uzyskać więcej informacji [, zobacz Konfigurowanie diagnostyki dla Cloud Services platformy Azure i Virtual Machines](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md) .

## <a name="avoid-declaring-dbcontext-objects-as-static"></a>Należy unikać deklarowania obiektów typu DbContext jako statyczne
### <a name="id"></a>ID
AP6000

### <a name="description"></a>Opis
Aby zapisać pamięci, należy unikać deklarowania obiektów typu DBContext jako statyczne.

Podziel się swoimi pomysłami i opiniami na temat [opinii o analizie kodu platformy Azure](https://go.microsoft.com/fwlink/?LinkId=403771).

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

## <a name="next-steps"></a>Kolejne kroki
Aby dowiedzieć się więcej na temat optymalizacji i rozwiązywania problemów z aplikacjami platformy Azure, zobacz [Rozwiązywanie problemów z aplikacją sieci Web w Azure App Service przy użyciu programu Visual Studio](/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio)
