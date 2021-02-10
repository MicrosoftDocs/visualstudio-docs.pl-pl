---
title: Korzystanie z okna zadania | Microsoft Docs
description: Zadania są operacjami asynchronicznymi, które mogą być uruchamiane współbieżnie. Na tym samym wątku można uruchamiać wiele zadań. Użyj zadań do wyświetlania informacji o obiekcie Task i WinJS. Promise.
ms.custom: SEO-VS-2020
ms.date: 03/18/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.paralleltasks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fcae019e8854ecee9cdc553eedd3e9d2d0f28a63
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948586"
---
# <a name="using-the-tasks-window-c-visual-basic-c"></a>Korzystanie z okna zadania (C#, Visual Basic, C++)

Okno **zadania** przypomina okno **wątków** , z tą różnicą, że wyświetla informacje o <xref:System.Threading.Tasks.Task?displayProperty=fullName> obiektach, [task_handle](/cpp/parallel/concrt/reference/task-group-class)lub [WinJS. Promise](/previous-versions/windows/apps/br211867(v=win.10)) obiektów zamiast poszczególnych wątków. Podobnie jak wątki, zadania reprezentują operacje asynchroniczne, które mogą być uruchamiane współbieżnie; można jednak uruchomić wiele zadań w tym samym wątku.

W kodzie zarządzanym można użyć okna **zadania** podczas pracy z <xref:System.Threading.Tasks.Task?displayProperty=fullName> obiektami lub z słowami kluczowymi **await** i **Async** (**await** i **Async** w języku VisualBasic). Aby uzyskać więcej informacji o zadaniach w kodzie zarządzanym, zobacz  [programowanie równoległe](/dotnet/standard/parallel-programming/index).

