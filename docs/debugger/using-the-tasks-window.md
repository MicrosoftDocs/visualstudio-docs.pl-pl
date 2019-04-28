---
title: Korzystanie z okna zadań | Dokumentacja firmy Microsoft
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b32dc6372a6ce4983e9bd11e05a4a662d0ad44ba
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62901608"
---
# <a name="using-the-tasks-window-c-visual-basic-c"></a>Korzystanie z okna zadań (C#, Visual Basic, C++)

**Zadania** przypomina okna **wątków** okna, z wyjątkiem, że przedstawia informacje na temat <xref:System.Threading.Tasks.Task?displayProperty=fullName>, [task_handle](/cpp/parallel/concrt/reference/task-group-class), lub [WinJS.Promise ](/previous-versions/windows/apps/br211867(v=win.10)) obiekty zamiast każdego wątku. Takie jak wątki zadania reprezentują operacje asynchroniczne, które można uruchomić jednocześnie; Jednak wiele zadań może działać na tym samym wątku.

W kodzie zarządzanym można używać **zadania** okna podczas pracy z <xref:System.Threading.Tasks.Task?displayProperty=fullName> obiektów lub za pomocą **await** i **async** słowa kluczowe (**Await** i **Async** w języka Visual Basic). Aby uzyskać więcej informacji o zadaniach w kodzie zarządzanym, zobacz [programowania równoległego](/dotnet/standard/parallel-programming/index).

