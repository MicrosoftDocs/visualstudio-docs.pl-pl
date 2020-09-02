---
title: Pisanie rejestratorów obsługujących wiele procesorów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, multi-proc aware loggers
- multi-proc loggers
- loggers, multi-proc
ms.assetid: ff987d1b-1798-4803-9ef6-cc8fcc263516
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0d2eaf41ac66cd1bdf680145bef43b17cc29a505
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64802072"
---
# <a name="writing-multi-processor-aware-loggers"></a>Zapisywanie rejestratorów uwzględniających wiele procesorów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możliwość wykorzystania [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] wielu procesorów może obniżyć czas kompilowania projektu, ale również zwiększa złożoność tworzenia dzienników zdarzeń. W środowisku jednoprocesorowym zdarzenia, komunikaty, ostrzeżenia i błędy docierają do rejestratora w sposób przewidywalny, sekwencyjny. Jednak w środowisku z obsługą wielu procesorów zdarzenia z różnych źródeł mogą zostać dostarczone w tym samym czasie lub poza sekwencją. W tym celu program [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] udostępnia Rejestrator z obsługą wieloprocesorową i nowy model rejestrowania oraz umożliwia tworzenie niestandardowych "rejestratorów przekazywania".  
  
## <a name="multi-processor-logging-challenges"></a>Wyzwania dotyczące rejestrowania wieloprocesorowego  
 Po utworzeniu co najmniej jednego projektu w systemie wieloprocesorowym lub wielordzeniowym [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zdarzenia kompilacji dla wszystkich projektów są generowane w tym samym czasie. Nieuporządkowane komunikatów o zdarzeniach może dotrzeć do rejestratora w tym samym czasie lub poza sekwencją. Ponieważ [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] rejestrator 2,0 nie jest przeznaczony do obsługi tej sytuacji, może przeciążyć Rejestrator i spowodować zwiększenie czasów kompilacji, niepoprawnych danych wyjściowych rejestratora lub nawet przerwaną kompilację. Aby rozwiązać te problemy, Rejestrator (począwszy od [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 3,5) może przetwarzać zdarzenia poza sekwencją oraz skorelować zdarzenia i ich źródła.  
  
 Aby zwiększyć efektywność rejestrowania jeszcze bardziej, można utworzyć niestandardowy Rejestrator przesyłania dalej. Niestandardowy Rejestrator przesyłania dalej działa jako filtr, umożliwiając wybór, przed kompilacją, tylko zdarzenia, które mają być monitorowane. W przypadku korzystania z niestandardowego rejestratora przesyłania dalej niepożądane zdarzenia nie mogą przeciążyć rejestratora, zaśmiecać dzienników lub długo tworzyć czasy kompilacji.  
  
## <a name="multi-processor-logging-models"></a>Modele rejestrowania na wiele procesorów  
 Aby zapewnić problemy z kompilacją z obsługą wiele procesorów, program [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] obsługuje dwa modele rejestrowania, centralne i rozproszone.  
  
### <a name="central-logging-model"></a>Centralny model rejestrowania  
 W centralnym modelu rejestrowania pojedyncze wystąpienie MSBuild.exe działa jako "centralny węzeł" i podrzędne wystąpienia węzła centralnego ("węzły pomocnicze") dołączają do centralnego węzła, aby ułatwić wykonywanie zadań kompilacji.  
  
 ![Model rejestratora centralnego](../msbuild/media/centralnode.png "CentralNode")  
  
 Rejestratory różnych typów, które dołączają do węzła centralnego, są znane jako "rejestratory centralne". Tylko jedno wystąpienie każdego typu rejestratora może być dołączone do węzła centralnego w tym samym czasie.  
  
 Gdy wystąpi kompilacja, węzły pomocnicze kierują zdarzenia kompilacji do węzła centralnego. Węzeł centralny kieruje wszystkie zdarzenia, a także te węzły pomocnicze do co najmniej jednego dołączonego rejestratora centralnego. Rejestratory tworzą następnie pliki dziennika, które są oparte na danych przychodzących.  
  
 Chociaż <xref:Microsoft.Build.Framework.ILogger> jest to wymagane tylko do wdrożenia przez rejestrator centralny, zalecamy także zaimplementowanie, <xref:Microsoft.Build.Framework.INodeLogger> Aby centralny Rejestrator zainicjuje się liczbą węzłów uczestniczących w kompilacji. Następujące Przeciążenie <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> metody wywołuje się, gdy aparat inicjuje rejestrator.  
  
```  
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
 Wszystkie istniejące wbudowane <xref:Microsoft.Build.Framework.ILogger> rejestratory mogą działać jako rejestratory środkowe i można dołączyć do kompilacji. Jednak centralne rejestratory zapisywane bez jawnej obsługi scenariuszy rejestrowania wieloprocesorowego i zdarzeń poza kolejnością mogą przerwać kompilację lub utworzyć nieaktualne dane wyjściowe.  
  
### <a name="distributed-logging-model"></a>Model rejestrowania rozproszonego  
 W centralnym modelu rejestrowania zbyt dużo ruchu komunikatów przychodzących może przeciążyć centralny węzeł, na przykład, gdy wiele projektów kompiluje się w tym samym czasie. Pozwala to na obciążenie zasobów systemowych i zmniejszenie wydajności kompilacji. Aby ułatwić ten problem, program [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] obsługuje dystrybuowany model rejestrowania.  
  
 ![Model rejestrowania rozproszonego](../msbuild/media/distnode.png "DistNode")  
  
 Model rejestrowania rozproszonego rozszerza centralny model rejestrowania, umożliwiając tworzenie rejestratora przesyłania dalej.  
  
#### <a name="forwarding-loggers"></a>Rejestratory przesyłania dalej  
 Rejestrator przekazywania to pomocniczy, lekki Rejestrator z filtrem zdarzeń, który dołącza do węzła pomocniczego i odbiera przychodzące zdarzenia kompilacji z tego węzła. Filtruje zdarzenia przychodzące i przekazuje tylko te, które są określone w węźle centralnym. Zmniejsza to ruch komunikatów wysyłany do węzła centralnego i zwiększa ogólną wydajność kompilacji.  
  
 Istnieją dwa sposoby używania rejestrowania rozproszonego w następujący sposób:  
  
- Dostosuj rejestratora wstępnego przekazywania o nazwie <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> .  
  
- Napisz własny niestandardowy Rejestrator przesyłania dalej.  
  
  Możesz zmodyfikować ConfigurableForwardingLogger zgodnie z wymaganiami. W tym celu wywołaj rejestrator w wierszu polecenia przy użyciu MSBuild.exe i Wyświetl listę zdarzeń kompilacji, które mają być przekazywane przez rejestrator do węzła centralnego.  
  
  Alternatywnie można utworzyć niestandardowy Rejestrator przesyłania dalej. Tworząc niestandardowy Rejestrator przesyłania dalej, można dostosować zachowanie rejestratora. Tworzenie niestandardowego rejestratora przesyłania dalej jest jednak bardziej skomplikowane niż tylko Dostosowywanie ConfigurableForwardingLogger. Aby uzyskać więcej informacji, zobacz [Tworzenie rejestratorów przekazywania](../msbuild/creating-forwarding-loggers.md).  
  
## <a name="using-the-configurableforwardinglogger-for-simple-distributed-logging"></a>Używanie ConfigurableForwardingLogger na potrzeby prostego rejestrowania rozproszonego  
 Aby dołączyć ConfigurableForwardingLogger lub niestandardowy Rejestrator przesyłania dalej, użyj `/distributedlogger` przełącznika ( `/dl` dla krótkiej) w MSBuild.exe kompilacji wiersza polecenia. Format służący do określania nazw typów i klas rejestratora jest taki sam jak w przypadku `/logger` przełącznika, z tą różnicą, że Rejestrator rozproszony zawsze ma dwie klasy rejestrowania zamiast jednego, rejestratora przekazywania i centralnego rejestratora. Poniżej przedstawiono przykład sposobu dołączania niestandardowego rejestratora przesyłania dalej o nazwie XMLForwardingLogger.  
  
```  
msbuild.exe myproj.proj/distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,Culture=neutral  
```  
  
> [!NOTE]
> Gwiazdka (*) musi oddzielić dwie nazwy rejestratora w `/dl` przełączniku.  
  
 Korzystanie z ConfigurableForwardingLogger przypomina korzystanie z dowolnego innego Rejestratora (jak przedstawiono w [uzyskiwaniu dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md)), z tą różnicą, że należy dołączyć Rejestrator ConfigurableForwardingLogger zamiast typowego [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] rejestratora i określić jako parametry zdarzenia, które mają być przekazywane przez ConfigurableForwardingLogger do węzła centralnego.  
  
 Na przykład jeśli chcesz otrzymywać powiadomienia tylko wtedy, gdy kompilacja rozpocznie się i skończy, a gdy wystąpi błąd, należy przekazać `BUILDSTARTEDEVENT` , `BUILDFINISHEDEVENT` i `ERROREVENT` jako parametry. Wiele parametrów można przekazywać, rozdzielając je średnikami. Poniżej przedstawiono przykład użycia ConfigurableForwardingLogger do przesyłania dalej tylko `BUILDSTARTEDEVENT` `BUILDFINISHEDEVENT` zdarzeń, i `ERROREVENT` .  
  
```  
msbuild.exe myproj.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,Culture=neutral*ConfigureableForwardingLogger,C:\My.dll;BUILDSTARTEDEVENT; BUILDFINISHEDEVENT;ERROREVENT  
```  
  
 Poniżej znajduje się lista dostępnych parametrów ConfigurableForwardingLogger.  
  
|Parametry ConfigurableForwardingLogger|  
|---------------------------------------------|  
|BUILDSTARTEDEVENT|  
|BUILDFINISHEDEVENT|  
|PROJECTSTARTEDEVENT|  
|PROJECTFINISHEDEVENT|  
|TARGETSTARTEDEVENT|  
|TARGETFINISHEDEVENT|  
|TASKSTARTEDEVENT|  
|TASKFINISHEDEVENT|  
|ERROREVENT|  
|WARNINGEVENT|  
|HIGHMESSAGEEVENT|  
|NORMALMESSAGEEVENT|  
|LOWMESSAGEEVENT|  
|CUSTOMEVENT|  
|WIERSZA polecenia|  
|PERFORMANCESUMMARY|  
|Nosummary|  
|SHOWCOMMANDLINE|  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie rejestratorów przekazywania](../msbuild/creating-forwarding-loggers.md)