W kodzie natywnym można użyć okna **zadania** podczas pracy z [grupami zadań](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [algorytmami równoległymi](/cpp/parallel/concrt/parallel-algorithms), [agentami asynchronicznymi](/cpp/parallel/concrt/asynchronous-agents)i [zadaniami uproszczonymi](/cpp/parallel/concrt/task-scheduler-concurrency-runtime). Aby uzyskać więcej informacji o zadaniach w kodzie natywnym, zobacz [środowisko uruchomieniowe współbieżności](/cpp/parallel/concrt/concurrency-runtime).

W języku JavaScript można użyć okna zadania podczas pracy z kodem Promise `.then` . Aby uzyskać więcej informacji, zobacz [programowanie asynchroniczne w języku JavaScript (aplikacje platformy UWP)](/previous-versions/windows/apps/hh700330(v=win.10)) .

Okna **zadania** można użyć po każdym przerwaniu w debugerze. Możesz uzyskać do niego dostęp w menu **Debuguj** , klikając pozycję **Windows** , a następnie klikając pozycję **zadania**. Poniższa ilustracja przedstawia okno **zadania** w jego domyślnym trybie.

![Okno zadań](../debugger/media/parallel_tasks_window.png "Parallel_Tasks_Window")

> [!NOTE]
> W kodzie zarządzanym, <xref:System.Threading.Tasks.Task> który ma stan [TaskStatus. Created](<xref:System.Threading.Tasks.TaskStatus.Created>), [TaskStatus. WaitingForActivation](<xref:System.Threading.Tasks.TaskStatus.WaitingForActivation>)lub [TaskStatus. WaitingToRun](<xref:System.Threading.Tasks.TaskStatus.WaitingToRun>) może nie być wyświetlany w oknie **zadań** , gdy zarządzane wątki są w stanie uśpienia lub przyłączania.

## <a name="tasks-column-information"></a>Informacje o kolumnie zadania

W kolumnach okna **zadania** są wyświetlane poniższe informacje.

|Nazwa kolumny|Opis|
|-----------------|-----------------|
|**Znaczników**|Pokazuje, które zadania są oflagowane i umożliwiają Flagowanie lub usuwanie flagi zadania.|
|**Ikony**|Żółta strzałka wskazuje bieżące zadanie. Bieżące zadanie to zadanie najwyższego poziomu w bieżącym wątku.<br /><br /> Biała Strzałka wskazuje zadanie przerywania, czyli bieżące, gdy debuger został wywołany.<br /><br /> Ikona Wstrzymaj oznacza zadanie, które zostało zamrożone przez użytkownika. Zadanie można zablokować i odblokować, klikając je prawym przyciskiem myszy na liście.|
|**ID (Identyfikator)**|Numer dostarczony przez system dla zadania. W kodzie natywnym jest to adres zadania.|
|**Stan**|Bieżący stan (zaplanowany, aktywny, zablokowany, zakleszczony, oczekujące lub ukończone) zadania. Zaplanowane zadanie to takie, które nie zostało jeszcze uruchomione i dlatego nie zawiera jeszcze stosu wywołań, przypisanego wątku ani powiązanych informacji.<br /><br /> Aktywne zadanie to takie, które wykonywało kod przed przerwaniem w debugerze.<br /><br /> Zadanie oczekujące lub zablokowane to takie, które jest blokowane, ponieważ oczekuje na zdarzenie, które ma być sygnalizowane, blokadę do zwolnienia lub inne zadanie do zakończenia.<br /><br /> Zazakleszczony zadanie to oczekujące zadanie, którego wątek jest zakleszczony przy użyciu innego wątku.<br /><br /> Umieść kursor nad komórką **stanu** dla zazakleszczenia lub oczekującego zadania, aby wyświetlić więcej informacji na temat bloku. **Ostrzeżenie:**  Okno **zadania** raportuje zakleszczenie tylko dla zablokowanego zadania, które używa elementu podstawowego synchronizacji, który jest obsługiwany przez przechodzenie łańcucha oczekiwania (WCT). Na przykład w przypadku zakleszczenia <xref:System.Threading.Tasks.Task> obiektu, który używa WCT, program debugowania raportuje **oczekiwanie na zakleszczenie**. W przypadku zadania, które jest zarządzane przez środowisko uruchomieniowe współbieżności, które nie korzysta z WCT, debuger zgłasza **oczekiwanie**. Aby uzyskać więcej informacji na temat WCT, zobacz [przechodzenie łańcucha oczekiwania](/windows/desktop/Debug/wait-chain-traversal).|
|**Godzina rozpoczęcia**|Godzina, o której zadanie stało aktywne.|
|**Czas trwania**|Liczba sekund, przez jaką zadanie jest aktywne.|
|**Czas ukończenia**|Godzina ukończenia zadania.|
|**Lokalizacja**|Bieżąca lokalizacja w stosie wywołań zadania. Umieść kursor nad tą komórką, aby zobaczyć cały stos wywołań dla zadania. Zaplanowane zadania nie mają wartości w tej kolumnie.|
|**Zadanie**|Metoda początkowa i wszystkie argumenty, które zostały przekazane do zadania podczas jego tworzenia.|
|**AsyncState**|Dla kodu zarządzanego zadanie ma stan. Domyślnie ta kolumna jest ukryta. Aby wyświetlić tę kolumnę, otwórz menu kontekstowe dla jednego z nagłówków kolumn. Wybierz **kolumny**, **AsyncState**.|
|**Nadrzędny**|Identyfikator zadania, które spowodowało utworzenie tego zadania. Jeśli to pole jest puste, zadanie nie ma elementu nadrzędnego. Ma to zastosowanie tylko w przypadku programów zarządzanych.|
|**Przypisanie wątku**|Identyfikator i nazwa wątku, w którym jest uruchomione zadanie.|
|**Wywołując**|Dla kodu zarządzanego, domena aplikacji, w której wykonywane jest zadanie.|
|**task_group**|Dla kodu natywnego, adres [task_group](/cpp/parallel/concrt/reference/task-group-class) obiektu, który zaplanował zadanie. W przypadku agentów asynchronicznych i uproszczonych zadań ta kolumna jest ustawiona na 0.|
|**Proces**|Identyfikator procesu, w którym uruchomiono zadanie.|

 Kolumny do widoku można dodać, klikając prawym przyciskiem myszy nagłówek kolumny, a następnie wybierając odpowiednie kolumny. (Usuń kolumny przez wyczyszczenie opcji). Możesz również zmienić kolejność kolumn, przeciągając je w lewo lub w prawo. Menu skrótów kolumny jest pokazane na poniższej ilustracji.

 ![Menu Widok skrótu w oknie zadania](../debugger/media/parallel_tasks_contextmenu.png "Parallel_Tasks_ContextMenu")

## <a name="sorting-tasks"></a>Sortowanie zadań
 Aby posortować zadania według kryteriów kolumn, kliknij nagłówek kolumny. Na przykład klikając nagłówek kolumny **Identyfikator** , można sortować zadania według identyfikatora zadania: 1, 2, 3, 4, 5 itd. Aby odwrócić porządek sortowania, ponownie kliknij nagłówek kolumny. Bieżąca kolumna sortowania i porządek sortowania jest wskazywany przez strzałkę w kolumnie.

## <a name="grouping-tasks"></a>Grupowanie zadań
 Zadania można grupować na podstawie dowolnej kolumny w widoku listy. Na przykład klikając prawym przyciskiem myszy nagłówek kolumny **stan** , a następnie klikając pozycję **Grupuj według**  >  **[*stan*]**, można zgrupować wszystkie zadania, które mają ten sam stan. Można na przykład szybko zobaczyć oczekujące zadania, aby można było skupić się na tym, dlaczego są one zablokowane. Możesz również zwinąć grupę, która nie jest interesująca podczas sesji debugowania. W ten sam sposób można grupować według innych kolumn. Grupa może być (cofnięta) oflagowana po kliknięciu przycisku obok nagłówka grupy. Poniższa ilustracja przedstawia okno **zadania** w trybie grupowania.

 ![Tryb grupowania w oknie zadań](../debugger/media/parallel_tasks_groupedmode.png "Parallel_Tasks_GroupedMode")

## <a name="parent-child-view"></a>Nadrzędny widok podrzędny
 (Ten widok jest dostępny tylko dla kodu zarządzanego). Klikając prawym przyciskiem myszy nagłówek kolumny **stan** , a następnie klikając pozycję **Grupuj według** elementów  >  **nadrzędnych**, można zmienić listę zadań na hierarchiczny widok, w którym każde zadanie podrzędne jest węzłem podrzędnym, który może być wyświetlany lub ukryty w obszarze nadrzędnym.

## <a name="flagging-tasks"></a>Oflagowanie zadań
 Można oflagować wątek, w którym uruchamiane jest zadanie, zaznaczając element listy zadań, a następnie wybierając opcję **Oflaguj przypisany wątek** z menu kontekstowego lub klikając ikonę flagi w pierwszej kolumnie. Jeśli oflagujesz kilka zadań, Możesz sortować według kolumny flag, aby przenieść wszystkie oflagowane zadania do góry, aby można było skupić się na nich. Można również użyć okna **stosów równoległych** do wyświetlania tylko oflagowanych zadań. Pozwala to na odfiltrowanie zadań, które nie są interesujące do debugowania. Flagi nie są utrwalane między sesjami debugowania.

## <a name="freezing-and-thawing-tasks"></a>Zamrażanie i odblokowywanie zadań
 Można zablokować wątek, w którym uruchomiono zadanie, klikając prawym przyciskiem myszy element listy zadań, a następnie klikając polecenie **Zablokuj przypisany wątek**. (Jeśli zadanie jest już zamrożone, polecenie jest **odblokowanie przypisanego wątku**). Po zablokowaniu wątku ten wątek nie zostanie wykonany po przejściu przez kod po bieżącym punkcie przerwania. **Zablokuj wszystkie wątki, ale to jedno** polecenie blokuje wszystkie wątki z wyjątkiem tego, który wykonuje element listy zadań.

 Na poniższej ilustracji przedstawiono pozostałe elementy menu dla każdego zadania.

 ![Menu wątku skrótów w oknie zadania](../debugger/media/parallel_tasks_contextmenu2.png "Parallel_Tasks_ContextMenu2")

## <a name="switching-the-active-task-or-frame"></a>Przełączanie aktywnego zadania lub ramki

Polecenie **Przełącz do zadania** powoduje, że bieżące zadanie jest aktywne. Polecenie **Przełącz do ramki** powoduje, że wybrana Ramka stosu ma aktywną ramkę stosu. Kontekst debugera przechodzi do bieżącego zadania lub wybranej ramki stosu.

## <a name="see-also"></a>Zobacz też

- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)
- [Programowanie równoległe](/dotnet/standard/parallel-programming/index)
- [Współbieżność środowiska wykonawczego](/cpp/parallel/concrt/concurrency-runtime)
- [Korzystanie z okna stosów równoległych](../debugger/using-the-parallel-stacks-window.md)
- [Przewodnik: debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md)