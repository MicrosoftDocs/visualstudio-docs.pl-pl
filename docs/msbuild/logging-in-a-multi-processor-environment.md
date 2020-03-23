---
title: Logowanie w środowisku wieloprocesorowym | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, multi-processor logging
- MSBuild, logging
ms.assetid: dd4dae65-ed04-4883-b48d-59bcb891c4dc
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0c332fb67e96bdfea0059de11441da7c32871633
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633567"
---
# <a name="logging-in-a-multi-processor-environment"></a>Logowanie w środowisku wieloprocesorowym

Możliwość MSBuild do korzystania z wielu procesorów może znacznie zmniejszyć czas tworzenia projektu, ale również zwiększa złożoność rejestrowania. W środowisku z jednym procesorem rejestrator może obsługiwać przychodzące zdarzenia, komunikaty, ostrzeżenia i błędy w przewidywalny, sekwencyjny sposób. Jednak w środowisku wieloprocesorowym zdarzenia z kilku źródeł mogą docierać jednocześnie lub poza kolejnością. MSBuild udostępnia nowy rejestrator obsługujący wiele procesorów i umożliwia tworzenie niestandardowych "rejestratorów przekazywania".

## <a name="log-multiple-processor-builds"></a>Rejestrowanie kompilacji z wieloma procesorami

Podczas tworzenia jednego lub więcej projektów w systemie wieloprocesorowym lub wielordzeniowym zdarzenia kompilacji MSBuild dla wszystkich projektów są generowane jednocześnie. Lawina danych zdarzeń może dotrzeć do rejestratora w tym samym czasie lub poza kolejnością. Może to przeciążeć rejestratora i spowodować wydłużenie czasu kompilacji, niepoprawne dane wyjściowe rejestratora, a nawet przerwanej kompilacji. Aby rozwiązać te problemy, rejestrator MSBuild może przetwarzać zdarzenia pozasekwowane i skorelować zdarzenia i ich źródła.

Można jeszcze bardziej zwiększyć wydajność rejestrowania, tworząc niestandardowy rejestrator przekazywania. Rejestrator do przekazywania niestandardowego działa jako filtr, umożliwiając wybranie, przed utworzeniem, zdarzeń, które chcesz monitorować. Podczas korzystania z rejestratora przekazywania niestandardowego, niepożądane zdarzenia nie przeciągają rejestratora, zaśmiecać dzienniki lub powolne czasy kompilacji.

### <a name="central-logging-model"></a>Centralny model rejestrowania

W przypadku kompilacji wieloprocesorowych MSBuild używa "centralnego modelu rejestrowania". W modelu rejestrowania centralnego *wystąpienie msbuild.exe* działa jako podstawowy proces kompilacji lub "węzeł centralny". Pomocnicze wystąpienia *msbuild.exe*lub "węzły pomocnicze" są dołączone do węzła centralnego. Wszelkie rejestratory oparte na ILogger dołączone do węzła centralnego są znane jako "rejestratory centralne", a rejestratory dołączone do węzłów pomocniczych są znane jako "rejestratory pomocnicze".

Po wystąpieniu kompilacji rejestratory pomocnicze trasy ich ruchu zdarzeń do rejestratorów centralnych. Ponieważ zdarzenia pochodzą z kilku węzłów pomocniczych, dane docierają do węzła centralnego jednocześnie, ale przeplatane. Aby rozpoznać odwołania do zdarzenia do projektu i zdarzenia do celu, argumenty zdarzenia zawierają dodatkowe informacje kontekstu zdarzenia kompilacji.

Chociaż <xref:Microsoft.Build.Framework.ILogger> tylko jest wymagane do zaimplementowania przez rejestratora <xref:Microsoft.Build.Framework.INodeLogger> centralnego, zaleca się również zaimplementować, jeśli chcesz, aby rejestrator centralny zainicjować z liczbą węzłów, które uczestniczą w kompilacji. Następujące przeciążenie <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> metody jest wywoływana, gdy aparat inicjuje rejestratora:

```csharp
public interface INodeLogger: ILogger
{
    public void Initialize(IEventSource eventSource, int nodeCount);
}
```

### <a name="distributed-logging-model"></a>Rozproszony model rejestrowania

W modelu rejestrowania centralnego zbyt dużo ruchu przychodzącego wiadomości, takich jak gdy wiele projektów kompilacji na raz, może przytłoczyć węzeł centralny, który podkreśla system i obniża wydajność kompilacji.

Aby zmniejszyć ten problem, MSBuild włącza również "rozproszony model rejestrowania", który rozszerza centralny model rejestrowania, umożliwiając tworzenie rejestratorów przekazywania. Rejestrator przekazywania jest dołączony do węzła pomocniczego i odbiera przychodzące zdarzenia kompilacji z tego węzła. Rejestrator przekazywania jest tak samo jak zwykły rejestrator, z tą różnicą, że można filtrować zdarzenia, a następnie do przodu tylko te żądane do węzła centralnego. Zmniejsza to ruch komunikatów w węźle centralnym i w związku z tym umożliwia lepszą wydajność.

 Rejestratora przekazywania można utworzyć, implementując <xref:Microsoft.Build.Framework.IForwardingLogger> interfejs, który <xref:Microsoft.Build.Framework.ILogger>pochodzi od programu . Interfejs jest zdefiniowany jako:

```csharp
public interface IForwardingLogger: INodeLogger
{
    public IEventRedirector EventRedirector { get; set; }
    public int NodeId { get; set; }
}
```

Aby przekazać dalej zdarzenia w rejestratorze <xref:Microsoft.Build.Framework.IEventRedirector.ForwardEvent%2A> przekazywania, należy wywołać metodę <xref:Microsoft.Build.Framework.IEventRedirector> interfejsu. Przekazać odpowiedni <xref:Microsoft.Build.Framework.BuildEventArgs>lub pochodny jako parametr.

Aby uzyskać więcej informacji, zobacz [Tworzenie rejestratorów przekazywania](../msbuild/creating-forwarding-loggers.md).

### <a name="attaching-a-distributed-logger"></a>Dołączanie rejestratora rozproszonego

Aby dołączyć rozproszony rejestrator do kompilacji wiersza `-distributedlogger` polecenia, `-dl` użyj przełącznika (lub, w skrócie). Format określania nazw typów rejestratora i klas są takie same `-logger` jak dla przełącznika, z tą różnicą, że rozproszony rejestrator składa się z dwóch klas rejestrowania: rejestratora przekazywania i rejestratora centralnego. Poniżej znajduje się przykład dołączania rozproszonego rejestratora:

```cmd
msbuild.exe *.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,
Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,
Culture=neutral
```

Gwiazdka (*) oddziela dwie nazwy rejestratora `-dl` w przełączniku.

## <a name="see-also"></a>Zobacz też

- [Tworzenie rejestratorów](../msbuild/build-loggers.md)
- [Tworzenie rejestratorów przekazywania](../msbuild/creating-forwarding-loggers.md)
