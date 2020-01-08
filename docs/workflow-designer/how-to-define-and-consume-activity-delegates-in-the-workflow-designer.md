---
title: 'Projektant przepływu pracy: Definiowanie delegatów działań i korzystanie z nich'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 4309294a2be703b7511355b87c97341fee06d405
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593905"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Instrukcje: Definiowanie delegatów działań i korzystanie z nich w Projektant przepływu pracy

.NET Framework 4,5 zawiera projektanta poza ramką dla działania <xref:System.Activities.Statements.InvokeDelegate>. Ten Projektant może służyć do przypisywania delegatów do działania, które wynikają z <xref:System.Activities.ActivityDelegate>, takich jak <xref:System.Activities.ActivityAction> lub <xref:System.Activities.ActivityFunc%601>.

## <a name="define-an-activity-delegate"></a>Zdefiniuj delegata działania

1. Utwórz nowy projekt **aplikacji konsoli przepływu pracy** .

   > [!NOTE]
   > Jeśli szablony projektów **przepływu pracy** nie są widoczne, najpierw zainstaluj składnik **Windows Workflow Foundation** programu Visual Studio. Aby uzyskać szczegółowe instrukcje, zobacz [Install Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

3. Kliknij prawym przyciskiem myszy projekt w **Eksplorator rozwiązań** a następnie wybierz pozycję **Dodaj** > **nowy element**. Wybierz kategorię **przepływu pracy** , a następnie wybierz szablon elementu **działania** . Nadaj nowemu działaniu wartość **foreach. XAML** , a następnie wybierz przycisk **OK**.

   Działanie zostanie otwarte w Projektancie przepływu pracy.

4. W Projektant przepływu pracy kliknij kartę **argumenty** .

5. Kliknij przycisk **Utwórz argument**. Nazwij nowe **elementy**argumentu.

6. W kolumnie **Typ argumentu** wybierz pozycję **Tablica [T]** .

7. W przeglądarce typu wybierz **obiekt** , a następnie wybierz przycisk **OK**.

8. Kliknij przycisk **Utwórz argument** ponownie. Nazwij nową **treść**argumentu. W kolumnie **kierunek** dla nowego argumentu wybierz pozycję **Właściwość**.

9. W kolumnie Typ argumentu wybierz pozycję **Przeglądaj w poszukiwaniu typów**

10. W przeglądarce typu wpisz **ActivityAction** w polu **Nazwa typu** . Wybierz pozycję **ActivityAction\<t >** w widoku drzewa. Na liście rozwijanej wybierz **obiekt** , który zostanie wyświetlony, aby przypisać do argumentu typ **ActivityAction\<> obiektu** .

11. Przeciągnij działanie <xref:System.Activities.Statements.While> z sekcji **przepływ sterowania** w przyborniku do powierzchni projektanta.

12. Wybierz działanie <xref:System.Activities.Statements.While> i wybierz kartę **zmienne** .

13. Wybierz pozycję **Utwórz zmienną**. Nazwij nowy **indeks**zmiennych.

14. W kolumnie **Typ zmiennej** wybierz wartość **Int32**. Pozostaw **zakres** **jako nieokreślony**, a kolumna **Domyślna** jest pusta.

15. Ustaw właściwość **Condition** działania <xref:System.Activities.Statements.While> na **indeksowanie < elementów. length;** .

16. Przeciągnij działanie <xref:System.Activities.Statements.InvokeDelegate> z sekcji elementy **pierwotne** w przyborniku do **treści** <xref:System.Activities.Statements.While> działania.

17. Wybierz pozycję **treść** na liście rozwijanej delegata.

18. W siatce **Właściwości** działania <xref:System.Activities.Statements.InvokeDelegate> kliknij przycisk **...** w właściwości **Delegat argumenty** .

19. W kolumnie **wartość** argumentu nazwanego **argumentu**wpisz **elementy [index]** . Kliknij przycisk **OK** , aby zamknąć okno dialogowe **DelegateArguments** .

20. Przeciągnij działanie <xref:System.Activities.Statements.Assign> na linię poziomą poniżej działania <xref:System.Activities.Statements.InvokeDelegate>. Zostanie utworzone działanie <xref:System.Activities.Statements.Assign>, a działanie <xref:System.Activities.Statements.Sequence> zostanie automatycznie utworzone w celu uwzględnienia dwóch działań w sekcji **treść** **działania operacji.** Sekwencja jest wymagana, ponieważ sekcja **treści** może zawierać tylko jedno działanie. Automatyczne tworzenie nowego działania <xref:System.Activities.Statements.Sequence> jest nową funkcją .NET Framework 4,5.

21. Ustaw właściwość **na** <xref:System.Activities.Statements.Assign> działanie do **indeksowania**. Ustaw właściwość **wartość** działania **Przypisz** na wartość **index + 1**.

    Niestandardowa czynność " **Sqlforeach** " wywołuje dowolne działanie raz dla każdej wartości przesyłanej do niej za pomocą kolekcji **Items** , z wartościami w kolekcji jako danymi wejściowymi dla działania.

## <a name="use-the-custom-activity-in-a-workflow"></a>Korzystanie z niestandardowego działania w przepływie pracy

1. Skompiluj projekt, naciskając klawisz **Ctrl**+**SHIFT**+**B**.

2. W **Eksplorator rozwiązań**Otwórz **Workflow1. XAML** w projektancie.

3. Przeciągnij działanie elementu **foreach** z przybornika do powierzchni projektanta. Działanie znajduje się w sekcji przybornika o tej samej nazwie co projekt.

4. Ustaw właściwość **Items** działania elementu **foreach** na **nowy obiekt [] {1, "ABC"}** .

5. Przeciągnij działanie <xref:System.Activities.Statements.WriteLine> z sekcji elementy **pierwotne** w przyborniku do sekcji **Delegat: Body** **działania elementu** .

6. Ustaw właściwość **Text** działania <xref:System.Activities.Statements.WriteLine> na **argument. ToString ()** .

Gdy przepływ pracy jest wykonywany, w konsoli programu zostaną wyświetlone następujące dane wyjściowe:

**1**
**abc**
