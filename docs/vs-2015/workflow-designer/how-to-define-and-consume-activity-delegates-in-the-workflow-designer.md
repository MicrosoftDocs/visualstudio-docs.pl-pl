---
title: 'Instrukcje: Definiowanie delegatów działań i korzystanie z nich w Projektant przepływu pracy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 26ba92a2ba7aa6eed471383c875104549e896804
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72603853"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Instrukcje: Definiowanie i stosowanie delegowania działania w Projektancie przepływu pracy
[!INCLUDE[net_v45](../includes/net-v45-md.md)] zawiera nowy projektanta poza ramką dla <xref:System.Activities.Statements.InvokeDelegate> działania. Ten Projektant może służyć do przypisywania delegatów do działania, które pochodzi od <xref:System.Activities.ActivityDelegate> , takich jak <xref:System.Activities.ActivityAction> lub <xref:System.Activities.ActivityFunc%601> .

### <a name="define-an-activity-delegate"></a>Zdefiniuj delegata działania

1. W programie [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] Wybierz kolejno pozycje **plik**, **Nowy**i **projekt**. Wybierz węzeł **przepływ pracy** po lewej stronie i szablon **aplikacji konsoli przepływu pracy** po prawej stronie. Nazwij projekt (jeśli to konieczne), a następnie kliknij przycisk **OK**.

2. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**, **nowy element.**... Wybierz węzeł **przepływ pracy** po lewej stronie i szablon **działania** po prawej stronie. Nadaj nowemu działaniu wartość **foreach. XAML** , a następnie kliknij przycisk **OK**. Działanie zostanie otwarte w Projektancie przepływu pracy.

3. W Projektancie przepływu pracy kliknij kartę **argumenty** .

4. Kliknij przycisk **Utwórz argument**. Nazwij nowe **elementy**argumentu.

5. W kolumnie **Typ argumentu** wybierz pozycję **Tablica [T]**.

6. W przeglądarce typów wybierz pozycję  **obiekt**. Kliknij przycisk **OK**.

7. Kliknij przycisk **Utwórz argument** ponownie. Nazwij nową **treść**argumentu. W kolumnie **kierunek** dla nowego argumentu wybierz pozycję **Właściwość**.

8. W kolumnie Typ argumentu wybierz pozycję **Przeglądaj w poszukiwaniu typów...**

9. W przeglądarce typu wpisz **ActivityAction** w polu **Nazwa typu** . W widoku drzewa wybierz pozycję **ActivityAction \<T> ** . Wybierz z listy rozwijanej **obiekt** , który zostanie wyświetlony, aby przypisać do argumentu Typ **ActivityAction \<Object> ** .

10. Przeciągnij <xref:System.Activities.Statements.While> działanie z sekcji **przepływ sterowania** w przyborniku do powierzchni projektanta.

11. Wybierz <xref:System.Activities.Statements.While> działanie i wybierz kartę **zmienne** .

12. Wybierz pozycję **Utwórz zmienną**. Nazwij nowy **indeks**zmiennych.

13. W kolumnie **Typ zmiennej** wybierz wartość **Int32**. Pozostaw **zakres** **jako nieokreślony**, a kolumna **Domyślna** jest pusta.

14. Ustaw właściwość **Condition** <xref:System.Activities.Statements.While> działania na **indeksowanie < elementów. length;**.

15. Przeciągnij <xref:System.Activities.Statements.InvokeDelegate> działanie z sekcji elementy **pierwotne** w przyborniku do **treści** <xref:System.Activities.Statements.While> działania.

16. Wybierz pozycję **treść** na liście rozwijanej delegata.

17. W siatce **Właściwości** <xref:System.Activities.Statements.InvokeDelegate> działania kliknij przycisk **...** w właściwości **argumenty delegatów** .

18. W kolumnie **wartość** argumentu nazwanego **argumentu**wpisz **elementy [index]**. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **DelegateArguments** .

19. Przeciągnij <xref:System.Activities.Statements.Assign> działanie na linię poziomą poniżej <xref:System.Activities.Statements.InvokeDelegate> działania. <xref:System.Activities.Statements.Assign>Działanie zostanie utworzone, a <xref:System.Activities.Statements.Sequence> działanie zostanie utworzone automatycznie, aby zawierało dwa działania w sekcji **Body** działania. **MyForEach** Sekwencja jest wymagana, ponieważ sekcja **treści** może zawierać tylko jedno działanie. Automatyczne tworzenie nowego <xref:System.Activities.Statements.Sequence> działania jest nową funkcją [!INCLUDE[net_v45](../includes/net-v45-md.md)] .

20. Ustaw właściwość **na** dla <xref:System.Activities.Statements.Assign> działania na **indeks**. Ustaw właściwość **wartość** działania **Przypisz** na wartość **index + 1**.

    Niestandardowa czynność "Activity **foreach** " spowoduje teraz wywołanie dowolnego działania raz dla każdej wartości przekazaną do niej za pomocą kolekcji **Items** , z wartościami w kolekcji jako danymi wejściowymi dla działania.

### <a name="use-the-custom-activity-in-a-workflow"></a>Korzystanie z niestandardowego działania w przepływie pracy

1. Skompiluj projekt, naciskając **klawisze CTRL + SHIFT + B**.

2. W **Eksplorator rozwiązań**Otwórz **Workflow1. XAML** w projektancie.

3. Przeciągnij działanie elementu **foreach** z przybornika do powierzchni projektanta. Działanie będzie w sekcji przybornika o tej samej nazwie co projekt.

4. Ustaw właściwość **Items** działania elementu **foreach** na **nowy obiekt [] {1, "ABC"}**.

5. Przeciągnij <xref:System.Activities.Statements.WriteLine> działanie z sekcji elementy **pierwotne** w przyborniku do sekcji **Delegat: Body** działania elementu. **MyForEach**

6. Ustaw właściwość **Text** <xref:System.Activities.Statements.WriteLine> działania na **argument. ToString ()**.

   Gdy przepływ pracy jest wykonywany, w konsoli programu zostaną wyświetlone następujące elementy:

   **1** 
    **ABC**