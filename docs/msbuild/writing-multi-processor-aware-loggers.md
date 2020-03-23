---
title: Pisanie rejestratorów z uwzględnieniem wielu procesorów | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, multi-proc aware loggers
- multi-proc loggers
- loggers, multi-proc
ms.assetid: ff987d1b-1798-4803-9ef6-cc8fcc263516
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 886e012b026ef17b512a7e134d080382744783ef
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630750"
---
# <a name="write-multi-processor-aware-loggers"></a>Pisanie rejestratorów obsługujących wiele procesorów

Możliwość MSBuild do korzystania z wielu procesorów może zmniejszyć czas tworzenia projektu, ale również zwiększa złożoność tworzenia rejestrowania zdarzeń. W środowisku z jednym procesorem zdarzenia, komunikaty, ostrzeżenia i błędy docierają do rejestratora w przewidywalny, sekwencyjny sposób. Jednak w środowisku wieloprocesorowym zdarzenia z różnych źródeł mogą docierać w tym samym czasie lub poza kolejnością. Aby to zapewnić, MSBuild zapewnia rejestrator z uwzględnieniem wielu procesorów i nowy model rejestrowania i umożliwia tworzenie niestandardowych "rejestratorów przekazywania".

## <a name="multi-processor-logging-challenges"></a>Wyzwania związane z rejestrowaniem wielu procesorów

 Podczas tworzenia jednego lub więcej projektów w systemie wieloprocesorowym lub wielordzeniowym zdarzenia kompilacji MSBuild dla wszystkich projektów są generowane w tym samym czasie. Lawina komunikatów zdarzeń może dojść do rejestratora w tym samym czasie lub poza kolejnością. Ponieważ rejestrator MSBuild 2.0 nie jest przeznaczony do obsługi tej sytuacji, może przeciągnąć rejestratora i spowodować wydłużenie czasu kompilacji, niepoprawne dane wyjściowe rejestratora lub nawet przerwanej kompilacji. Aby rozwiązać te problemy, rejestrator (począwszy od MSBuild 3.5) może przetwarzać zdarzenia pozasekwowania i skorelować zdarzenia i ich źródła.

 Można jeszcze bardziej zwiększyć wydajność rejestrowania, tworząc niestandardowy rejestrator przekazywania. Niestandardowy rejestrator przekazywania działa jako filtr, umożliwiając wybranie, przed utworzeniem, tylko zdarzenia, które chcesz monitorować. Korzystając z niestandardowego rejestratora przekazywania, niepożądane zdarzenia nie mogą przeciążyć rejestratora, zaśmiecać dzienniki lub powolny czas kompilacji.

## <a name="multi-processor-logging-models"></a>Wieloprocesorowe modele rejestrowania

 Aby zapewnić problemy kompilacji związane z wieloma procesorami, MSBuild obsługuje dwa modele rejestrowania, centralne i rozproszone.

### <a name="central-logging-model"></a>Centralny model rejestrowania

 W centralnym modelu rejestrowania *pojedyncze wystąpienie msbuild.exe* działa jako "węzeł centralny", a wystąpienia podrzędne węzła centralnego ("węzły pomocnicze") dołączyć do węzła centralnego, aby ułatwić wykonywanie zadań kompilacji.

 ![Model rejestratora centralnego](../msbuild/media/centralnode.png "CentralNode (Niem.")

 Rejestratory różnych typów, które dołączają do węzła centralnego są znane jako "rejestratory centralne". Tylko jedno wystąpienie każdego typu rejestratora można dołączyć do węzła centralnego w tym samym czasie.

 Gdy kompilacja wystąpi, węzły pomocnicze trasy ich zdarzenia kompilacji do węzła centralnego. Węzeł centralny kieruje wszystkie zdarzenia, a także te węzłów pomocniczych, do jednego lub więcej dołączonych rejestratorów centralnych. Rejestratory następnie utworzyć pliki dziennika, które są oparte na danych przychodzących.

 Chociaż <xref:Microsoft.Build.Framework.ILogger> tylko jest wymagane do zaimplementowania przez rejestratora <xref:Microsoft.Build.Framework.INodeLogger> centralnego, zaleca się również zaimplementować tak, aby centralny rejestrator inicjuje z liczbą węzłów, które uczestniczą w kompilacji. Następujące przeciążenie <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> metody wywołuje, gdy aparat inicjuje rejestratora.

```csharp
public interface INodeLogger: ILogger
{
    public void Initialize(IEventSource eventSource, int nodeCount);
}
```

 Wszelkie istniejące <xref:Microsoft.Build.Framework.ILogger>rejestratory oparte na tym może działać jako rejestratory centralne i można dołączyć do kompilacji. Jednak rejestratory centralne napisane bez jawnej obsługi scenariuszy rejestrowania wielu procesorów i zdarzeń poza kolejnością może przerwać kompilacji lub produkcji bez znaczenia danych wyjściowych.

### <a name="distributed-logging-model"></a>Rozproszony model rejestrowania

 W modelu rejestrowania centralnego zbyt dużo ruchu przychodzącego wiadomości może przytłoczyć węzeł centralny, na przykład, gdy wiele projektów kompilacji w tym samym czasie. Może to naprężenia zasobów systemowych i zmniejszyć wydajność kompilacji. Aby złagodzić ten problem, MSBuild obsługuje model rejestracji rozproszonej.

 ![Rozproszony model rejestrowania](../msbuild/media/distnode.png "DistNode ( DistNode )")

 Model rejestrowania rozproszonego rozszerza centralny model rejestrowania, umożliwiając utworzenie rejestratora przekazywania.

