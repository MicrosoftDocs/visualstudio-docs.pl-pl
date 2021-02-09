---
title: Wyświetl wątki w oknie stosów równoległych | Microsoft Docs
description: Używaj stosów równoległych, aby ułatwić debugowanie aplikacji wielowątkowych. Można wyświetlić informacje o stosie dla wszystkich wątków i informacje stosu wywołań z centrum zadań.
ms.custom: SEO-VS-2020
ms.date: 11/20/2018
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelstacks
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: f50efb78-5206-4803-bb42-426ef8133f2f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7b92f4e2faf2043c26c7119b6f9754edd3bdc990
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884393"
---
# <a name="view-threads-and-tasks-in-the-parallel-stacks-window-c-visual-basic-c"></a>Wyświetl wątki i zadania w oknie stosów równoległych (C#, Visual Basic, C++)

Okno **stosów równoległych** jest przydatne do debugowania aplikacji wielowątkowych. Zawiera kilka widoków:

- [Widok wątków](#threads-view) przedstawia informacje stosu wywołań dla wszystkich wątków w aplikacji. Między wątkami i ramkami stosu można przechodzić do tych wątków.

- [Widok zadań](#tasks-view) przedstawia informacje stosu wywołań wyśrodkowanych przez zadania.
  - W obszarze kod zarządzany widok **zadania** zawiera stosy wywołań <xref:System.Threading.Tasks.Task?displayProperty=fullName> obiektów.
  - W kodzie natywnym widok **zadań** pokazuje stosy wywołań [grup zadań](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [algorytmów równoległych](/cpp/parallel/concrt/parallel-algorithms), [agentów asynchronicznych](/cpp/parallel/concrt/asynchronous-agents)i prostych [zadań](/cpp/parallel/concrt/task-scheduler-concurrency-runtime).

- [Widok metody](#method-view) przestawia stos wywołań na wybranej metodzie.

## <a name="use-the-parallel-stacks-window"></a>Korzystanie z okna stosów równoległych

Aby otworzyć okno **stosów równoległych** , musisz być w sesji debugowania. Wybierz kolejno opcje **Debuguj**  >    >  **równoległe stosy** systemu Windows.

### <a name="toolbar-controls"></a>Kontrolki paska narzędzi

Okno **stosów równoległych** ma następujące kontrolki paska narzędzi:

![Pasek narzędzi w oknie stosów równoległych](../debugger/media/parallel_stackstoolbar.png "Pasek narzędzi stosów równoległych")

|Ikona|Kontrola|Opis|
|-|-|-|
|![Pole kombi wątki/zadania](media/parallel_toolbar1.png "Pole kombi wątki/zadania")|**Wątki** / Pole kombi **zadań**|Przełącza widok między stosami wywołań wątków i wywołań stosów zadań. Aby uzyskać więcej informacji, zobacz widok [zadań](#tasks-view) i [wątki](#threads-view).|
|![Pokaż tylko oflagowaną ikonę](media/parallel_toolbar2.png "Pokaż tylko oflagowaną ikonę")|Pokaż tylko Oflagowane|Pokazuje stosy wywołań tylko dla wątków, które są oflagowane w innych oknach debugera, takich jak okno **wątków GPU** i okno **czujki równoległej** .|
|![Ikona przełączania widoku metody](media/parallel_toolbar3.png "Ikona przełączania widoku metody")|Przełącz **Widok metody**|Przełącza między widokami stosu wywołań i **widokiem metody**. Aby uzyskać więcej informacji, zobacz [Widok metody](#method-view).|
|![Automatyczne przewijanie do bieżącej ikony](media/parallel_toolbar4.png "Automatyczne przewijanie do bieżącej ikony")|Automatyczne przewijanie do bieżącej ramki stosu|Autoprzewija wykres, aby bieżąca Ramka stosu była w widoku. Ta funkcja jest przydatna, gdy zmieniasz bieżącą ramkę stosu z innych okien lub gdy trafisz nowy punkt przerwania w dużych wykresach.|
|![Przełącz ikonę powiększenia](media/parallel_toolbar5.png "Przełącz ikonę powiększenia")|Przełącz kontrolkę powiększenia|Pokazuje lub ukrywa kontrolkę powiększenia po lewej stronie okna. <br /><br />Bez względu na widoczność kontrolki powiększenia można również powiększać, naciskając klawisz **Ctrl** i przytrzymując kółka myszy, lub naciskając **klawisze CTRL** + **SHIFT** , + **+** Aby pomniejszyć i **nacisnąć klawisz** + **SHIFT** , + **-** Aby pomniejszyć. |

### <a name="stack-frame-icons"></a>Ikony ramek stosu
Poniższe ikony zawierają informacje o aktywnych i bieżących ramkach stosu we wszystkich widokach:

|Ikona|Opis|
|-|-|
|![Żółta strzałka](media/icon_parallelyellowarrow.gif)|Wskazuje bieżącą lokalizację (aktywną ramkę stosu) bieżącego wątku.|
|![Ikona wątków](media/icon_parallelthreads.gif)|Wskazuje bieżącą lokalizację (aktywną ramkę stosu) niebieżącego wątku.|
|![Zielona strzałka](media/icon_parallelgreenarrow.gif)|Wskazuje bieżącą ramkę stosu (bieżący kontekst debugera). Nazwa metody jest pogrubiona w dowolnym miejscu.|

### <a name="context-menu-items"></a>Elementy menu kontekstowego
Poniższe elementy menu skrótów są dostępne po kliknięciu prawym przyciskiem myszy w widoku **wątki** lub widoku **zadań** . Ostatnie sześć elementów jest taka sama jak w [oknie stosu wywołań](how-to-use-the-call-stack-window.md).

![Menu skrótów w oknie stosów równoległych](../debugger/media/parallel_contmenu.png "Menu skrótów w oknie stosów równoległych")

|Element menu|Opis|
|-|-|
|**Flaga**|Flaguje wybrany element.|
|**Usuń flagę z**|Usuń flagę wybranego elementu.|
|**Funkcja**|Powoduje zablokowanie wybranego elementu.|
|**Odblokuj**|Umożliwia odblokowanie wybranego elementu.|
|**Przełącz do ramki**|Analogicznie jak odpowiednie polecenie menu w oknie **stosu wywołań** . Jednak w oknie **stosów równoległych** jedna metoda może znajdować się w kilku ramkach. Możesz wybrać wybraną ramkę w podmenu dla tego elementu. Jeśli jedna z ramek stosu znajduje się w bieżącym wątku, ta ramka jest domyślnie zaznaczona w podmenu.|
|**Przejdź do zadania** lub **Przejdź do wątku**|Przełącza do widoku **zadań** lub **wątków** i utrzymuje wyróżnioną ramkę stosu.|
|**Przejdź do kodu źródłowego**|Przechodzi do odpowiedniej lokalizacji w oknie kod źródłowy. |
|**Przejdź do demontażu**|Przechodzi do odpowiedniej lokalizacji w oknie **demontażu** .|
|**Pokaż kod zewnętrzny**|Pokazuje lub ukrywa kod zewnętrzny.|
|**Wyświetlanie szesnastkowe**|Przełącza między liczbą dziesiętną i szesnastkową.|
|**Pokaż wątki w źródle**|Flaguje lokalizację wątku w oknie kod źródłowy. |
|**Informacje dotyczące załadowania symboli**|Otwiera okno dialogowe **Informacje o ładowaniu symboli** .|
|**Ustawienia symboli**|Otwiera okno dialogowe **Ustawienia symboli** . |

## <a name="threads-view"></a>Widok wątków

W widoku **wątków** Ramka stosu i ścieżka wywołania bieżącego wątku są wyróżnione kolorem niebieskim. Bieżąca lokalizacja wątku jest pokazana przez żółtą strzałkę.

Aby zmienić bieżącą ramkę stosu, kliknij dwukrotnie inną metodę. Może to również przełączać bieżący wątek, w zależności od tego, czy wybrana metoda jest częścią bieżącego wątku czy innego wątku.

Gdy wykres widoku **wątków** jest zbyt duży, aby zmieścił się w oknie, w oknie zostanie wyświetlony formant **widoku oka** . Możesz przenieść ramkę w kontrolce, aby przejść do różnych części wykresu.

Na poniższej ilustracji przedstawiono jeden wątek, który prowadzi od głównego do zarządzanego przejścia kodu w kodzie natywnym. Sześć wątków znajduje się w bieżącej metodzie. Jeden z nich przechodzi do wątku. uśpienia, a drugi nadal przechodzi do konsoli. WriteLine, a następnie do SyncTextWriter. WriteLine.

 ![Widok wątków w oknie stosów równoległych](../debugger/media/parallel_stack1.png "Widok wątków w oknie stosów równoległych")

W poniższej tabeli opisano główne funkcje widoku **wątki** :

|Wywołanie|Nazwa elementu|Opis|
|-|-|-|
|1|Segment lub węzeł stosu wywołań|Zawiera serię metod dla co najmniej jednego wątku. Jeśli ramka nie ma połączonych linii strzałek, ramka pokazuje całą ścieżkę wywołania dla wątków.|
|2|Wyróżnianie niebieskie|Wskazuje ścieżkę wywołania bieżącego wątku.|
|3|Linie strzałek|Połącz węzły, aby utworzyć całą ścieżkę wywołania dla wątków.|
|4|Nagłówek węzła|Pokazuje liczbę procesów i wątków dla węzła.|
|5|Metoda|Reprezentuje co najmniej jedną ramkę stosu w tej samej metodzie.|
|6|Etykietka narzędzia dla metody|Pojawia się po umieszczeniu wskaźnika myszy na metodzie. W widoku **wątki** etykietka narzędzia pokazuje wszystkie wątki, w tabeli podobnej do okna **wątki** . |

## <a name="tasks-view"></a>Widok zadań
Jeśli aplikacja używa <xref:System.Threading.Tasks.Task?displayProperty=fullName> obiektów (kodu zarządzanego) lub `task_handle` obiektów (kod natywny) do wyrażania równoległości, można użyć widoku **zadań** . Widok **zadań** pokazuje stosy wywołań zadań zamiast wątków.

W widoku **zadania** :

- Stosy wywołań wątków, które nie są uruchomione, nie są wyświetlane.
- Stosy wywołań wątków, które są uruchomionymi zadaniami, są przycinane na górze i u dołu, aby pokazać najbardziej odpowiednie ramki dla zadań.
- Gdy kilka zadań znajduje się w jednym wątku, stosy wywołań tych zadań są wyświetlane w osobnych węzłach.

Aby wyświetlić cały stos wywołań, przełącz się z powrotem do widoku **wątków** , klikając prawym przyciskiem myszy ramkę stosu i wybierając pozycję **Przejdź do wątku**.

Na poniższej ilustracji przedstawiono widok **wątków** u góry i widok odpowiednich **zadań** u dołu.

![Widoki wątków i zadań](../debugger/media/parallel_threads-tasks.png "Widoki wątków i zadań")

Umieść kursor nad metodą, aby wyświetlić etykietkę narzędzia z dodatkowymi informacjami. W widoku **zadania** etykietka narzędzia pokazuje wszystkie zadania w tabeli podobne do okna **zadania** .

Na poniższej ilustracji przedstawiono etykietkę narzędzia dla metody w widoku **wątki** u góry i dla odpowiedniego widoku **zadań** w dolnej części.

![Etykietki narzędzi wątków i zadań](../debugger/media/parallel_threads-tasks-tooltips.png "Etykietki narzędzi wątków i zadań")

## <a name="method-view"></a>Widok metody
W widoku **wątki** lub widoku **zadań** można przestawiać wykres na bieżącą metodę, wybierając ikonę **przełączania metody przełącznika** na pasku narzędzi. **Widok metody** pokazuje na bieżąco wszystkie metody we wszystkich wątkach wywoływanych lub wywoływanych przez bieżącą metodę. Na poniższej ilustracji pokazano, jak te same informacje wyglądają w widoku **wątki** po lewej stronie i w **widoku metody** po prawej stronie.

![Widok wątków i widok metody](../debugger/media/parallel_methodview.png "Widok wątków i widok metody")

Jeśli przełączysz się do nowej ramki stosu, nadajesz tej metodzie bieżącą metodę i **Widok metody** wyświetla wszystkie obiekty wywołujące i wywoływane dla nowej metody. Może to spowodować, że niektóre wątki pojawiają się lub znikają z widoku, w zależności od tego, czy ta metoda pojawia się na stosach wywołań. Aby powrócić do widoku stosu wywołań, wybierz ponownie ikonę paska narzędzi **widoku metody** .

## <a name="see-also"></a>Zobacz też
- [Rozpocznij debugowanie aplikacji wielowątkowej](../debugger/get-started-debugging-multithreaded-apps.md)
- [Przewodnik: debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md)
- [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md)
- [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)
- [Programowanie równoległe](/dotnet/standard/parallel-programming/index)
- [Korzystanie z okna zadań](../debugger/using-the-tasks-window.md)
- [Klasa zadania](../extensibility/debugger/task-class-internal-members.md)