W kodzie natywnym można użyć **zadania** okna podczas pracy z [grupy zadań](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [równoległe algorytmy](/cpp/parallel/concrt/parallel-algorithms), [agentów asynchronicznych](/cpp/parallel/concrt/asynchronous-agents), i [zadań lekkich](/cpp/parallel/concrt/task-scheduler-concurrency-runtime). Aby uzyskać więcej informacji o zadaniach w kodzie natywnym, zobacz [współbieżność środowiska wykonawczego](/cpp/parallel/concrt/concurrency-runtime).

W języku JavaScript, można użyć okna zadań podczas pracy z promise `.then` kodu. Zobacz [asynchronicznego programowania w języku JavaScript (platformy uwp)](/previous-versions/windows/apps/hh700330(v=win.10)) Aby uzyskać więcej informacji.

Możesz użyć **zadania** okna zawsze wtedy, gdy wkroczenia do debugera. Dostęp na **debugowania** menu, klikając **Windows** , a następnie klikając polecenie **zadania**. Poniższa ilustracja przedstawia **zadania** okna trybu domyślnego.

![Okno zadań](../debugger/media/parallel_tasks_window.png "Parallel_Tasks_Window")

> [!NOTE]
> W kodzie zarządzanym <xref:System.Threading.Tasks.Task> , ma stan [TaskStatus.Created](<xref:System.Threading.Tasks.TaskStatus.Created>), [TaskStatus.WaitingForActivation](<xref:System.Threading.Tasks.TaskStatus.WaitingForActivation>), lub [TaskStatus.WaitingToRun](<xref:System.Threading.Tasks.TaskStatus.WaitingToRun>) może nie być wyświetlane w **zadania** okna, gdy zarządzane wątki są w stanie uśpienia lub sprzężenia.

## <a name="tasks-column-information"></a>Informacje o kolumnach zadania

Kolumny w **zadania** okna są wyświetlane następujące dane.

|Nazwa kolumny|Opis|
|-----------------|-----------------|
|**flagi**|Umożliwia Flagowanie zadania lub i przedstawia zadania, które są oznaczone.|
|**Ikony**|Żółta strzałka wskazuje bieżącego zadania. Bieżące zadanie jest zadaniem najważniejsze dla bieżącego wątku.<br /><br /> Biały strzałek wskazuje zadania istotne, czyli ten, który były aktualne, gdy debuger został wywołany.<br /><br /> Ikona Wstrzymaj wskazuje zadanie, które są zablokowane przez użytkownika. Można Zablokuj i Odblokuj zadania, klikając prawym przyciskiem myszy na liście.|
|**Identyfikator**|Liczba dostarczane przez system dla zadania. W kodzie natywnym jest to adres zadania.|
|**Status**|Bieżący stan (zaplanowane, aktywne, zablokowane, prawdopodobnie zakleszczone, oczekiwanie na lub ukończone) zadania. Zaplanowane zadanie to taki, który nie został jeszcze uruchomiony i dlatego nie ma jeszcze stos wywołań, przypisany wątek lub powiązane informacje.<br /><br /> Aktywne zadanie to taki, który był wykonywany kod przed przerwanie w debugerze.<br /><br /> Oczekiwanie na lub zablokowane zadania to taki, który jest zablokowane, ponieważ trwa oczekiwanie na zdarzenie ma być zasygnalizowany, blokady mogą być wprowadzane lub inne zadanie, aby zakończyć.<br /><br /> Prawdopodobnie zakleszczone zadanie jest zadanie oczekujące, w których wątek jest zakleszczone przez inny wątek.<br /><br /> Umieść kursor nad **stan** komórki dla prawdopodobnie zakleszczone lub Oczekiwanie na zadanie, aby zobaczyć więcej informacji na temat tego bloku. **Ostrzeżenie:**  **Zadania** okna raporty zakleszczenia tylko w przypadku zablokowanych zadanie, które używa podstawowego synchronizacji, który jest obsługiwany przez przejście przez łańcuch oczekiwania (WCT). Na przykład prawdopodobnie zakleszczone <xref:System.Threading.Tasks.Task> obiektu, który używa WCT, debuger raporty **oczekujące, zakleszczone**. Prawdopodobnie zakleszczone zadania, który jest zarządzany przez środowisko uruchomieniowe współbieżności, która nie korzysta z WCT, raportów jest debugera **oczekiwania**. Aby uzyskać więcej informacji na temat WCT zobacz [oczekiwania przechodzenie łańcucha](/windows/desktop/Debug/wait-chain-traversal).|
|**Godzina rozpoczęcia**|Czas, w którym zadanie stały się aktywne.|
|**Czas trwania**|Liczba sekund, które zadania była aktywna.|
|**Czas ukończenia**|Czas, w którym zadanie jest ukończone.|
|**Lokalizacja**|Bieżąca lokalizacja w stosie wywołań zadania. Umieść kursor nad tej komórki, aby zobaczyć cały stos wywołań dla zadania. Zaplanowane zadania nie mają wartości w tej kolumnie.|
|**Zadanie**|Metoda początkowa i argumenty, które zostały przekazane do zadania, gdy został on utworzony.|
|**AsyncState**|Dla kodu zarządzanego, stan zadania. Domyślnie ta kolumna jest ukryta. Aby wyświetlić tę kolumnę, otwórz menu kontekstowe dla jednego z nagłówków kolumn. Wybierz **kolumn**, **AsyncState**.|
|**Nadrzędny**|Identyfikator zadania, które utworzył to zadanie. Jeśli to pole jest puste, zadania jest Brak elementu nadrzędnego. Dotyczy tylko programów zarządzanych.|
|**Wątek przypisania**|Identyfikator i nazwa wątku, na którym działa zadanie.|
|**AppDomain**|Dla kodu zarządzanego, domeny aplikacji, w którym zadanie jest wykonywane.|
|**task_group**|Dla kodu natywnego adresu [task_group](/cpp/parallel/concrt/reference/task-group-class) obiekt, który zaplanowane zadanie. Dla agentów asynchronicznych i zadań lekkich ta kolumna jest równa 0.|
|**Proces**|Identyfikator procesu, który zadanie jest uruchomione.|

 Kliknij prawym przyciskiem myszy nagłówek kolumny, a następnie wybrać kolumny, które chcesz, możesz dodać kolumny do widoku. (Usunąć kolumny, usuwając zaznaczenie opcji). Można również zmienić kolejność kolumn, przeciągając je w lewo lub w prawo. Menu skrótów w kolumnie jest wyświetlany na poniższej ilustracji.

 ![Menu Widok skrótów w oknie zadania](../debugger/media/parallel_tasks_contextmenu.png "Parallel_Tasks_ContextMenu")

## <a name="sorting-tasks"></a>Sortowanie zadania
 Aby posortować zadania według kryteriów kolumny, kliknij nagłówek kolumny. Na przykład klikając **identyfikator** nagłówek kolumny można posortować zadania według Identyfikatora zadania: 1,2,3,4,5 i tak dalej. Aby odwrócić porządek sortowania, kliknij nagłówek kolumny ponownie. Według bieżącej kolumny i sortowania kolejności sortowania jest wskazywany przez strzałkę w kolumnie.

## <a name="grouping-tasks"></a>Grupowania zadań
 Można grupować zadania oparte na dowolną kolumnę w widoku listy. Na przykład, klikając prawym przyciskiem myszy **stan** nagłówek kolumny, a następnie klikając polecenie **Grupuj według** > **[*stan*]**, możesz Grupa wszystkich zadań, które mają ten sam stan. Na przykład można szybko wyświetlić, oczekujące na zadania, dzięki czemu możesz skupić się na dlaczego są blokowane. Można również zwinąć grupy, która nie jest przedmiotem zainteresowania podczas sesji debugowania. W ten sam sposób można grupować według innych kolumn. Grupa może być (NZ) po prostu przez kliknięcie przycisku obok nagłówka grupy. Poniższa ilustracja przedstawia **zadania** okna w trybie zgrupowane.

 ![Tryb zgrupowane w oknie zadania](../debugger/media/parallel_tasks_groupedmode.png "Parallel_Tasks_GroupedMode")

## <a name="parent-child-view"></a>Nadrzędny widok podrzędny
 (W tym widoku jest dostępne tylko dla kodu zarządzanego). Klikając prawym przyciskiem myszy **stan** nagłówek kolumny, a następnie klikając polecenie **Grupuj według** > **nadrzędnego**, do hierarchiczny widok, w którym można zmienić na liście zadań Każde zadanie podrzędne jest podwęźle, które mogą być wyświetlane lub ukryte w jego obiektu nadrzędnego.

## <a name="flagging-tasks"></a>Flagowanie zadania
 Można flagę wątku, na liście zadań, na którym działa zadanie, wybierając zadanie, element, a następnie wybierając **Oflaguj przypisany wątek** z menu kontekstowego lub klikając ikonę flagi w pierwszej kolumnie. Jeśli flaga jest kilka zadań, następnie można sortować na kolumna flagi, aby wyświetlić oflagowanych zadań u góry, dzięki czemu można skupić się właśnie na nich. Można również użyć **stosów równoległych** okna, aby wyświetlić tylko oflagowane zadania. Pozwala to odfiltrować zadania, które nie jest konieczne w celu debugowania. Flagi nie są zachowywane między sesjami debugowania.

## <a name="freezing-and-thawing-tasks"></a>Zawiesza się i odblokowania zadania
 Można zamrozić wątku, na którym działa zadanie, kliknij prawym przyciskiem myszy element listy zadań, a następnie klikając polecenie **Blokuj przypisany wątek**. (Jeśli zadanie jest już zablokowany, polecenie jest **Odblokuj przypisany wątek**.) Po zablokowaniu wątku, który wątek nie zostanie wykonany po przejść przez kod po bieżącym punktu przerwania. **Zablokuj wszystkie wątki, ale ten jeden** polecenie zawiesza się wszystkie wątki z wyjątkiem tego, który wykonuje element listy zadań.

 Poniższa ilustracja przedstawia innymi elementami menu dla każdego zadania.

 ![Menu wątku skrótów w oknie zadania](../debugger/media/parallel_tasks_contextmenu2.png "Parallel_Tasks_ContextMenu2")

## <a name="switching-the-active-task-or-frame"></a>Przełączanie aktywnych zadań lub ramki

**Przełącz do zadania** polecenia sprawia, że bieżące zadanie aktywne zadania. **Przełącz do ramki** polecenia sprawia, że wybrany stosu ramki aktywną ramkę stosu. Kontekst debugera przełącza się do bieżącego zadania lub ramki stosu wybrane.

## <a name="see-also"></a>Zobacz także

- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)
- [Programowanie równoległe](/dotnet/standard/parallel-programming/index)
- [Środowisko uruchomieniowe współbieżności](/cpp/parallel/concrt/concurrency-runtime)
- [Korzystanie z okna stosów równoległych](../debugger/using-the-parallel-stacks-window.md)
- [Przewodnik: Debugowanie aplikacji równoległej](../debugger/walkthrough-debugging-a-parallel-application.md)