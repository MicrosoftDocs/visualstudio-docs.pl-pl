---
title: Za pomocą projektanta przepływu pracy automatu stanu starszych | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 54469f2e255ff9ea726ea1b6c13abcb55c33252d
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63444114"
---
# <a name="using-the-legacy-state-machine-workflow-designer"></a>Używanie starszej wersji Projektanta przepływu pracy automatu stanów
Podczas tworzenia nowego projektu przepływu pracy maszyny stanu w [!INCLUDE[vs2010](../includes/vs2010-md.md)] który jest przeznaczony dla jednej [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] lub [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)], możesz użyć **Aplikacja konsoli przepływu pracy maszyny w stanie** lub  **Stan biblioteki przepływu pracy automatu** szablonu projektu w starszej wersji. Jeśli zostanie wybrana jedna z tych szablonów projektu maszyny stanu, Projektant machine stanu jest przedstawiany jako interfejsu użytkownika projektanta przepływu pracy w starszej wersji. Aby dowiedzieć się, szablony projektów maszyny stanu starszej wersji, zobacz [jak: Tworzenie aplikacji konsoli przepływu pracy automatu stanów (starsza wersja)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md) i [jak: Tworzenie biblioteki przepływu pracy automatu stanów (starsza wersja)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md).  
  
 Przepływ pracy automatu stanów składa się z szeregu stanów. Jeden stan jest oznaczona jako początkowego stanu. Każdy stan mogą otrzymać zestaw zdarzeń. Na podstawie zdarzenia, przejście może przyjąć inny stan. Przepływ pracy automatu stanów może mieć stan końcowy. Po nawiązaniu przejście do stanu końcowego kończy działanie przepływu pracy.  
  
## <a name="state-machine-designer-views"></a>Projektant widoków automatu stanów  
 Projektant maszyny stanu jest dowolny kształt projektanta, co oznacza, że działania mogą być przenoszone między za darmo na powierzchni projektowej. Projektant machine stan ma dwa widoki: *stanu* widoku i *oparte na zdarzeniach* widoku.  
  
 Widok stanu przedstawia stan działania i oparte na zdarzeniach działań, które mogą być zawarte wewnątrz działania elementu stanu. W tym widoku przejścia z jednego stanu do drugiego są reprezentowane przez linie, które rozszerzają działania oparte na zdarzeniach w jednego stanu do innego stanu. Można również utworzyć przejść przez siebie Rysowanie linii. Aby narysować przejścia, wybierz działanie oparte na zdarzeniach, a następnie wybierz jeden z uchwytów na działania i przeciągnij go. Ta akcja rysuje linię. Ten wiersz jest następnie dołączany do stanu docelowego wskazujący przejścia między stanami.  
  
 Aby uzyskać dostęp do zdarzeń opartych na widok, kliknij dwukrotnie działania oparte na zdarzeniach. Projektant, który pojawia się odbywa się podobnie projektanta sekwencyjnego przepływu pracy. W górnej części projektanta paska nawigacyjnego, pokazuje hierarchię działań do działania oparte na zdarzeniach, która jest wyświetlana. Klikając dowolny element w hierarchii wyświetlane, może przejść do widoku stanu. Jeśli użytkownik narysuje przejścia z jednego stanu do drugiego w widoku stanu, a w przypadku wyświetlania zdarzeń opartych na wyświetlanie tego działania, działania stanu zestawu jest dodawane do działania oparte na zdarzeniach. Jeśli zmienisz właściwości działania stanu zestawu, jest to widoczne w widoku stanu.  
  
## <a name="state-machine-workflow-activities"></a>Działania przepływu pracy automatu stanów  
 W poniższej tabeli opisano kluczowymi działaniami, które są używane w Projektancie przepływu pracy stanu komputera.  
  
|Nazwa przybornika|Działanie|Opis|  
|------------------|--------------|-----------------|  
|**State**|[Działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Reprezentuje stan w automacie stanów; może zawierać dodatkowe **działanie StateActivity** działań. Aby uzyskać więcej informacji, zobacz [przy użyciu działania działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65083).|  
|**SetState**|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Określa przejścia do nowego stanu. Aby uzyskać więcej informacji, zobacz [przy użyciu działania SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082).|  
|**Działanie StateInitialization**|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|Wykonuje, gdy stan jest wprowadzana; może zawierać innych działań. Aby uzyskać więcej informacji, zobacz [przy użyciu działania działanie StateInitialization](http://go.microsoft.com/fwlink?LinkID=65006).|  
|**Działanie StateFinalization**|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|Wykonuje zawarte działania podczas opuszczania [działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) działania. Aby uzyskać więcej informacji, zobacz [przy użyciu działania StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008).|  
|**EventDriven**|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Używane dla stanów, które polegają na wystąpienie zewnętrznego zdarzenia, aby rozpocząć wykonywanie. **EventDrivenActivity** czynność musi być w działaniu, który implementuje [IEventActivity](http://go.microsoft.com/fwlink?LinkID=65032) interfejs jako pierwsze działanie podrzędne. Aby uzyskać więcej informacji, zobacz [przy użyciu działania EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068).|  
  
 Głównym składnikiem przepływ pracy automatu stanów jest [działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) działania. Zdarzenia są przechwytywane w różnych punktach przepływu pracy stanu komputera, różne stany są wprowadzane do obsługi zadań, które są skojarzone ze zdarzeniami. W okresie istnienia przepływu pracy przepływ pracy może wystawić, a następnie wprowadź kilka różnych stanów. Te stany łączyć się ze sobą przy użyciu [SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041) działania.  
  
 Przeciągnięcie nowego **działanie StateActivity** na powierzchnię projektu przepływu pracy, można dodać [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029), [StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044), [ StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043), lub dodatkowe **działanie StateActivity** działań jako działania podrzędne.  
  
> [!CAUTION]
> Korzystając z projektanta przepływu pracy stanu komputera do tworzenia przepływów pracy, należy monitorować strukturę przepływu pracy są projektowanie z uwzględnieniem **konspekt dokumentu** okno widoku. Wyświetlanie struktury przepływ pracy automatu stanów w **konspekt dokumentu** widoku okna odzwierciedla logiczne układ działania w pliku znaczników przepływu pracy. Fizycznego układu działań przepływu pracy w jakiej występują na powierzchni projektowej może nie dublowanie logiczne układ działania w pliku znaczników przepływu pracy.  
>   
> Aby otworzyć **konspekt dokumentu** okna na **widoku** menu, wskaż **Windows inne**, a następnie wybierz pozycję **konspekt dokumentu**.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Tworzenie aplikacji konsoli przepływu pracy automatu stanów (starsza wersja)](../workflow-designer/how-to-create-state-machine-workflow-console-applications-legacy.md)   
 [Instrukcje: Tworzenie biblioteki przepływu pracy automatu stanów (starsza wersja)](../workflow-designer/how-to-create-a-state-machine-workflow-library-legacy.md)   
 [Przepływy pracy automatu stanów](http://go.microsoft.com/fwlink?LinkID=65016)   
 [Przy użyciu działania działanie StateActivity](http://go.microsoft.com/fwlink?LinkID=65083)   
 [Przy użyciu działania StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65006)   
 [Przy użyciu działania StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65008)   
 [Przy użyciu działania SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65082)   
 [Przy użyciu działania EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65068)