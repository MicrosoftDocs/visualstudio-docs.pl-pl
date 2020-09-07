---
title: Optymalizowanie kodu platformy Azure
description: Dowiedz się, jak narzędzia optymalizacji kodu platformy Azure w programie Visual Studio pomagają zwiększyć niezawodność i lepszą obsługę kodu.
author: ghogen
manager: jillfra
ms.assetid: ed48ee06-e2d2-4322-af22-07200fb16987
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: 3ee226aac0d705da29333260966781d5b9b627ed
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508460"
---
# <a name="optimizing-your-azure-code"></a>Optymalizacja kodu platformy Azure
Podczas programowania aplikacji korzystających z Microsoft Azure, istnieją pewne wskazówki dotyczące kodowania, które należy wykonać, aby zapobiec problemom z skalowalnością, zachowaniem i wydajnością aplikacji w środowisku chmury. Firma Microsoft udostępnia Narzędzie analizy kodu platformy Azure, które rozpoznaje i identyfikuje kilka często spotykanych problemów oraz ułatwia ich rozwiązywanie. Narzędzie można pobrać w programie Visual Studio za pośrednictwem programu NuGet.

## <a name="azure-code-analysis-rules"></a>Reguły analizy kodu platformy Azure
Narzędzie Azure Code Analysis używa następujących reguł, aby automatycznie oflagować kod platformy Azure w przypadku znalezienia znanych problemów z wydajnością. Wykryte problemy są wyświetlane w postaci ostrzeżeń lub błędów kompilatora. Poprawki kodu lub sugestie dotyczące rozpoznawania ostrzeżeń lub błędów często są udostępniane za pomocą ikony żarówki.

## <a name="avoid-using-default-in-process-session-state-mode"></a>Unikaj używania domyślnego trybu stanu sesji (w procesie)
### <a name="id"></a>ID
AP0000

### <a name="description"></a>Opis
Jeśli używasz domyślnego trybu stanu sesji (w procesie) dla aplikacji w chmurze, możesz utracić stan sesji.