#### <a name="forwarding-loggers"></a>Rejestratory przekazywania

 Rejestrator przekazywania jest rejestratorem pomocniczym, odciążonym, który ma filtr zdarzeń, który dołącza do węzła pomocniczego i odbiera przychodzące zdarzenia kompilacji z tego węzła. Filtruje zdarzenia przychodzące i przekazuje tylko te, które określisz do węzła centralnego. Zmniejsza to ruch komunikatów, który jest wysyłany do węzła centralnego i zwiększa ogólną wydajność kompilacji.

 Istnieją dwa sposoby korzystania z rejestrowania rozproszonego w następujący sposób:

- Dostosuj wstępnie sfabrykowany rejestrator <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger>przekazywania o nazwie .

- Napisz własny rejestrator przekazywania niestandardowych.

Można zmodyfikować ConfigurableForwardingLogger zgodnie z wymaganiami. Aby to zrobić, należy wywołać rejestratora w wierszu polecenia za pomocą *programu MSBuild.exe*i wyświetlić listę zdarzeń kompilacji, które mają być przekazywane do węzła centralnego.

Alternatywnie można utworzyć niestandardowy rejestrator przekazywania. Tworząc rejestratora przekazywania niestandardowego, można dostosować zachowanie rejestratora. Jednak tworzenie rejestratora niestandardowych przekazywania jest bardziej skomplikowane niż tylko dostosowywanie ConfigurableForwardingLogger. Aby uzyskać więcej informacji, zobacz [Tworzenie rejestratorów przekazywania](../msbuild/creating-forwarding-loggers.md).

## <a name="using-the-configurableforwardinglogger-for-simple-distributed-logging"></a>Korzystanie z konfigurowalnyforwardingLogger dla prostego rejestrowania rozproszonego

 Aby dołączyć plik ConfigurableForwardingLogger lub niestandardowy rejestrator przekazywania, użyj `-distributedlogger` przełącznika (w`-dl` skrócie) w kompilacji wiersza polecenia *MSBuild.exe.* Format określania nazw typów rejestratora i klas jest taki sam `-logger` jak dla przełącznika, z tą różnicą, że rozproszony rejestrator zawsze ma dwie klasy rejestrowania zamiast jednej, rejestratora przekazywania i rejestratora centralnego. Poniżej przedstawiono przykład sposobu dołączania niestandardowego rejestratora przekazywania o nazwie XMLForwardingLogger.

```cmd
msbuild.exe myproj.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,Culture=neutral
```

> [!NOTE]
> Gwiazdka (*) musi oddzielić dwie nazwy `-dl` rejestratora w przełączniku.

 Korzystanie z ConfigurableForwardingLogger jest jak przy użyciu innego rejestratora (zgodnie z opisem w [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)), z tą różnicą, że dołączyć ConfigurableForwardingLogger rejestratora zamiast typowego rejestratora MSBuild i określić jako parametry zdarzenia, które mają konfigurowaćForwardingLogger przekazać do węzła centralnego.

 Na przykład, jeśli chcesz otrzymywać powiadomienia tylko wtedy, gdy kompilacja rozpoczyna się i `BUILDSTARTEDEVENT` `BUILDFINISHEDEVENT`kończy, `ERROREVENT` a gdy wystąpi błąd, należy przekazać , i jako parametry. Wiele parametrów można przekazać, oddzielając je średnikami. Poniżej przedstawiono przykład użycia configurableForwardingLogger do przesyłania `BUILDSTARTEDEVENT` `BUILDFINISHEDEVENT`dalej `ERROREVENT` tylko , i zdarzenia.

```cmd
msbuild.exe myproj.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*ConfigureableForwardingLogger,C:\My.dll;BUILDSTARTEDEVENT; BUILDFINISHEDEVENT;ERROREVENT
```

 Poniżej znajduje się lista dostępnych parametrów ConfigurableForwardingLogger.

|Konfigurowalne parametry rejestratoraforwarding|
| - |
|BUILDSTARTEDEVENT|
|BUILDFINISHEDEVENT|
|PROJECTSTARTEDEVENT|
|PROJEKTFINISHEDEVENT|
|TARGETSTARTEDEVENT (POCZĄTEK DOCELOWYCH WYDARZEŃ)|
|CELFINISHEDEVENT|
|ZADANIESTARTEDEVENT|
|ZADANIE ZAKOŃCZONEVENT|
|BŁĄD|
|OSTRZEŻENIEEVENT|
|HIGHMESSAGEEVENT|
|NORMALMESSAGEEVENT|
|LOWMESSAGEEVENT|
|CUSTOMEVENT (CUSTOMEVENT)|
|Commandline|
|WYNIKIUMMARY|
|NOSUMMARY ( NOSUMMARY )|
|SHOWCOMMANDLINE (SHOWCOMMANDLINE)|

## <a name="see-also"></a>Zobacz też

- [Tworzenie rejestratorów przekazywania](../msbuild/creating-forwarding-loggers.md)