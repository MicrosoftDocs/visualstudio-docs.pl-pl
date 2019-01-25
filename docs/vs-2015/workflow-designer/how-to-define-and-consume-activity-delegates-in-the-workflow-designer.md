---
title: 'Instrukcje: Definiowanie i stosowanie delegowania działania w Projektancie przepływu pracy | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
author: steved0x
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 37adb6cf6462887010b1c06c7d5af4a539203b15
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54803601"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Instrukcje: Definiowanie i stosowanie delegowania działania w Projektancie przepływu pracy
[!INCLUDE[net_v45](../includes/net-v45-md.md)] zawiera nowe Projektant out-of-box <xref:System.Activities.Statements.InvokeDelegate> działania. Projektant można przypisać delegatów do działania, który pochodzi od <xref:System.Activities.ActivityDelegate>, takich jak <xref:System.Activities.ActivityAction> lub <xref:System.Activities.ActivityFunc%601>.  
  
### <a name="define-an-activity-delegate"></a>Zdefiniowanie pełnomocnika działania  
  
1. W [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)], wybierz opcję **pliku**, **New**, **projektu**. Wybierz **przepływu pracy** węzła po lewej stronie, a **Aplikacja konsoli przepływu pracy** szablonu po prawej stronie. Nazwij projekt (w razie potrzeby), a następnie kliknij przycisk **Ok**.  
  
2. Kliknij prawym przyciskiem myszy nad projektem w **Eksploratora rozwiązań** i wybierz **Dodaj**, **nowy element...** . Wybierz **przepływu pracy** węzła po lewej stronie, a **działania** szablonu po prawej stronie. Nazwa nowego działania **MyForEach.xaml** i kliknij przycisk **Ok**. Działanie zostanie otwarty w Projektancie przepływu pracy.  
  
3. W Projektancie przepływu pracy kliknij **argumenty** kartę.  
  
4. Kliknij przycisk **utworzenia argumentu**. Nazwij nowy argument **elementów**.  
  
5. W **typ argumentu** kolumny wybierz **tablica [T]**.  
  
6. W przeglądarce typu wybierz **obiektu**. Kliknij przycisk **Ok**.  
  
7. Kliknij przycisk **Utwórz Argument** ponownie. Nazwij nowy argument **treści**. W **kierunek** kolumny jako argumentu nowy, wybierz opcję **właściwość**.  
  
8. W kolumnie Typ argumentu wybierz **vyhledat typy...**  
  
9. W przeglądarce typu wprowadź **elementu ActivityAction** w **nazwy typu** pola. Wybierz **elementu ActivityAction\<T >** w widoku drzewa. Wybierz **obiektu** na liście rozwijanej, który wygląda jak przypisać typu **elementu ActivityAction\<obiektu >** do argumentu.  
  
10. Przeciągnij <xref:System.Activities.Statements.While> działanie z **przepływ sterowania** sekcji przybornika do powierzchni projektanta.  
  
11. Wybierz <xref:System.Activities.Statements.While> działania, a następnie wybierz **zmienne** kartę.  
  
12. Wybierz **utworzyć zmienną**. Nadaj nazwę nowej zmiennej **indeksu**.  
  
13. W **typ zmiennej** kolumny wybierz **Int32**. Pozostaw **zakres** jako **podczas**i **domyślne** puste kolumny.  
  
14. Ustaw **warunek** właściwość <xref:System.Activities.Statements.While> działanie **indeks < Items.Length;**.  
  
15. Przeciągnij <xref:System.Activities.Statements.InvokeDelegate> działanie z **podstawowych** sekcji przybornika, aby **treści** z <xref:System.Activities.Statements.While> działania.  
  
16. Wybierz **treści** listy rozwijanej delegata.  
  
17. W **właściwości** siatkę <xref:System.Activities.Statements.InvokeDelegate> działania, kliknij przycisk **...** znajdujący się w **argumenty delegata** właściwości.  
  
18. W **wartość** kolumny argument o nazwie **Argument**, wprowadź **elementów [Index]**. Kliknij przycisk **Ok** zamknąć **DelegateArguments** okna dialogowego.  
  
19. Przeciągnij <xref:System.Activities.Statements.Assign> działania na linii poziomej poniżej <xref:System.Activities.Statements.InvokeDelegate> działania. <xref:System.Activities.Statements.Assign> Działania zostanie utworzony, a <xref:System.Activities.Statements.Sequence> działania zostaną utworzone automatycznie zawiera dwa działania w **treści** części **MyForEach** działania. Sekwencja jest konieczne, ponieważ **treści** sekcji może zawierać tylko jedno działanie. Automatyczne utworzenie nowego <xref:System.Activities.Statements.Sequence> działanie jest to nowa funkcja usługi [!INCLUDE[net_v45](../includes/net-v45-md.md)].  
  
20. Ustaw **do** właściwość <xref:System.Activities.Statements.Assign> działanie **indeksu**. Ustaw **wartość** właściwość **przypisać** działanie **indeksu + 1**.  
  
    Niestandardowy **MyForEach** działania wywoła teraz dowolne działanie, jeden raz dla każdej wartości przekazywane do niego za pośrednictwem **elementów** kolekcji przy użyciu wartości w kolekcji jako dane wejściowe dla działania.  
  
### <a name="use-the-custom-activity-in-a-workflow"></a>Używanie niestandardowych działań w przepływie pracy  
  
1. Skompiluj projekt, naciskając klawisz **Ctrl + Shift + B**.  
  
2. W **Eksploratora rozwiązań**, otwórz **Workflow1.xaml** w projektancie.  
  
3. Przeciągnij **MyForEach** działania z przybornika do powierzchni projektanta. Działanie pojawią się w sekcji przybornika z taką samą nazwę jak projektu.  
  
4. Ustaw **elementów** właściwość **MyForEach** działanie **nowy obiekt [] {1, "abc"}**.  
  
5. Przeciągnij <xref:System.Activities.Statements.WriteLine> działanie z **podstawowych** sekcji przybornika, aby **delegata: treść** części **MyForEach** działania.  
  
6. Ustaw **tekstu** właściwość <xref:System.Activities.Statements.WriteLine> działanie **Argument.ToString()**.  
  
   Podczas wykonywania przepływu pracy, konsolę będzie następujący:  
  
   **1**   
   **abc**