Podziel się swoimi pomysłami i opiniami na temat [opinii o analizie kodu platformy Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Przyczyna
Domyślnie tryb stanu sesji określony w pliku web.config jest w toku. Ponadto, jeśli w pliku konfiguracji nie określono wpisu, tryb stanu sesji jest domyślnie używany w procesie. Tryb w procesie przechowuje stan sesji w pamięci na serwerze sieci Web. Po ponownym uruchomieniu wystąpienia lub wykorzystaniu nowego wystąpienia do obsługi równoważenia obciążenia lub przełączenia w tryb failover stan sesji przechowywanej w pamięci na serwerze sieci Web nie jest zapisywany. Ta sytuacja uniemożliwia skalowanie aplikacji w chmurze.

Stan sesji ASP.NET obsługuje kilka różnych opcji magazynu dla danych stanu sesji: InProc, StateServer, SQLServer, Custom i off. Zalecane jest używanie trybu niestandardowego do hostowania danych w zewnętrznym magazynie stanów sesji, takim jak [dostawca stanu sesji platformy Azure dla Redis](https://devblogs.microsoft.com/aspnet/announcing-asp-net-session-state-provider-for-redis-preview-release/).

### <a name="solution"></a>Rozwiązanie
Jednym z zalecanych rozwiązań jest przechowywanie stanu sesji na zarządzanej pamięci podręcznej. Dowiedz się, jak przechowywać stan sesji [przy użyciu dostawcy stanu sesji platformy Azure dla usługi Redis](https://devblogs.microsoft.com/aspnet/announcing-asp-net-session-state-provider-for-redis-preview-release/) . Możesz również przechowywać stan sesji w innych miejscach, aby upewnić się, że aplikacja jest skalowalna w chmurze. Aby dowiedzieć się więcej na temat rozwiązań alternatywnych, należy odczytać [tryby stanu sesji](/previous-versions/ms178586(v=vs.140)).

## <a name="run-method-should-not-be-async"></a>Metoda run nie powinna być asynchroniczna
### <a name="id"></a>ID
AP1000

### <a name="description"></a>Opis
Utwórz metody asynchroniczne (takie jak [await](/dotnet/csharp/language-reference/operators/await)) poza metodą [Run ()](/previous-versions/azure/reference/ee772746(v=azure.100)) , a następnie wywołaj metody asynchroniczne z [przebiegu ()](/previous-versions/azure/reference/ee772746(v=azure.100)). Deklarowanie metody [[Run ()](/previous-versions/azure/reference/ee772746(v=azure.100))](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) jako asynchronicznej powoduje, że rola proces roboczy wprowadza pętlę ponownego uruchomienia.

Podziel się swoimi pomysłami i opiniami na temat [opinii o analizie kodu platformy Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Przyczyna
Wywoływanie metod asynchronicznych wewnątrz metody [Run ()](/previous-versions/azure/reference/ee772746(v=azure.100)) powoduje, że środowisko uruchomieniowe usługi w chmurze odtwarza rolę procesu roboczego. Po uruchomieniu roli procesu roboczego wszystkie wykonywanie programu odbywa się wewnątrz metody [Run ()](/previous-versions/azure/reference/ee772746(v=azure.100)) . Wyjście z metody Run powoduje ponowne uruchomienie roli procesu roboczego. Gdy środowisko uruchomieniowe roli procesu roboczego trafi do metody asynchronicznej, wysyła wszystkie operacje po metodzie asynchronicznej, a następnie zwraca. Powoduje to, że rola proces roboczy może wyjść z metody Run i ponownie uruchomić. W następnej iteracji wykonywania rola proces roboczy ponownie przywraca metodę asynchroniczną i uruchamia ponownie, powodując ponowne odtworzenie roli procesu roboczego.

### <a name="solution"></a>Rozwiązanie
Umieść wszystkie operacje asynchroniczne poza metodą [Run ()](/previous-versions/azure/reference/ee772746(v=azure.100)) . Następnie Wywołaj metodę Async refaktoryzacji z wewnątrz metody Run, taką jak RunAsync (). Czekaj. Narzędzie analizy kodu platformy Azure może pomóc w rozwiązaniu tego problemu.

Poniższy fragment kodu ilustruje poprawkę kodu dla tego problemu:

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

## <a name="use-service-bus-shared-access-signature-authentication"></a>Użyj Service Bus uwierzytelniania sygnatury dostępu współdzielonego
### <a name="id"></a>ID
AP2000

### <a name="description"></a>Opis
Użyj sygnatury dostępu współdzielonego (SAS) do uwierzytelniania. Usługa Access Control Service (ACS) jest przestarzała na potrzeby uwierzytelniania w usłudze Service Bus.

Podziel się swoimi pomysłami i opiniami na temat [opinii o analizie kodu platformy Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Przyczyna
W celu zwiększenia bezpieczeństwa Azure Active Directory zastępują uwierzytelnianie usług ACS przy użyciu uwierzytelniania SAS. Zobacz [, Azure Active Directory to przyszłość usługi ACS,](https://cloudblogs.microsoft.com/enterprisemobility/2013/06/22/azure-active-directory-is-the-future-of-acs/) Aby uzyskać informacje na temat planu przejścia.

### <a name="solution"></a>Rozwiązanie
Używaj uwierzytelniania SAS w aplikacjach. Poniższy przykład pokazuje, jak używać istniejącego tokenu SAS do uzyskiwania dostępu do przestrzeni nazw lub jednostki usługi Service Bus.

```csharp
MessagingFactory listenMF = MessagingFactory.Create(endpoints, new StaticSASTokenProvider(subscriptionToken));
SubscriptionClient sc = listenMF.CreateSubscriptionClient(topicPath, subscriptionName);
BrokeredMessage receivedMessage = sc.Receive();
```

Aby uzyskać więcej informacji, zobacz następujące tematy.

* Aby zapoznać się z omówieniem, zobacz [uwierzytelnianie sygnatury dostępu współdzielonego za pomocą Service Bus](/azure/service-bus-messaging/service-bus-sas)
* [Jak używać uwierzytelniania sygnatury dostępu współdzielonego z Service Bus](/azure/service-bus-messaging/service-bus-sas)

## <a name="consider-using-onmessage-method-to-avoid-receive-loop"></a>Rozważ użycie metody OnMessage, aby uniknąć "pętli odbioru"
### <a name="id"></a>ID
AP2002

### <a name="description"></a>Opis
Aby uniknąć przechodzenia do "pętli odbioru", wywołanie metody **OnMessage** jest lepszym rozwiązaniem do odbierania komunikatów niż wywoływanie metody **Receive** . Jeśli jednak musisz użyć metody **Receive** i określić niedomyślny czas oczekiwania serwera, upewnij się, że czas oczekiwania serwera wynosi więcej niż minutę.

Podziel się swoimi pomysłami i opiniami na temat [opinii o analizie kodu platformy Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Przyczyna
Podczas wywoływania **OnMessage**klient uruchamia wewnętrzną pompę komunikatów, która stale sonduje kolejkę lub subskrypcję. Ta pompa komunikatów zawiera nieskończoną pętlę, która wystawia wywołanie do odbierania komunikatów. Jeśli wystąpiło limit czasu, wygeneruje nowe wywołanie. Interwał limitu czasu zależy od wartości właściwości [OperationTimeout](/dotnet/api/microsoft.servicebus.messaging.messagingfactorysettings) [MessagingFactory](/dotnet/api/microsoft.servicebus.messaging.messagingfactory), która jest używana.

Zaletą korzystania z funkcji **OnMessage** w porównaniu do **odbierania** jest to, że użytkownicy nie muszą ręcznie sondować o komunikaty, obsługiwać wyjątki, przetwarzać wiele komunikatów równolegle i kończyć komunikaty.

Jeśli wywołasz metodę **Receive** bez używania jej wartości domyślnej, upewnij się, że wartość *ServerWaitTime* jest większa niż jedna minuta. Ustawienie *ServerWaitTime* na więcej niż jedną minutę uniemożliwia serwerowi przekroczenie limitu czasu, zanim komunikat zostanie w pełni odebrany.

### <a name="solution"></a>Rozwiązanie
Zapoznaj się z poniższymi przykładami kodu w celu uzyskania zalecanych zastosowań. Aby uzyskać więcej informacji, zobacz [QueueClient. OnMessage Metoda (Microsoft. ServiceBus. Messaging)](/dotnet/api/microsoft.servicebus.messaging.queueclient) i [QueueClient. Receive — Metoda (Microsoft. ServiceBus. Messaging)](/dotnet/api/microsoft.servicebus.messaging.queueclient).

Aby zwiększyć wydajność infrastruktury usługi Azure Messaging, zapoznaj się z podręcznikiem [obsługi komunikatów](/previous-versions/msp-n-p/dn589781(v=pandp.10))w ramach wzorca projektowego.

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

## <a name="consider-using-asynchronous-service-bus-methods"></a>Rozważ użycie asynchronicznych metod Service Bus
### <a name="id"></a>ID
AP2003

### <a name="description"></a>Opis
Użyj metod Service Bus asynchronicznej, aby zwiększyć wydajność za pomocą komunikatów obsługiwanych przez brokera.

Podziel się swoimi pomysłami i opiniami na temat [opinii o analizie kodu platformy Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Przyczyna
Użycie metod asynchronicznych umożliwia współbieżność programu aplikacji, ponieważ wykonywanie każdego wywołania nie blokuje wątku głównego. W przypadku korzystania z metod obsługi komunikatów Service Bus wykonywanie operacji (wysyłanie, odbieranie, usuwanie itp.) trwa. Ta godzina obejmuje przetwarzanie operacji przez usługę Service Bus, a także opóźnienia żądania i odpowiedzi. Aby zwiększyć liczbę operacji na czas, operacje muszą być wykonywane współbieżnie. Aby uzyskać więcej informacji, zobacz [najlepsze rozwiązania dotyczące ulepszeń wydajności przy użyciu Service Bus komunikatów obsługiwanych przez brokera](/previous-versions/azure/hh528527(v=azure.100)).

### <a name="solution"></a>Rozwiązanie
Aby uzyskać informacje dotyczące sposobu korzystania z zalecanej metody asynchronicznej, zobacz [QueueClient Class (Microsoft. ServiceBus. Messaging)](/dotnet/api/microsoft.servicebus.messaging.queueclient) .

Aby zwiększyć wydajność infrastruktury usługi Azure Messaging, zapoznaj się z podręcznikiem [obsługi komunikatów](/previous-versions/msp-n-p/dn589781(v=pandp.10))w ramach wzorca projektowego.

## <a name="consider-partitioning-service-bus-queues-and-topics"></a>Rozważ partycjonowanie Service Bus kolejek i tematów
### <a name="id"></a>ID
AP2004

### <a name="description"></a>Opis
Podziel się Service Bus kolejkami i tematami, aby uzyskać lepszą wydajność przy użyciu Service Bus komunikatów.

Podziel się swoimi pomysłami i opiniami na temat [opinii o analizie kodu platformy Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Przyczyna
Partycjonowanie Service Bus kolejek i tematów zwiększa przepływność wydajności i dostępność usług, ponieważ ogólna przepływność partycjonowanej kolejki lub tematu nie jest już ograniczona przez wydajność jednego brokera komunikatów lub magazynu komunikatów. Ponadto tymczasowa awaria magazynu obsługi wiadomości nie powoduje, że podzielona Kolejka ani temat nie jest dostępny. Aby uzyskać więcej informacji, zobacz [partycjonowanie jednostek komunikatów](/previous-versions/azure/dn520246(v=azure.100)).

### <a name="solution"></a>Rozwiązanie
Poniższy fragment kodu przedstawia sposób partycjonowania jednostek obsługi komunikatów.

```csharp
// Create partitioned topic.
NamespaceManager ns = NamespaceManager.CreateFromConnectionString(myConnectionString);
TopicDescription td = new TopicDescription(TopicName);
td.EnablePartitioning = true;
ns.CreateTopic(td);
```

Aby uzyskać więcej informacji, zobacz [partycjonowane Service Bus kolejki i tematy | Microsoft Azure blog](https://azure.microsoft.com/blog/2013/10/29/partitioned-service-bus-queues-and-topics/) i zapoznaj się z przykładem [kolejki Microsoft Azure Service Bus z podziałem na partycje](https://code.msdn.microsoft.com/windowsazure/Service-Bus-Partitioned-7dfd3f1f) .

## <a name="do-not-set-sharedaccessstarttime"></a>Nie ustawiaj SharedAccessStartTime
### <a name="id"></a>ID
AP3001

### <a name="description"></a>Opis
Należy unikać używania SharedAccessStartTimeset do bieżącego czasu, aby natychmiast uruchomić zasady dostępu współdzielonego. Należy ustawić tę właściwość tylko wtedy, gdy chcesz uruchomić zasady dostępu współdzielonego w późniejszym czasie.

Podziel się swoimi pomysłami i opiniami na temat [opinii o analizie kodu platformy Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Przyczyna
Synchronizacja zegara powoduje niewielką różnicę czasu między centrami danych. Na przykład można logicznie myśleć o ustawianiu czasu rozpoczęcia zasad SAS magazynu jako bieżącego czasu przy użyciu daty/godziny. teraz lub podobnej metody spowodują natychmiastowe zastosowanie zasad SAS. Jednak niewielkie różnice czasu między centrami danych mogą powodować problemy z tym, ponieważ niektóre czasy centrów danych mogą być nieco późniejsze od czasu rozpoczęcia, a inne przed nim. W efekcie zasady sygnatury dostępu współdzielonego mogą szybko wygasnąć (a nawet natychmiast), jeśli okres istnienia zasad jest ustawiony za krótki.

Aby uzyskać więcej wskazówek na temat korzystania z sygnatury dostępu współdzielonego w usłudze Azure Storage, zobacz [wprowadzenie do tworzenia sygnatury Microsoft Azure Storage dostępu współdzielonego tabeli](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/)

### <a name="solution"></a>Rozwiązanie
Usuń instrukcję, która ustawia godzinę rozpoczęcia zasad dostępu współdzielonego. Narzędzie analizy kodu platformy Azure zawiera poprawkę tego problemu. Aby uzyskać więcej informacji na temat zarządzania zabezpieczeniami, zobacz wzorzec projektowania wzorca [portiera](/previous-versions/msp-n-p/dn568102(v=pandp.10)).

Poniższy fragment kodu przedstawia poprawkę kodu dla tego problemu.

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

## <a name="shared-access-policy-expiry-time-must-be-more-than-five-minutes"></a>Czas wygaśnięcia zasad dostępu współdzielonego musi być większy niż pięć minut
### <a name="id"></a>ID
AP3002

### <a name="description"></a>Opis
W zegarach między centrami danych w różnych lokalizacjach może być co najwyżej pięć minut, ze względu na warunek znany jako "przesunięcie zegara". Aby zapobiec wygaśnięciu tokenu zasad SAS przed upływem zaplanowanego, ustaw czas wygaśnięcia na więcej niż pięć minut.

Podziel się swoimi pomysłami i opiniami na temat [opinii o analizie kodu platformy Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Przyczyna
Centra danych w różnych lokalizacjach na całym świecie synchronizują się za pomocą sygnału zegara. Ponieważ jest to czasochłonne, aby sygnał zegara poruszał się do różnych lokalizacji, może istnieć różnica czasu między centrami danych w różnych lokalizacjach geograficznych, chociaż wszystko jest supposedly zsynchronizowane. Różnica czasu może mieć wpływ na czas rozpoczęcia i interwał wygaśnięcia zasad dostępu współdzielonego. W związku z tym, aby zapewnić, że zasady dostępu współdzielonego zaczynają obowiązywać natychmiast, nie określaj godziny rozpoczęcia. Ponadto należy się upewnić, że czas wygaśnięcia wynosi więcej niż 5 minut, aby zapobiec wczesnemu przekroczeniu limitu czasu.

Aby uzyskać więcej informacji o korzystaniu z sygnatury dostępu współdzielonego w usłudze Azure Storage, zobacz [wprowadzenie do tworzenia sygnatury Microsoft Azure Storage dostępu współdzielonego tabeli](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/)

### <a name="solution"></a>Rozwiązanie
Aby uzyskać więcej informacji na temat zarządzania zabezpieczeniami, zobacz wzorzec projektowania wzorca [portiera](/previous-versions/msp-n-p/dn568102(v=pandp.10)).

Poniżej przedstawiono przykład nieokreślania czasu rozpoczęcia zasad dostępu współdzielonego.

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

Poniżej przedstawiono przykład określania czasu rozpoczęcia zasad dostępu współdzielonego z upływem czasu wygaśnięcia zasad większym niż pięć minut.

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

Aby uzyskać więcej informacji, zobacz [Konfigurowanie anonimowego publicznego dostępu do odczytu dla kontenerów i obiektów BLOB](/azure/storage/blobs/anonymous-read-access-configure?tabs=portal).

## <a name="use-cloudconfigurationmanager"></a>Użyj CloudConfigurationManager
### <a name="id"></a>ID
AP4000

### <a name="description"></a>Opis
Korzystanie z klasy [ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) dla projektów, takich jak witryna sieci Web platformy Azure i usługi Azure Mobile Services, nie spowoduje problemów ze środowiskiem uruchomieniowym. Najlepszym rozwiązaniem jest jednak użycie usługi Cloud[ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx) jako ujednoliconej metody zarządzania konfiguracjami dla wszystkich aplikacji w chmurze platformy Azure.

Podziel się swoimi pomysłami i opiniami na temat [opinii o analizie kodu platformy Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Przyczyna
CloudConfigurationManager odczytuje plik konfiguracyjny odpowiedni dla środowiska aplikacji.

[CloudConfigurationManager](/previous-versions/azure/)

### <a name="solution"></a>Rozwiązanie
Refaktoryzacja kodu, aby użyć [klasy CloudConfigurationManager](/previous-versions/azure/reference/mt634650(v=azure.100)). Poprawka kodu dla tego problemu jest zapewniana przez narzędzie Azure Code Analysis.

Poniższy fragment kodu przedstawia poprawkę kodu dla tego problemu. Zamień

`var settings = ConfigurationManager.AppSettings["mySettings"];`

with

`var settings = CloudConfigurationManager.GetSetting("mySettings");`

Oto przykład sposobu przechowywania ustawienia konfiguracji w pliku App.config lub Web.config. Dodaj ustawienia do sekcji appSettings w pliku konfiguracji. Poniżej znajduje się plik Web.config dla poprzedniego przykładu kodu.

```xml
<appSettings>
    <add key="webpages:Version" value="3.0.0.0" />
    <add key="webpages:Enabled" value="false" />
    <add key="ClientValidationEnabled" value="true" />
    <add key="UnobtrusiveJavaScriptEnabled" value="true" />
    <add key="mySettings" value="[put_your_setting_here]"/>
  </appSettings>
```

## <a name="avoid-using-hard-coded-connection-strings"></a>Unikaj używania zakodowanych parametrów połączenia
### <a name="id"></a>ID
AP4001

### <a name="description"></a>Opis
Jeśli używasz zakodowanych parametrów połączenia i musisz je zaktualizować później, musisz wprowadzić zmiany w kodzie źródłowym i ponownie skompilować aplikację. Jeśli jednak przechowujesz parametry połączenia w pliku konfiguracji, możesz je później zmienić, aktualizując plik konfiguracji.

Podziel się swoimi pomysłami i opiniami na temat [opinii o analizie kodu platformy Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Przyczyna
Ciągi połączeń z kodowaniem, które są niewłaściwe, ponieważ wprowadzają problemy, gdy należy szybko zmienić parametry połączenia. Ponadto, jeśli projekt musi być zaewidencjonowany do kontroli źródła, ciągi połączeń kodowane wprowadzają luki w zabezpieczeniach, ponieważ ciągi mogą być wyświetlane w kodzie źródłowym.

### <a name="solution"></a>Rozwiązanie
Przechowywanie parametrów połączenia w plikach konfiguracji lub środowiskach platformy Azure.

* W przypadku aplikacji autonomicznych Użyj app.config do przechowywania ustawień parametrów połączenia.
* W przypadku aplikacji sieci Web hostowanych przez usługi IIS Użyj web.config do przechowywania parametrów połączenia.
* W przypadku aplikacji ASP.NET vNext należy używać configuration.jsdo przechowywania parametrów połączenia.

Aby uzyskać informacje na temat korzystania z plików konfiguracji, takich jak web.config lub app.config, zobacz [wytyczne dotyczące konfiguracji sieci Web ASP.NET](/aspnet/web-forms/overview/deployment/visual-studio-web-deployment/web-config-transformations). Aby dowiedzieć się, jak działają zmienne środowiskowe platformy Azure, zobacz [witryny sieci Web systemu Azure: jak działają ciągi aplikacji i parametry połączenia](https://azure.microsoft.com/blog/2013/07/17/windows-azure-web-sites-how-application-strings-and-connection-strings-work/). Aby uzyskać informacje na temat przechowywania parametrów połączenia w kontroli źródła, zobacz [unikanie umieszczania poufnych informacji, takich jak parametry połączenia w plikach przechowywanych w repozytorium kodu źródłowego](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control).

## <a name="use-diagnostics-configuration-file"></a>Użyj pliku konfiguracji diagnostyki
### <a name="id"></a>ID
AP5000

### <a name="description"></a>Opis
Zamiast konfigurować ustawienia diagnostyczne w kodzie, np. przy użyciu interfejsu API programowania Microsoft. WindowsAzure. Diagnostics, należy skonfigurować ustawienia diagnostyczne w pliku Diagnostics. wadcfg. (Lub, Diagnostics. wadcfgx, jeśli używasz zestawu Azure SDK 2,5). Dzięki temu można zmienić ustawienia diagnostyki bez konieczności ponownego kompilowania kodu.

Podziel się swoimi pomysłami i opiniami na temat [opinii o analizie kodu platformy Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Przyczyna
Przed wdrożeniem zestawu Azure SDK 2,5 (który korzysta z diagnostyki Azure 1,3) Diagnostyka Azure (funkcji wad) można skonfigurować przy użyciu kilku różnych metod: dodanie go do obiektu BLOB konfiguracji w magazynie przy użyciu kodu bezwzględnego, konfiguracji deklaracyjnej lub konfiguracji domyślnej. Jednak preferowanym sposobem skonfigurowania diagnostyki jest użycie pliku konfiguracji XML (Diagnostics. wadcfg lub Diagnostics. wadcfgx dla zestawu SDK 2,5 i nowszego) w projekcie aplikacji. W tym podejściu plik Diagnostics. wadcfg całkowicie definiuje konfigurację i można ją zaktualizować i ponownie wdrożyć w programie. Mieszanie użycia pliku konfiguracji Diagnostics. wadcfg z metodami programistycznymi ustawień konfiguracji za pomocą klasy [DiagnosticMonitor](/previous-versions/azure/reference/ee758597(v=azure.100))lub [RoleInstanceDiagnosticManager](/previous-versions/azure/reference/ee773157(v=azure.100))może prowadzić do nieporozumień. Aby uzyskać więcej informacji, zobacz temat [Inicjowanie lub zmiana konfiguracji Diagnostyka Azure](/previous-versions/azure/hh411537(v=azure.100)) .

Począwszy od funkcji wad 1,3 (dołączonego do zestawu Azure SDK 2,5), nie jest już możliwe użycie kodu w celu skonfigurowania diagnostyki. W związku z tym można podać konfigurację tylko w przypadku zastosowania lub aktualizacji rozszerzenia diagnostyki.

### <a name="solution"></a>Rozwiązanie
Użyj projektanta konfiguracji diagnostyki do przenoszenia ustawień diagnostycznych do pliku konfiguracji diagnostyki (Diagnostics. wadcfg lub Diagnostics. wadcfgx dla zestawu SDK 2,5 i nowszego). Zalecane jest również zainstalowanie [zestawu Azure SDK 2,5](https://social.msdn.microsoft.com/Forums/en-US/home) i użycie najnowszej funkcji diagnostyki.

1. W menu skrótów dla roli, którą chcesz skonfigurować, wybierz polecenie Właściwości, a następnie wybierz kartę Konfiguracja.
2. W sekcji **Diagnostyka** upewnij się, że zaznaczone jest pole wyboru **Włącz diagnostykę** .
3. Wybierz przycisk **Konfiguruj** .

   ![Uzyskiwanie dostępu do opcji Włącz diagnostykę](./media/vs-azure-tools-optimizing-azure-code-in-visual-studio/IC796660.png)

   Aby uzyskać więcej informacji [, zobacz Konfigurowanie diagnostyki dla Cloud Services platformy Azure i Virtual Machines](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md) .

## <a name="avoid-declaring-dbcontext-objects-as-static"></a>Unikaj deklarowania obiektów DbContext jako static
### <a name="id"></a>ID
AP6000

### <a name="description"></a>Opis
Aby zaoszczędzić pamięć, unikaj deklarowania obiektów DbContext jako static.

Podziel się swoimi pomysłami i opiniami na temat [opinii o analizie kodu platformy Azure](https://social.msdn.microsoft.com/Forums/en-US/home).

### <a name="reason"></a>Przyczyna
Obiekty DbContext przechowują wyniki zapytania z każdego wywołania. Statyczne obiekty DbContext nie są usuwane, dopóki domena aplikacji nie zostanie zwolniona. W związku z tym, statyczny obiekt DbContext może zużywać duże ilości pamięci.

### <a name="solution"></a>Rozwiązanie
Zadeklaruj DbContext jako zmienną lokalną lub niestatyczne pole wystąpienia, użyj go dla zadania, a następnie pozwól, aby można było je usunąć po użyciu.

Poniższy Przykładowa Klasa kontrolera MVC pokazuje, jak używać obiektu DbContext.

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
Aby dowiedzieć się więcej na temat optymalizacji i rozwiązywania problemów z aplikacjami platformy Azure, zobacz [Rozwiązywanie problemów z aplikacją sieci Web w Azure App Service przy użyciu programu Visual Studio](/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio)
