---
title: Optymalizacja kodu platformy Azure
description: Dowiedz się, jak narzędzia do optymalizacji kodu platformy Azure w programie Visual Studio pomagają uczynić kod bardziej niezawodnym i wydajnym.
author: ghogen
manager: jillfra
ms.assetid: ed48ee06-e2d2-4322-af22-07200fb16987
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: e42a746761b09e99e158ecef8e9054bc0049c03d
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489639"
---
# <a name="optimizing-your-azure-code"></a>Optymalizacja kodu platformy Azure
Podczas programowania aplikacji korzystających z platformy Microsoft Azure, istnieją pewne praktyki kodowania, które należy wykonać, aby uniknąć problemów ze skalowalnością aplikacji, zachowaniem i wydajnością w środowisku chmury. Firma Microsoft udostępnia narzędzie analizy kodu platformy Azure, które rozpoznaje i identyfikuje kilka z tych często występujących problemów i pomaga je rozwiązać. Narzędzie można pobrać w programie Visual Studio za pośrednictwem programu NuGet.

## <a name="azure-code-analysis-rules"></a>Reguły analizy kodu platformy Azure
Narzędzie analizy kodu azure używa następujących reguł, aby automatycznie flagi kodu platformy Azure, gdy znajdzie znane problemy wpływające na wydajność. Wykryte problemy są wyświetlane jako ostrzeżenia lub błędy kompilatora. Poprawki kodu lub sugestie dotyczące rozwiązania ostrzeżenia lub błędu są często dostarczane za pośrednictwem ikony żarówki.

## <a name="avoid-using-default-in-process-session-state-mode"></a>Unikaj używania domyślnego trybu stanu sesji (w trakcie procesu)
### <a name="id"></a>ID
Ap000

### <a name="description"></a>Opis
Jeśli używasz domyślnego (w trakcie procesu) trybu stanu sesji dla aplikacji w chmurze, możesz utracić stan sesji.

