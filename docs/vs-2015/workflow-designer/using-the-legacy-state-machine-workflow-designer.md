---
title: Używanie starszej wersji komputera Projektant przepływu pracy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- StateFinalizationActivity activity
- StateActivity activity
- SetStateActivity activity
- EventDrivenActivity activity
- state machine workflow designer
- state machine workflows, designer
- state machine workflows, activities
- StateInitializationActivity activity
ms.assetid: 2cd21123-35c2-4eaf-82f6-86fce7a8f04d
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8c2b1ce1f1b2c6a16b5576880904feadf37a3e7b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72606769"
---
# <a name="using-the-legacy-state-machine-workflow-designer"></a>Używanie starszej wersji Projektanta przepływu pracy automatu stanów
Podczas tworzenia nowego projektu przepływu pracy automatu stanów w [!INCLUDE[vs2010](../includes/vs2010-md.md)], która jest przeznaczona dla [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)], można użyć **aplikacji konsolowej przepływu pracy automatu Stanów** lub **biblioteki przepływu pracy** automatu Stanów szablon projektu. W przypadku wybrania jednego z tych szablonów projektów komputera stanu Projektant automatu stanów zostanie przedstawiony jako starszy interfejs użytkownika projektanta przepływu pracy. Aby uzyskać informacje na temat starszych szablonów projektów komputera stanu, zobacz [How to: Create State automat Workflow Console Applications (starsze)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) i [instrukcje: Create a State Machine Workflow Library (starsza wersja)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md).

 Przepływ pracy automatu Stanów składa się z zestawu Stanów. Jeden stan jest oznaczany jako stan początkowy. Każdy stan może odbierać określony zestaw zdarzeń. Na podstawie zdarzenia można przejść do innego stanu. Przepływ pracy automatu Stanów może mieć stan końcowy. Po zakończeniu przejścia do stanu końcowego przepływ pracy zostaje zakończony.

## <a name="state-machine-designer-views"></a>Widoki projektanta automatu Stanów
 Projektant automatu Stanów jest projektantem dowolnego rzędu, co oznacza, że działania mogą być swobodnie przemieszczane na powierzchni projektowej. Projektant automatu Stanów ma dwa widoki: widok *stanu* i widok *sterowany zdarzeniami* .

 Widok stanu przedstawia działania stanu i działania sterowane zdarzeniami, które mogą być zawarte w działaniu stanu. W tym widoku przejścia z jednego stanu do drugiego są reprezentowane przez wiersze, które wykraczają poza działanie sterowane zdarzeniami w jednym stanie z innym stanem. Możesz również tworzyć przejścia przez rysowanie linii samodzielnie. Aby narysować przejście, wybierz działanie sterowane zdarzeniami, a następnie wybierz jeden z uchwytów działania i przeciągnij go. Ta akcja rysuje linię. Ten wiersz jest następnie dołączany do stanu docelowego, wskazując przejście między Stanami.

 Aby uzyskać dostęp do widoku sterowanego zdarzeniami, kliknij dwukrotnie działanie sterowane zdarzeniami. Wyświetlany Projektant jest podobny do projektanta sekwencyjnego przepływu pracy. Na górze projektanta na pasku nawigacyjnym wyświetlana jest hierarchia działań do wyświetlonego działania sterowanego zdarzeniami. Możesz przejść z powrotem do widoku stanu, klikając dowolny element w wyświetlonej hierarchii. Jeśli nastąpiło przejście z jednego stanu do innego w widoku stanu, a Jeśli wyświetlasz widok sterowany zdarzeniami tego działania, to działanie ustawiania stanu jest dodawane do działania sterowanego zdarzeniami. Jeśli zmienisz właściwości działania Ustaw stan, zostanie ono odzwierciedlone w widoku stanu.

## <a name="state-machine-workflow-activities"></a>Działania przepływu pracy automatu Stanów
 W poniższej tabeli opisano podstawowe działania, które są używane w Projektancie przepływu pracy automatu Stanów.

|Nazwa przybornika|Działanie|Opis|
|------------------|--------------|-----------------|
|**State**|[Działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Reprezentuje stan na komputerze stanu; może zawierać dodatkowe działania **działanie StateActivity** . Aby uzyskać więcej informacji, zobacz [Korzystanie z działania działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|
|**Metoda setstate**|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Określa przejście do nowego stanu. Aby uzyskać więcej informacji, zobacz [Korzystanie z działania SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|
|**StateInitialization**|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Wykonuje się po wprowadzeniu stanu; może zawierać inne działania. Aby uzyskać więcej informacji, zobacz [Korzystanie z działania StateInitialization](http://go.microsoft.com/fwlink?LinkID=65006).|
|**StateFinalization**|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Wykonuje zawarte działania przy opuszczaniu działania [działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) . Aby uzyskać więcej informacji, zobacz [Korzystanie z działania StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|
|**EventDriven**|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Używane dla Stanów, które polegają na zdarzeniu zewnętrznym do rozpoczęcia wykonywania. Działanie **EventDrivenActivity** musi mieć działanie implementujące interfejs [IEventActivity](http://go.microsoft.com/fwlink?LinkID=65032) jako pierwsze działanie podrzędne. Aby uzyskać więcej informacji, zobacz [Korzystanie z działania EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|

 Głównym składnikiem przepływu pracy automatu Stanów jest działanie [działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) . Gdy zdarzenia są przechwytywane w różnych punktach przepływu pracy automatu Stanów, w celu obsługi zadań skojarzonych ze zdarzeniami są wprowadzane różne stany. Przepływ pracy może opuścić czas trwania przepływu pracy i wprowadzić kilka różnych stanów. Te Stany łączą się ze sobą przy użyciu działania [SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041) .

 Po przeciągnięciu nowego **działanie StateActivity** na powierzchnię projektu przepływu pracy można dodać [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029), [StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044), [StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)lub dodatkowe działania **działanie StateActivity** jako działania podrzędne.

> [!CAUTION]
> W przypadku tworzenia przepływów pracy za pomocą projektanta przepływu pracy automatu Stanów należy monitorować strukturę przepływu pracy, który jest projektowany przy użyciu okna widoku **konspektu dokumentu** . Widok struktury przepływu pracy automatu stanów w oknie widok **konspektu dokumentu** odzwierciedla układ logiczny działań w pliku znaczników przepływu pracy. Układ fizyczny działań przepływu pracy, które pojawiają się na powierzchni projektowej, może nie dublować układu logicznego działań w pliku znaczników przepływu pracy.
>
> Aby otworzyć okno **Konspekt dokumentu** , w menu **Widok** wskaż polecenie **inne okna**, a następnie wybierz polecenie **Konspekt dokumentu**.

## <a name="see-also"></a>Zobacz też
 [Instrukcje: Tworzenie aplikacji konsoli przepływu pracy automatu Stanów (starsza wersja)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) instrukcje: Tworzenie [przepływów pracy automatu](http://go.microsoft.com/fwlink?LinkID=65016) Stanów [(starsza wersja),](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md) [przy użyciu działania działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65083) [przy użyciu Działanie StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006) [przy użyciu działania StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008) [przy użyciu działania SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082) [przy użyciu działania EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068)