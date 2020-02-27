---
title: Rejestrowanie w środowisku wieloprocesorowym | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633567"
---
# <a name="logging-in-a-multi-processor-environment"></a>Rejestrowanie w środowisku wieloprocesorowym

Możliwość użycia wielu procesorów przez program MSBuild może znacznie skrócić czas budowania projektu, ale również zwiększa złożoność rejestrowania. W środowisku jednoprocesorowym Rejestrator może obsługiwać przychodzące zdarzenia, komunikaty, ostrzeżenia i błędy w przewidywalny, sekwencyjny sposób. Jednak w środowisku z wieloma procesorami zdarzenia z kilku źródeł mogą dotrzeć jednocześnie lub poza sekwencją. Program MSBuild udostępnia nowy Rejestrator obsługujący wiele procesorów i umożliwia tworzenie niestandardowych "rejestratorów przekazywania".

## <a name="log-multiple-processor-builds"></a>Rejestruj kompilacje wielokrotnego procesora

Po utworzeniu co najmniej jednego projektu w systemie wieloprocesorowym lub wielordzeniowym zdarzenia kompilacji MSBuild dla wszystkich projektów są generowane jednocześnie. Nieuporządkowane danych zdarzenia może dotrzeć do rejestratora w tym samym czasie lub poza sekwencją. Może to spowodować Przeciążenie rejestratora oraz wydłużenie czasów kompilowania, niepoprawnych danych wyjściowych rejestratora, a nawet przerwaną kompilację. Aby rozwiązać te problemy, rejestrator programu MSBuild może przetwarzać zdarzenia poza sekwencją i skorelować zdarzenia i ich źródła.

Aby zwiększyć efektywność rejestrowania jeszcze bardziej, można utworzyć niestandardowy Rejestrator przesyłania dalej. Rejestrator niestandardowego przesyłania dalej działa jako filtr, umożliwiając wybór, przed kompilacją, zdarzenia, które mają być monitorowane. W przypadku korzystania z niestandardowego rejestratora przesyłania dalej niepożądane zdarzenia nie zapychają rejestratora, nie zasłaniają dzienników ani wolno wydłużać czas kompilacji.

### <a name="central-logging-model"></a>Centralny model rejestrowania

W przypadku kompilacji z obsługą kilku procesorów MSBuild korzysta z "centralnego modelu rejestrowania". W centralnym modelu rejestrowania wystąpienie programu *MSBuild. exe* działa jako główny proces kompilacji lub "węzeł centralny". Dodatkowe wystąpienia programu *MSBuild. exe*lub "węzły pomocnicze" są dołączone do węzła centralnego. Wszystkie rejestratory oparte na ILogger dołączone do węzła centralnego są znane jako "rejestratory centralne" i rejestratory dołączone do węzłów pomocniczych są znane jako "rejestratory pomocnicze".

Gdy wystąpi kompilacja, rejestratory pomocnicze kierują ruch zdarzenia do centralnych rejestratorów. Ponieważ zdarzenia pochodzą z kilku węzłów pomocniczych, dane docierają do centralnych węzłów jednocześnie, ale z przeplotem. Aby rozwiązać odwołania zdarzenia do projektu i zdarzenia do obiektu docelowego, argumenty zdarzeń zawierają dodatkowe informacje kontekstu zdarzenia kompilacji.

Chociaż tylko <xref:Microsoft.Build.Framework.ILogger> jest wymagana do wdrożenia przez rejestrator centralny, zalecamy także zaimplementowanie <xref:Microsoft.Build.Framework.INodeLogger>, jeśli chcesz, aby Rejestrator centralny został zainicjowany z liczbą węzłów uczestniczących w kompilacji. Następujące Przeciążenie metody <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> jest wywoływane, gdy silnik inicjuje Rejestrator:

```csharp
public interface INodeLogger: ILogger
{
    public void Initialize(IEventSource eventSource, int nodeCount);
}
```

### <a name="distributed-logging-model"></a>Model rejestrowania rozproszonego

W centralnym modelu rejestrowania zbyt dużo przychodzącego ruchu komunikatów, na przykład w przypadku jednoczesnego kompilowania wielu projektów, może przeciążyć centralny węzeł, co kładzie nacisk na system i obniża wydajność kompilacji.

Aby zmniejszyć ten problem, program MSBuild umożliwia także "model rejestrowania rozproszonego", który rozszerza centralny model rejestrowania przez umożliwienie tworzenia rejestratorów przekazywania. Rejestrator przekazywania jest dołączany do węzła pomocniczego i odbiera przychodzące zdarzenia kompilacji z tego węzła. Rejestrator przekazywania jest podobny do zwykłego rejestratora, z tą różnicą, że może odfiltrować zdarzenia, a następnie przekazać tylko odpowiednie do węzła centralnego. Zmniejsza to ruch komunikatów w węźle centralnym i w związku z tym zapewnia lepszą wydajność.

 Rejestratora przekazywania można utworzyć, implementując interfejs <xref:Microsoft.Build.Framework.IForwardingLogger>, który pochodzi z <xref:Microsoft.Build.Framework.ILogger>. Interfejs jest zdefiniowany jako:

```csharp
public interface IForwardingLogger: INodeLogger
{
    public IEventRedirector EventRedirector { get; set; }
    public int NodeId { get; set; }
}
```

Aby przesłać dalej zdarzenia w rejestratorze przekazywania, wywołaj metodę <xref:Microsoft.Build.Framework.IEventRedirector.ForwardEvent%2A> interfejsu <xref:Microsoft.Build.Framework.IEventRedirector>. Przekaż odpowiednie <xref:Microsoft.Build.Framework.BuildEventArgs>lub pochodny jako parametr.

Aby uzyskać więcej informacji, zobacz [Tworzenie rejestratorów przekazywania](../msbuild/creating-forwarding-loggers.md).

### <a name="attaching-a-distributed-logger"></a>Dołączanie rejestratora rozproszonego

Aby dołączyć Rejestrator rozproszony do kompilacji wiersza polecenia, należy użyć przełącznika `-distributedlogger` (lub `-dl` for Short). Format służący do określania nazw typów i klas rejestratora jest taki sam jak w przypadku przełącznika `-logger`, z tą różnicą, że rozproszony Rejestrator składa się z dwóch klas rejestrowania: rejestratora przekazywania i centralnego rejestratora. Poniżej przedstawiono przykład dołączania rejestratora rozproszonego:

```cmd
msbuild.exe *.proj -distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,
Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,
Culture=neutral
```

Gwiazdka (*) oddziela dwie nazwy rejestratora w przełączniku `-dl`.

## <a name="see-also"></a>Zobacz też

- [Rejestratory kompilacji](../msbuild/build-loggers.md)
- [Utwórz rejestratory przekazywania](../msbuild/creating-forwarding-loggers.md)
