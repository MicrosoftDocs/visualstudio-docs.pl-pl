---
title: 'Projektant przepływu pracy: Definiowanie delegatów działań i korzystanie z nich'
description: Dowiedz się, jak .NET Framework 4,5 zawiera projektanta poza ramką dla działania InvokeDelegate, którego można użyć do definiowania delegatów działań i korzystania z nich.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: c59c828f380e47a06f8feb7b72788e76ad7ee08f
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94437921"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Instrukcje: Definiowanie i stosowanie delegowania działania w Projektancie przepływu pracy

.NET Framework 4,5 zawiera projektanta poza ramką dla <xref:System.Activities.Statements.InvokeDelegate> działania. Ten Projektant może służyć do przypisywania delegatów do działania, które pochodzi od <xref:System.Activities.ActivityDelegate> , takich jak <xref:System.Activities.ActivityAction> lub <xref:System.Activities.ActivityFunc%601> .

## <a name="define-an-activity-delegate"></a>Zdefiniuj delegata działania

1. Utwórz nowy projekt **aplikacji konsoli przepływu pracy** .

   > [!NOTE]
   > Jeśli szablony projektów **przepływu pracy** nie są widoczne, najpierw zainstaluj składnik **Windows Workflow Foundation** programu Visual Studio. Aby uzyskać szczegółowe instrukcje, zobacz [Install Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

3. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj**  >  **nowy element**. Wybierz kategorię **przepływu pracy** , a następnie wybierz szablon elementu **działania** . Nadaj nowemu działaniu wartość **foreach. XAML** , a następnie wybierz przycisk **OK**.

   Działanie zostanie otwarte w Projektancie przepływu pracy.

4. W Projektant przepływu pracy kliknij kartę **argumenty** .

5. Kliknij przycisk **Utwórz argument**. Nazwij nowe **elementy** argumentu.

6. W kolumnie **Typ argumentu** wybierz pozycję **Tablica [T]**.

7. W przeglądarce typu wybierz **obiekt** , a następnie wybierz przycisk **OK**.

8. Kliknij przycisk **Utwórz argument** ponownie. Nazwij nową **treść** argumentu. W kolumnie **kierunek** dla nowego argumentu wybierz pozycję **Właściwość**.

9. W kolumnie Typ argumentu wybierz pozycję **Przeglądaj w poszukiwaniu typów**

10. W przeglądarce typu wpisz **ActivityAction** w polu **Nazwa typu** . W widoku drzewa wybierz pozycję **ActivityAction \<T>** . Wybierz z listy rozwijanej **obiekt** , który zostanie wyświetlony, aby przypisać do argumentu Typ **ActivityAction \<Object>** .

11. Przeciągnij <xref:System.Activities.Statements.While> działanie z sekcji **przepływ sterowania** w przyborniku do powierzchni projektanta.

12. Wybierz <xref:System.Activities.Statements.While> działanie i wybierz kartę **zmienne** .

13. Wybierz pozycję **Utwórz zmienną**. Nazwij nowy **indeks** zmiennych.

14. W kolumnie **Typ zmiennej** wybierz wartość **Int32**. Pozostaw **zakres** **jako nieokreślony** , a kolumna **Domyślna** jest pusta.

15. Ustaw właściwość **Condition** <xref:System.Activities.Statements.While> działania na **indeksowanie < elementów. length;**.

16. Przeciągnij <xref:System.Activities.Statements.InvokeDelegate> działanie z sekcji elementy **pierwotne** w przyborniku do **treści** <xref:System.Activities.Statements.While> działania.

17. Wybierz pozycję **treść** na liście rozwijanej delegata.

18. W siatce **Właściwości** <xref:System.Activities.Statements.InvokeDelegate> działania kliknij przycisk **...** w właściwości **Delegat argumenty** .

19. W kolumnie **wartość** argumentu nazwanego **argumentu** wpisz **elementy [index]**. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **DelegateArguments** .

20. Przeciągnij <xref:System.Activities.Statements.Assign> działanie na linię poziomą poniżej <xref:System.Activities.Statements.InvokeDelegate> działania. To <xref:System.Activities.Statements.Assign> działanie jest tworzone, a <xref:System.Activities.Statements.Sequence> działanie jest tworzone automatycznie, aby zawierało dwa działania w sekcji **Body** działania. **MyForEach** Sekwencja jest wymagana, ponieważ sekcja **treści** może zawierać tylko jedno działanie. Automatyczne tworzenie nowego <xref:System.Activities.Statements.Sequence> działania jest nową funkcją .NET Framework 4,5.

21. Ustaw właściwość **na** dla <xref:System.Activities.Statements.Assign> działania na **indeks**. Ustaw właściwość **wartość** działania **Przypisz** na wartość **index + 1**.

    Niestandardowa czynność " **Sqlforeach** " wywołuje dowolne działanie raz dla każdej wartości przesyłanej do niej za pomocą kolekcji **Items** , z wartościami w kolekcji jako danymi wejściowymi dla działania.

## <a name="use-the-custom-activity-in-a-workflow"></a>Korzystanie z niestandardowego działania w przepływie pracy

1. Skompiluj projekt, naciskając **klawisze CTRL** + **SHIFT** + **B**.

2. W **Eksplorator rozwiązań** Otwórz **Workflow1. XAML** w projektancie.

3. Przeciągnij działanie elementu **foreach** z przybornika do powierzchni projektanta. Działanie znajduje się w sekcji przybornika o tej samej nazwie co projekt.

4. Ustaw właściwość **Items** działania elementu **foreach** na **nowy obiekt [] {1, "ABC"}**.

5. Przeciągnij <xref:System.Activities.Statements.WriteLine> działanie z sekcji elementy **pierwotne** w przyborniku do sekcji **Delegat: Body** działania elementu. **MyForEach**

6. Ustaw właściwość **Text** <xref:System.Activities.Statements.WriteLine> działania na **argument. ToString ()**.

Gdy przepływ pracy jest wykonywany, w konsoli programu zostaną wyświetlone następujące dane wyjściowe:

**1** 
 **ABC**