Podziel się swoimi pomysłami i opiniami na [temat analizy kodu Azure.](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Przyczyna
Domyślnie tryb stanu sesji określony w pliku web.config jest w toku. Ponadto jeśli w pliku konfiguracyjnym nie określono żadnego wpisu, tryb stanu sesji jest domyślnie w toku. Tryb w trakcie procesu przechowuje stan sesji w pamięci na serwerze sieci web. Po ponownym uruchomieniu wystąpienia lub nowe wystąpienie jest używane do równoważenia obciążenia lub obsługi pracy awaryjnej, stan sesji przechowywane w pamięci na serwerze sieci web nie jest zapisywany. Ta sytuacja uniemożliwia aplikacji jest skalowalne w chmurze.

ASP.NET stan sesji obsługuje kilka różnych opcji magazynu dla danych o stanie sesji: InProc, StateServer, SQLServer, Custom i Off. Zaleca się używanie trybu niestandardowego do hostowania danych w zewnętrznym magazynie stanu sesji, takim jak [dostawca stanu sesji platformy Azure dla programu Redis.](https://devblogs.microsoft.com/aspnet/announcing-asp-net-session-state-provider-for-redis-preview-release/)

### <a name="solution"></a>Rozwiązanie
Jednym z zalecanych rozwiązań jest przechowywanie stanu sesji w usłudze zarządzanej pamięci podręcznej. Dowiedz się, jak używać [dostawcy stanu sesji platformy Azure dla firmy Redis](https://devblogs.microsoft.com/aspnet/announcing-asp-net-session-state-provider-for-redis-preview-release/) do przechowywania stanu sesji. Można również przechowywać stan sesji w innych miejscach, aby upewnić się, że aplikacja jest skalowalna w chmurze. Aby dowiedzieć się więcej o alternatywnych rozwiązaniach, przeczytaj [tryby stanu sesji](https://msdn.microsoft.com/library/ms178586).

## <a name="run-method-should-not-be-async"></a>Run metoda nie powinna być async
### <a name="id"></a>ID
Ap1000 ( AP1000 )

### <a name="description"></a>Opis
Utwórz metody asynchroniczne (takie jak [await)](https://msdn.microsoft.com/library/hh156528.aspx)poza metodą [Run(),](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) a następnie wywołaj metody asynchroniczne z [Pliku Run().](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) Deklarowanie [[Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) metoda jako asynchroniowa powoduje, że rola procesu roboczego, aby wprowadzić pętlę ponownego uruchamiania.

Podziel się swoimi pomysłami i opiniami na [temat analizy kodu Azure.](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Przyczyna
Wywołanie metod asynchronicznych wewnątrz metody [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) powoduje, że środowisko uruchomieniowe usługi w chmurze powoduje, że rola procesu roboczego jest odtwarzana. Po uruchomieniu roli procesu roboczego wszystkie wykonywanie programu odbywa się wewnątrz metody [Run().](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) Zamykanie [run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) metoda powoduje ponowne uruchomienie roli procesu roboczego. Gdy środowisko uruchomieniowe roli procesu roboczego uderza w metodę asynchronizę, wywołuje wszystkie operacje po metodzie asynchroniiowej, a następnie zwraca. Powoduje to, że rola procesu roboczego do wyjścia z [[[[Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) metody i ponownego uruchomienia. W następnej iteracji wykonania roli procesu roboczego uderza metody asynchronii ponownie i uruchamia ponownie, powodując roli procesu roboczego do ponownego odtworzenia ponownie, jak również.

### <a name="solution"></a>Rozwiązanie
Umieść wszystkie operacje asynchroniczne poza metodą [Run().](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) Następnie wywołaj refaktoryzowanego metody asynchronicznej z wewnątrz [[Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) metody, takich jak RunAsync().wait. Narzędzie Analizy kodu azure może pomóc rozwiązać ten problem.

Poniższy fragment kodu pokazuje poprawkę kodu dla tego problemu:

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

## <a name="use-service-bus-shared-access-signature-authentication"></a>Korzystanie z uwierzytelniania podpisu dostępu udostępnionego usługi Service Bus
### <a name="id"></a>ID
Ap2000 (ap2000)

### <a name="description"></a>Opis
Użyj sygnatury dostępu współdzielonego (SAS) do uwierzytelniania. Usługa kontroli dostępu (ACS) jest przestarzała do uwierzytelniania magistrali usług.

Podziel się swoimi pomysłami i opiniami na [temat analizy kodu Azure.](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Przyczyna
Aby zwiększyć bezpieczeństwo, usługa Azure Active Directory zastępuje uwierzytelnianie usługi ACS uwierzytelnianiem sygnatury dostępu Współdzielonego. Zobacz [Usługa Azure Active Directory to przyszłość usługi ACS, aby](https://cloudblogs.microsoft.com/enterprisemobility/2013/06/22/azure-active-directory-is-the-future-of-acs/) uzyskać informacje na temat planu przejścia.

### <a name="solution"></a>Rozwiązanie
Użyj uwierzytelniania sygnatury dostępu Współdzielonego w aplikacjach. W poniższym przykładzie pokazano, jak używać istniejącego tokenu sygnatury dostępu do magistrali usług lub jednostki.

```csharp
MessagingFactory listenMF = MessagingFactory.Create(endpoints, new StaticSASTokenProvider(subscriptionToken));
SubscriptionClient sc = listenMF.CreateSubscriptionClient(topicPath, subscriptionName);
BrokeredMessage receivedMessage = sc.Receive();
```

Aby uzyskać więcej informacji, zobacz następujące tematy.

* Aby uzyskać omówienie, zobacz [Uwierzytelnianie podpisu dostępu współdzielonego za pomocą usługi Service Bus](https://msdn.microsoft.com/library/dn170477.aspx)
* [Jak używać uwierzytelniania podpisu dostępu współdzielonego za pomocą usługi Service Bus](https://msdn.microsoft.com/library/dn205161.aspx)
* W przypadku przykładowego projektu zobacz [Korzystanie z uwierzytelniania sygnatury dostępu współdzielonego (SAS) za pomocą subskrypcji usługi Service Bus](https://code.msdn.microsoft.com/windowsapps/Shared-Access-Signature-0a88adf8)

## <a name="consider-using-onmessage-method-to-avoid-receive-loop"></a>Rozważ użycie metody OnMessage, aby uniknąć "pętli odbierania"
### <a name="id"></a>ID
Ap2002 (ap2002)

### <a name="description"></a>Opis
Aby uniknąć przechodzenia do "receive pętli", wywołanie **OnMessage** metoda jest lepszym rozwiązaniem do odbierania wiadomości niż wywołanie **Receive** metody. Jeśli jednak należy użyć **Receive** metody i określić nie-domyślny czas oczekiwania serwera, upewnij się, że czas oczekiwania serwera jest więcej niż jedną minutę.

Podziel się swoimi pomysłami i opiniami na [temat analizy kodu Azure.](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Przyczyna
Podczas wywoływania **OnMessage,** klient uruchamia wewnętrzną pompę wiadomości, która stale sonduje kolejkę lub subskrypcję. Ta pompa wiadomości zawiera nieskończoną pętlę, która powoduje wywołanie odbierania wiadomości. Jeśli na wyjęcie czasu połączenia, zostanie ono nawołuje do nowego połączenia. Interwał limitu czasu jest określana przez wartość [OperationTimeout](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactorysettings.operationtimeout.aspx) właściwości [MessagingFactory,](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactory.aspx)który jest używany.

Zaletą korzystania **z OnMessage** w porównaniu do **Receive** jest to, że użytkownicy nie muszą ręcznie sondować wiadomości, obsługiwać wyjątki, przetwarzać wiele wiadomości równolegle i uzupełniać wiadomości.

Jeśli wywołasz **Receive** bez użycia jego wartości domyślnej, upewnij *się, że ServerWaitTime* wartość jest więcej niż jedną minutę. Ustawienie *ServerWaitTime* na więcej niż jedną minutę uniemożliwia serwerowi limit czasu przed pełnym odebraniem wiadomości.

### <a name="solution"></a>Rozwiązanie
Zapoznaj się z poniższymi przykładami kodu dla zalecanych zastosowań. Aby uzyskać więcej informacji, zobacz [QueueClient.OnMessage Method (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.onmessage.aspx) i [QueueClient.Receive Method (Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.receive.aspx).

Aby zwiększyć wydajność infrastruktury obsługi wiadomości platformy Azure, zobacz wzorzec projektu [Asynchroniczne podkłady do obsługi wiadomości.](https://msdn.microsoft.com/library/dn589781.aspx)

Poniżej przedstawiono przykład używania **onmessage** do odbierania wiadomości.

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

Poniżej przedstawiono przykład użycia **receive** z domyślnym czasem oczekiwania serwera.

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

Poniżej przedstawiono przykład użycia **receive** z nie-domyślny czas oczekiwania serwera.

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

## <a name="consider-using-asynchronous-service-bus-methods"></a>Rozważ użycie metod asynchroniiowej magistrali usług
### <a name="id"></a>ID
Ap2003

### <a name="description"></a>Opis
Użyj asynchronicznych service bus metody, aby zwiększyć wydajność z brokerem obsługi wiadomości.

Podziel się swoimi pomysłami i opiniami na [temat analizy kodu Azure.](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Przyczyna
Za pomocą metod asynchronicznych umożliwia współbieżność programu aplikacji, ponieważ wykonywanie każdego wywołania nie blokuje wątku głównego. Podczas korzystania z metod obsługi wiadomości usługi Service Bus wykonanie operacji (wysyłanie, odbieranie, usuwanie itp.) wymaga czasu. Ten czas obejmuje przetwarzanie operacji przez usługę Service Bus oprócz opóźnienia żądania i odpowiedzi. Aby zwiększyć liczbę operacji na czas, operacje muszą być wykonywane jednocześnie. Aby uzyskać więcej informacji, zapoznaj się z [najlepszymi praktykami w zakresie poprawy wydajności przy użyciu usługi Service Bus brokered Messaging](https://msdn.microsoft.com/library/azure/hh528527.aspx).

### <a name="solution"></a>Rozwiązanie
Zobacz [QueueClient Class (Microsoft.ServiceBus.Messaging),](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.aspx) aby uzyskać informacje na temat korzystania z zalecanej metody asynchroniiowej.

Aby zwiększyć wydajność infrastruktury obsługi wiadomości platformy Azure, zobacz wzorzec projektu [Asynchroniczne podkłady do obsługi wiadomości.](https://msdn.microsoft.com/library/dn589781.aspx)

## <a name="consider-partitioning-service-bus-queues-and-topics"></a>Rozważ partycjonowanie kolejek i tematów usługi Service Bus
### <a name="id"></a>ID
Ap2004 (ap2004)

### <a name="description"></a>Opis
Kolejki usługi Service Bus partycji i tematy dla lepszej wydajności z usługi Service Bus wiadomości.

Podziel się swoimi pomysłami i opiniami na [temat analizy kodu Azure.](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Przyczyna
Partycjonowanie kolejek i tematów usługi Service Bus zwiększa przepływność wydajności i dostępność usług, ponieważ ogólna przepływność podzielonej na partycje kolejki lub tematu nie jest już ograniczona przez wydajność jednego brokera komunikatów lub magazynu obsługi wiadomości. Ponadto tymczasowa awaria magazynu obsługi wiadomości nie sprawia, że kolejka na partycje lub temat są niedostępne. Aby uzyskać więcej informacji, zobacz [Partycjonowanie jednostek obsługi wiadomości](https://msdn.microsoft.com/library/azure/dn520246.aspx).

### <a name="solution"></a>Rozwiązanie
Poniższy fragment kodu pokazuje, jak partycjonować jednostki obsługi wiadomości.

```csharp
// Create partitioned topic.
NamespaceManager ns = NamespaceManager.CreateFromConnectionString(myConnectionString);
TopicDescription td = new TopicDescription(TopicName);
td.EnablePartitioning = true;
ns.CreateTopic(td);
```

Aby uzyskać więcej informacji, zobacz [Podzielone na partycje kolejki i tematy magistrali usług | Blog platformy Microsoft Azure](https://azure.microsoft.com/blog/2013/10/29/partitioned-service-bus-queues-and-topics/) i zapoznaj się z przykładem [kolejki podzielonej na partycje magistrali usług Microsoft Azure.](https://code.msdn.microsoft.com/windowsazure/Service-Bus-Partitioned-7dfd3f1f)

## <a name="do-not-set-sharedaccessstarttime"></a>Nie ustawiaj współużytku Współużytkuj Czasu Rozpoczęcia
### <a name="id"></a>ID
Ap3001

### <a name="description"></a>Opis
Należy unikać używania SharedAccessStartTimeset do bieżącego czasu, aby natychmiast uruchomić zasady dostępu współdzielonego. Wystarczy ustawić tę właściwość, jeśli chcesz uruchomić zasady dostępu współdzielonego w późniejszym czasie.

Podziel się swoimi pomysłami i opiniami na [temat analizy kodu Azure.](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Przyczyna
Synchronizacja zegara powoduje niewielką różnicę czasu między centrami danych. Na przykład logicznie można myśleć ustawienie czasu rozpoczęcia zasad sygnatury dostępu współdzielonego magazynu jako bieżący czas przy użyciu DateTime.Now lub podobnej metody spowoduje, że zasady sygnatury dostępu Współdzielonego zaczęły obowiązywać natychmiast. Jednak niewielkie różnice czasu między centrami danych może powodować problemy z tym, ponieważ niektóre czasy centrum danych może być nieco później niż czas rozpoczęcia, podczas gdy inne przed nim. W rezultacie zasady sygnatury dostępu Współdzielonego mogą wygasnąć szybko (lub nawet natychmiast), jeśli okres istnienia zasad jest ustawiony zbyt krótki.

Aby uzyskać więcej wskazówek dotyczących używania podpisu dostępu współdzielonego w magazynie platformy Azure, zobacz [Wprowadzenie sygnatury dostępu współdzielonego tabeli (sygnatura dostępu współdzielonego), Sygnatura dostępu współdzielonego kolejki i aktualizacja do usługi Blob SAS — Blogi zespołu magazynu Microsoft Azure Storage — Strona główna witryny — blogi MSDN](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/).

### <a name="solution"></a>Rozwiązanie
Usuń instrukcję, która ustawia godzinę rozpoczęcia zasad dostępu współdzielonego. Narzędzie analizy kodu azure zawiera poprawkę dla tego problemu. Aby uzyskać więcej informacji na temat zarządzania zabezpieczeniami, zobacz wzór projektu [Valet Key Pattern](https://msdn.microsoft.com/library/dn568102.aspx).

Poniższy fragment kodu pokazuje poprawkę kodu dla tego problemu.

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

## <a name="shared-access-policy-expiry-time-must-be-more-than-five-minutes"></a>Czas wygaśnięcia zasad dostępu współdzielonego musi wynosić więcej niż pięć minut
### <a name="id"></a>ID
Ap3002 (ap3002)

### <a name="description"></a>Opis
Może istnieć nawet pięć minut różnicy w zegarach między centrami danych w różnych lokalizacjach ze względu na stan znany jako "pochylenie zegara". Aby zapobiec wygaśnięciu tokenu zasad sygnatury dostępu Współdzielonego wcześniej niż planowano, ustaw czas wygaśnięcia na więcej niż pięć minut.

Podziel się swoimi pomysłami i opiniami na [temat analizy kodu Azure.](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Przyczyna
Centra danych w różnych miejscach na całym świecie synchronizują się za pomocą sygnału zegara. Ponieważ czas na sygnał zegara do podróży do różnych lokalizacji, może istnieć wariancja czasu między centrami danych w różnych lokalizacjach geograficznych, chociaż wszystko jest rzekomo zsynchronizowane. Ta różnica czasu może mieć wpływ na czas rozpoczęcia zasad dostępu udostępnionego i interwał wygaśnięcia. W związku z tym, aby upewnić się, że zasady dostępu współdzielonego zacznie obowiązywać natychmiast, nie określaj czasu rozpoczęcia. Ponadto upewnij się, że czas wygaśnięcia jest więcej niż 5 minut, aby zapobiec wczesnemu prze skończeniu czasu.

Aby uzyskać więcej informacji na temat używania podpisu dostępu współdzielonego w magazynie platformy Azure, zobacz [Wprowadzenie sygnatury dostępu współdzielonego tabeli (sygnatura dostępu współdzielonego), Sygnatura dostępu współdzielonego kolejki i aktualizacja do usługi Blob SAS — Blog zespołu magazynu microsoft azure — Strona główna witryny — blogi MSDN](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/).

### <a name="solution"></a>Rozwiązanie
Aby uzyskać więcej informacji na temat zarządzania zabezpieczeniami, zobacz wzór projektu [Valet Key Pattern](https://msdn.microsoft.com/library/dn568102.aspx).

Poniżej przedstawiono przykład nie określania godziny rozpoczęcia zasad dostępu udostępnionego.

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

Poniżej przedstawiono przykład określania czasu rozpoczęcia zasad dostępu udostępnionego z czasem wygaśnięcia zasad dłuższym niż pięć minut.

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

Aby uzyskać więcej informacji, zobacz [Tworzenie i używanie podpisu dostępu udostępnionego](https://msdn.microsoft.com/library/azure/jj721951.aspx).

## <a name="use-cloudconfigurationmanager"></a>Korzystanie z funkcji CloudConfigurationManager
### <a name="id"></a>ID
AP4000 (ap4000)

### <a name="description"></a>Opis
Przy użyciu [ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) klasy dla projektów, takich jak witryny sieci Web platformy Azure i usług mobilnych platformy Azure nie wprowadzi problemów środowiska uruchomieniowego. Najlepszym rozwiązaniem jest jednak użycie funkcji[Cloud ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) jako ujednoliconego sposobu zarządzania konfiguracjami dla wszystkich aplikacji usługi Azure Cloud.

Podziel się swoimi pomysłami i opiniami na [temat analizy kodu Azure.](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Przyczyna
CloudConfigurationManager odczytuje plik konfiguracji odpowiedni dla środowiska aplikacji.

[CloudConfigurationManager](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx)

### <a name="solution"></a>Rozwiązanie
Refaktoryzacja kodu do korzystania z [CloudConfigurationManager Klasy](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx). Poprawka kodu dla tego problemu jest dostarczana przez narzędzie analizy kodu azure.

Poniższy fragment kodu pokazuje poprawkę kodu dla tego problemu. Replace

`var settings = ConfigurationManager.AppSettings["mySettings"];`

with

`var settings = CloudConfigurationManager.GetSetting("mySettings");`

Oto przykład przechowywania ustawienia konfiguracji w pliku App.config lub Web.config. Dodaj ustawienia do sekcji appSettings pliku konfiguracyjnego. Poniżej znajduje się plik Web.config dla poprzedniego przykładu kodu.

```xml
<appSettings>
    <add key="webpages:Version" value="3.0.0.0" />
    <add key="webpages:Enabled" value="false" />
    <add key="ClientValidationEnabled" value="true" />
    <add key="UnobtrusiveJavaScriptEnabled" value="true" />
    <add key="mySettings" value="[put_your_setting_here]"/>
  </appSettings>
```

## <a name="avoid-using-hard-coded-connection-strings"></a>Unikaj używania zakodowanych ciągów połączeń
### <a name="id"></a>ID
Ap4001

### <a name="description"></a>Opis
Jeśli używasz zakodowanych ciągów połączeń i musisz zaktualizować je później, musisz wprowadzić zmiany w kodzie źródłowym i ponownie skompilować aplikację. Jeśli jednak parametry połączenia są przechowywane w pliku konfiguracyjnym, można je później zmienić, po prostu aktualizując plik konfiguracyjny.

Podziel się swoimi pomysłami i opiniami na [temat analizy kodu Azure.](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Przyczyna
Parametry połączenia hard-coding jest złą praktyką, ponieważ wprowadza problemy, gdy parametry połączenia muszą być szybko zmieniane. Ponadto jeśli projekt musi zostać zaewidencjonowany do kontroli źródła, zakodowane parametry połączenia wprowadzają luki w zabezpieczeniach, ponieważ ciągi mogą być wyświetlane w kodzie źródłowym.

### <a name="solution"></a>Rozwiązanie
Przechowuj parametry połączenia w plikach konfiguracyjnych lub środowiskach platformy Azure.

* W przypadku aplikacji autonomicznych użyj app.config do przechowywania ustawień ciągu połączenia.
* W przypadku aplikacji sieci Web hostowanych przez usługi IIS użyj pliku web.config do przechowywania ciągów połączeń.
* W przypadku ASP.NET aplikacji vNext należy używać pliku configuration.json do przechowywania ciągów połączeń.

Aby uzyskać informacje na temat korzystania z plików konfiguracji, takich jak web.config lub app.config, zobacz [ASP.NET Wskazówki dotyczące konfiguracji sieci Web](/aspnet/web-forms/overview/deployment/visual-studio-web-deployment/web-config-transformations). Aby uzyskać informacje na temat działania zmiennych środowiskowych platformy Azure, zobacz [Witryny sieci Web platformy Azure: jak działają ciągi aplikacji i parametry połączenia.](https://azure.microsoft.com/blog/2013/07/17/windows-azure-web-sites-how-application-strings-and-connection-strings-work/) Aby uzyskać informacje na temat przechowywania ciągu połączenia w formancie źródła, zobacz [unikanie umieszczania poufnych informacji, takich jak parametry połączenia, w plikach przechowywanych w repozytorium kodu źródłowego](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control).

## <a name="use-diagnostics-configuration-file"></a>Korzystanie z pliku konfiguracji diagnostyki
### <a name="id"></a>ID
Ap5000 (ap5000)

### <a name="description"></a>Opis
Zamiast konfigurować ustawienia diagnostyki w kodzie, takie jak za pomocą interfejsu API programowania Microsoft.WindowsAzure.Diagnostics, należy skonfigurować ustawienia diagnostyki w pliku diagnostics.wadcfg. (Lub diagnostics.wadcfgx jeśli używasz usługi Azure SDK 2.5). W ten sposób można zmienić ustawienia diagnostyki bez konieczności ponownego kompilacji kodu.

Podziel się swoimi pomysłami i opiniami na [temat analizy kodu Azure.](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Przyczyna
Przed azure SDK 2.5 (który używa diagnostyki platformy Azure 1.3), diagnostyka platformy Azure (WAD) można skonfigurować przy użyciu kilku różnych metod: dodawanie go do obiektu blob konfiguracji w magazynie, przy użyciu kodu imperatywnego, konfiguracji deklaratywnej lub konfiguracji domyślnej. Jednak preferowanym sposobem konfigurowania diagnostyki jest użycie pliku konfiguracyjnego XML (diagnostics.wadcfg lub diagnostics.wadcfgx dla SDK 2.5 lub nowszego) w projekcie aplikacji. W tym podejściu plik diagnostics.wadcfg całkowicie definiuje konfigurację i może być aktualizowany i ponownie rozmieszczony do woli. Mieszanie użycia pliku konfiguracyjnego diagnostics.wadcfg z programowymi metodami ustawiania konfiguracji przy użyciu klas [DiagnosticMonitor](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.diagnosticmonitor.aspx)lub [RoleInstanceDiagnosticManager](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.management.roleinstancediagnosticmanager.aspx)może prowadzić do nieporozumień. Aby uzyskać więcej informacji, zobacz [Inicjowanie lub zmienianie konfiguracji diagnostyki platformy Azure.](https://msdn.microsoft.com/library/azure/hh411537.aspx)

Począwszy od wad 1.3 (dołączone do usługi Azure SDK 2.5), nie jest już możliwe użycie kodu do konfigurowania diagnostyki. W rezultacie można podać konfigurację tylko podczas stosowania lub aktualizowania rozszerzenia diagnostyki.

### <a name="solution"></a>Rozwiązanie
Użyj projektanta konfiguracji diagnostyki, aby przenieść ustawienia diagnostyczne do pliku konfiguracji diagnostyki (diagnostics.wadcfg lub diagnostics.wadcfgx dla SDK 2.5 i nowszych). Zaleca się również zainstalowanie [narzędzia Azure SDK 2.5](https://social.msdn.microsoft.com/Forums/en-US/home) i korzystanie z najnowszej funkcji diagnostycznej.

1. W menu skrótów dla roli, którą chcesz skonfigurować, wybierz pozycję Właściwości, a następnie wybierz kartę Konfiguracja.
2. W sekcji **Diagnostyka** upewnij się, że jest zaznaczone pole wyboru **Włącz diagnostykę.**
3. Wybierz przycisk **Konfiguruj.**

   ![Dostęp do opcji Włącz diagnostykę](./media/vs-azure-tools-optimizing-azure-code-in-visual-studio/IC796660.png)

   Aby uzyskać więcej [informacji, zobacz Konfigurowanie diagnostyki usług w chmurze i maszyn wirtualnych](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md) platformy Azure.

## <a name="avoid-declaring-dbcontext-objects-as-static"></a>Unikaj deklarowania obiektów DbContext jako statycznych
### <a name="id"></a>ID
Ap6000 (ap6000)

### <a name="description"></a>Opis
Aby zapisać pamięć, należy unikać deklarowania DBContext obiektów jako statyczne.

Podziel się swoimi pomysłami i opiniami na [temat analizy kodu Azure.](https://social.msdn.microsoft.com/Forums/en-US/home)

### <a name="reason"></a>Przyczyna
DBContext obiekty przechowywania wyników kwerendy z każdego wywołania. Statyczne obiekty DBContext nie są usuwane, dopóki domena aplikacji nie zostanie zwolniona. W związku z tym statyczny DBContext obiekt może zużywać duże ilości pamięci.

### <a name="solution"></a>Rozwiązanie
Zadeklaruj DBContext jako pole instancji zmiennej lokalnej lub niestatyczne, użyj go do zadania, a następnie pozwól, aby zostały usunięte po użyciu.

W poniższym przykładzie klasy kontrolera MVC pokazano, jak używać obiektu DBContext.

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
Aby dowiedzieć się więcej na temat optymalizacji i rozwiązywania problemów z aplikacjami platformy Azure, zobacz [Rozwiązywanie problemów z aplikacją sieci Web w usłudze Azure App Service przy użyciu programu Visual Studio](/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio).
