---
title: 'Projektant przepływu pracy — jak: Definiowanie i stosowanie delegowania działania'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 9d0176113b444c2d5b7e4c9f304e35974fdb31e5
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/01/2019
ms.locfileid: "57222886"
---
# <a name="how-to-define-and-consume-activity-delegates-in-the-workflow-designer"></a>Instrukcje: Definiowanie i stosowanie delegowania działania w Projektancie przepływu pracy

.NET framework 4.5 zawiera Projektant out-of-box <xref:System.Activities.Statements.InvokeDelegate> działania. Projektant można przypisać delegatów do działania, który pochodzi od <xref:System.Activities.ActivityDelegate>, takich jak <xref:System.Activities.ActivityAction> lub <xref:System.Activities.ActivityFunc%601>.

## <a name="define-an-activity-delegate"></a>Zdefiniowanie pełnomocnika działania

1. W programie Visual Studio, wybierz **pliku** > **New** > **projektu**.

2. W **nowy projekt** okno dialogowe, wybierz opcję **przepływu pracy** kategorii po lewej stronie, a następnie wybierz pozycję **Aplikacja konsoli przepływu pracy** szablonu projektu. Nazwij projekt (w razie potrzeby), a następnie kliknij przycisk **Ok**.

   > [!NOTE]
   > Jeśli nie widzisz **przepływu pracy** kategorii, wcześniejszej instalacji **Windows Workflow Foundation** składnika programu Visual Studio. Aby uzyskać szczegółowe instrukcje, zobacz [Instalowanie programu Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

3. Kliknij prawym przyciskiem myszy nad projektem w **Eksploratora rozwiązań** i wybierz **Dodaj** > **nowy element**. Wybierz **przepływu pracy** kategorii, a następnie wybierz **działania** szablon elementu. Nazwa nowego działania **MyForEach.xaml** , a następnie wybierz **OK**.

   Działanie zostanie otwarty w Projektancie przepływu pracy.

4. W Projektancie przepływu pracy kliknij **argumenty** kartę.

5. Kliknij przycisk **utworzenia argumentu**. Nazwij nowy argument **elementów**.

6. W **typ argumentu** kolumny wybierz **tablica [T]**.

7. W przeglądarce typu wybierz **obiektu** , a następnie wybierz **OK**.

8. Kliknij przycisk **Utwórz Argument** ponownie. Nazwij nowy argument **treści**. W **kierunek** kolumny jako argumentu nowy, wybierz opcję **właściwość**.

9. W kolumnie Typ argumentu wybierz **vyhledat typy**

10. W przeglądarce typu wprowadź **elementu ActivityAction** w **nazwy typu** pola. Wybierz **elementu ActivityAction\<T >** w widoku drzewa. Wybierz **obiektu** na liście rozwijanej, który wygląda jak przypisać typu **elementu ActivityAction\<obiektu >** do argumentu.

11. Przeciągnij <xref:System.Activities.Statements.While> działanie z **przepływ sterowania** sekcji przybornika do powierzchni projektanta.

12. Wybierz <xref:System.Activities.Statements.While> działania, a następnie wybierz **zmienne** kartę.

13. Wybierz **utworzyć zmienną**. Nadaj nazwę nowej zmiennej **indeksu**.

14. W **typ zmiennej** kolumny wybierz **Int32**. Pozostaw **zakres** jako **podczas**i **domyślne** puste kolumny.

15. Ustaw **warunek** właściwość <xref:System.Activities.Statements.While> działanie **indeks < Items.Length;**.

16. Przeciągnij <xref:System.Activities.Statements.InvokeDelegate> działanie z **podstawowych** sekcji przybornika, aby **treści** z <xref:System.Activities.Statements.While> działania.

17. Wybierz **treści** listy rozwijanej delegata.

18. W **właściwości** siatkę <xref:System.Activities.Statements.InvokeDelegate> działania, kliknij przycisk **...**  znajdujący się w **argumenty delegata** właściwości.

19. W **wartość** kolumny argument o nazwie **Argument**, wprowadź **elementów [Index]**. Kliknij przycisk **Ok** zamknąć **DelegateArguments** okna dialogowego.

20. Przeciągnij <xref:System.Activities.Statements.Assign> działania na linii poziomej poniżej <xref:System.Activities.Statements.InvokeDelegate> działania. <xref:System.Activities.Statements.Assign> Tworzenia działania i <xref:System.Activities.Statements.Sequence> działania jest tworzona automatycznie zawiera dwa działania w **treści** części **MyForEach** działania. Sekwencja jest konieczne, ponieważ **treści** sekcji może zawierać tylko jedno działanie. Automatyczne utworzenie nowego <xref:System.Activities.Statements.Sequence> działania to nowa funkcja programu .NET Framework 4.5.

21. Ustaw **do** właściwość <xref:System.Activities.Statements.Assign> działanie **indeksu**. Ustaw **wartość** właściwość **przypisać** działanie **indeksu + 1**.

    Niestandardowy **MyForEach** działania wywołuje dowolne działanie, jeden raz dla każdej wartości przekazywane do niego za pośrednictwem **elementów** kolekcji przy użyciu wartości w kolekcji jako dane wejściowe dla działania.

## <a name="use-the-custom-activity-in-a-workflow"></a>Używanie niestandardowych działań w przepływie pracy

1.  Skompiluj projekt, naciskając klawisz **Ctrl**+**Shift**+**B**.

2.  W **Eksploratora rozwiązań**, otwórz **Workflow1.xaml** w projektancie.

3.  Przeciągnij **MyForEach** działania z przybornika do powierzchni projektanta. Działanie znajduje się w sekcji przybornika z taką samą nazwę jak projektu.

4.  Ustaw **elementów** właściwość **MyForEach** działanie **nowy obiekt [] {1, "abc"}**.

5.  Przeciągnij <xref:System.Activities.Statements.WriteLine> działanie z **podstawowych** sekcji przybornika, aby **delegata: treść** części **MyForEach** działania.

6.  Ustaw **tekstu** właściwość <xref:System.Activities.Statements.WriteLine> działanie **Argument.ToString()**.

Gdy przepływ pracy ma miejsce, w konsoli wyświetlone zostaną następujące dane wyjściowe:

**1**
**abc**