---
title: Logowanie w środowisku wielu procesorów | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, multi-processor logging
- MSBuild, logging
ms.assetid: dd4dae65-ed04-4883-b48d-59bcb891c4dc
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 35184f6ef724a9f0e803a10c9bda2c6981313ed6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68205972"
---
# <a name="logging-in-a-multi-processor-environment"></a>Logowanie w środowisku wielu procesorów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możliwość używania wielu procesorów MSBuild może znacznie skrócić czas tworzenia projektu, ale również dodaje złożoności do rejestrowania. W środowisku jednoprocesorowym rejestratora może obsługiwać przychodzących zdarzenia, wiadomości, ostrzeżenia i błędy w sposób przewidywalny i sekwencyjne. Jednak w środowisku wielu procesorów zdarzenia z kilku źródeł mogą pojawić się równocześnie lub poza sekwencją. MSBuild zapewnia nowy Rejestrator procesorów uwzględniających oraz umożliwia tworzenie niestandardowych "przekazywania rejestratorów."  
  
## <a name="logging-multiple-processor-builds"></a>Rejestrowanie wielu procesorów kompilacji  
 Gdy tworzysz jeden lub więcej projektów w systemie wieloprocesorowym lub wielordzeniowych MSBuild kompilacji zdarzenia dla wszystkich projektów są generowane, jednocześnie. U rejestratora lawiny dane zdarzeń może pojawić się w tym samym czasie lub poza sekwencją. To może przeciąży rejestratora i czasy kompilacji zwiększona, rejestratora nieprawidłowe dane wyjściowe lub uszkodzone kompilacji. Aby rozwiązać te problemy, rejestratora MSBuild przetwarzanie zdarzenia typu "out sekwencji" i skorelować zdarzenia i ich źródła.  
  
 Może poprawić wydajność rejestrowania jeszcze więcej, tworząc rejestratora przekazywanie niestandardowych. Rejestrator niestandardowych przekazywania działa jako filtr, umożliwiając wybierz przed kompilacją, zdarzenia, które chcesz monitorować. Korzystając z Rejestratora przekazywanie niestandardowych zdarzeń niepożądanych nie przeciąży rejestratora, zbliżyć do siebie te dzienniki lub wolno budowania razy.  
  
### <a name="central-logging-model"></a>Model centralnego rejestrowania  
 Dla kompilację na wielu procesorach program MSBuild używa "model centralnego rejestrowania". W modelu centralnego rejestrowania wystąpienie MSBuild.exe działa jako proces kompilacji głównej lub "węźle centralnym." Dodatkowych wystąpień MSBuild.exe lub "węzłów pomocniczych" są dołączone do węźle centralnym. Rejestratory na podstawie ILogger dołączony do węzła centralnej są określane jako "centralnej rejestratorów" i rejestratorów dołączony do węzłów pomocniczych są określane jako "dodatkowej rejestratorów."  
  
 W przypadku kompilacji dodatkowej rejestratorów kierować ruch zdarzeń do centralnej rejestratorów. Ponieważ generowane przez kilka węzłów pomocniczych te zdarzenia, dane dociera węźle centralnym jednocześnie, ale z przeplotem. Aby rozwiązać odwołania do zdarzeń do projektu i cel zdarzenia, argumenty zdarzenia obejmują informacje o kontekście zdarzenia kompilacji dodatkowe.  
  
 Mimo że jest to jedyna <xref:Microsoft.Build.Framework.ILogger> jest wymagane do zaimplementowania przez rejestrator centralnej, firma Microsoft zaleca również Implementowanie <xref:Microsoft.Build.Framework.INodeLogger> chcącym rejestratora centralnego można zainicjować z liczbą węzłów, które uczestniczą w kompilacji. Następujące przeciążenia <xref:Microsoft.Build.Framework.ILogger.Initialize%2A> metoda jest wywoływana, gdy aparat rejestratora:  
  
```  
public interface INodeLogger: ILogger  
{  
    public void Initialize(IEventSource eventSource, int nodeCount);  
}  
```  
  
### <a name="distributed-logging-model"></a>Model rejestrowania rozproszonego  
 W modelu centralnego rejestrowania zbyt dużej ilości przychodzącego ruchu wiadomości, na przykład podczas kompilacji w przypadku wielu projektów naraz, może spowodować przeciążenie węźle centralnym, co podkreśla systemu i obniża wydajność kompilacji.  
  
 Aby ograniczyć ten problem, MSBuild umożliwia również "model rejestrowania rozproszonego", który rozszerzają model centralnego rejestrowania, umożliwiając tworzenie przekazywania rejestratorów. Rejestrator przekazywania jest dołączony do węzła pomocniczego i odbiera zdarzenia przychodzące kompilacji z tego węzła. Rejestrator przekazywania działa tak jak regularne rejestratora, z tą różnicą, że można filtrować zdarzenia i następnie prześlij je dalej tylko żądane tweety na węźle centralnym. Zmniejsza ruch komunikatów w węźle centralnym i dlatego zapewnia lepszą wydajność.  
  
 Możesz utworzyć rejestratora przekazywania przez zaimplementowanie <xref:Microsoft.Build.Framework.IForwardingLogger> interfejs, który pochodzi od klasy <xref:Microsoft.Build.Framework.ILogger>. Interfejs jest określony jako:  
  
```  
public interface IForwardingLogger: INodeLogger  
{  
    public IEventRedirector EventRedirector { get; set; }  
    public int NodeId { get; set; }  
}  
```  
  
 Do przesyłania dalej zdarzeń w rejestratora przekazywania, należy wywołać <xref:Microsoft.Build.Framework.IEventRedirector.ForwardEvent%2A> metody <xref:Microsoft.Build.Framework.IEventRedirector> interfejsu. Przekaż odpowiednią <xref:Microsoft.Build.Framework.BuildEventArgs>, lub Utworów zależnych, jako parametr.  
  
 Aby uzyskać więcej informacji, zobacz [tworzenie przekazywania rejestratorów](../msbuild/creating-forwarding-loggers.md).  
  
### <a name="attaching-a-distributed-logger"></a>Dołączanie rozproszonych rejestratora  
 Aby dołączanie rozproszonych rejestratora dla kompilacji wiersza polecenia, należy użyć `/distributedlogger` (lub `/dl` w skrócie) przełącznika. Format określająca nazwy klasy i typy rejestratora są takie same jak w przypadku `/logger` przełączyć, chyba że rozproszonych rejestratora składa się z dwóch klas rejestrowania: Rejestrator przekazywania i rejestratora centralnego. Poniżej znajduje się przykład dołączenia rejestratora rozproszonych:  
  
```  
msbuild.exe *.proj /distributedlogger:XMLCentralLogger,MyLogger,Version=1.0.2,  
Culture=neutral*XMLForwardingLogger,MyLogger,Version=1.0.2,  
Culture=neutral  
```  
  
 Znak gwiazdki (*) oddziela nazwy dwóch rejestratora w `/dl` przełącznika.  
  
## <a name="see-also"></a>Zobacz też  
 [Rejestratory kompilacji](../msbuild/build-loggers.md)   
 [Tworzenie przekazywania rejestratorów](../msbuild/creating-forwarding-loggers.md)
