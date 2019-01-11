---
title: Wyświetl wątki w okna stosów równoległych | Dokumentacja firmy Microsoft
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4e08171c02288f89e706c80ab6dfd5ef9538318c
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227944"
---
# <a name="view-threads-and-tasks-in-the-parallel-stacks-window-c-visual-basic-c"></a>Wyświetlanie wątkach i zadaniach w okna stosów równoległych (C#, Visual Basic, C++)

**Stosów równoległych** okno jest przydatne w przypadku debugowania aplikacji wielowątkowych. Ma kilka widoków:

- [Widok wątków](#threads-view) pokazuje informacje stosu wywołań dla wszystkich wątków w aplikacji. Możesz przechodzić między wątkami i ramki stosu w tych wątkach. 

- [Zadania widoku](#tasks-view) pokazuje informacje stosu wywołań wyśrodkowany zadania. 
  - W kodzie zarządzanym **zadania** widok pokazuje stosy wywołań <xref:System.Threading.Tasks.Task?displayProperty=fullName> obiektów. 
  - W kodzie natywnym **zadania** widok pokazuje stosy wywołań [grupy zadań](/cpp/parallel/concrt/task-parallelism-concurrency-runtime), [równoległe algorytmy](/cpp/parallel/concrt/parallel-algorithms), [agentów asynchronicznych](/cpp/parallel/concrt/asynchronous-agents)i [zadań lekkich](/cpp/parallel/concrt/task-scheduler-concurrency-runtime).  
  
- [Metoda widoku](#method-view) obracając stos wywołań w przypadku wybranej metody. 

## <a name="use-the-parallel-stacks-window"></a>Korzystanie z okna stosów równoległych 

Aby otworzyć **stosów równoległych** okna, jest możliwe tylko w sesji debugowania. Wybierz **debugowania** > **Windows** > **stosów równoległych**. 

### <a name="toolbar-controls"></a>Formanty paska narzędzi

**Stosów równoległych** okno zawiera następujące kontrolki paska narzędzi: 

![Pasek narzędzi okna stosów równoległych](../debugger/media/parallel_stackstoolbar.png "narzędzi stosów równoległych")  
  
|Ikona|Formant|Opis|  
|-|-|-|  
|![Pole kombi wątków/zadań](media/parallel_toolbar1.png "pola kombi wątków/zadań")|**Wątki**/**zadania** pola kombi|Przełącza widok między Wywołaj stosy wątków i Wywołaj stosy zadania. Aby uzyskać więcej informacji, zobacz [zadania widoku](#tasks-view) i [wątki widoku](#threads-view).|  
|![Pokaż tylko oflagowane ikonę](media/parallel_toolbar2.png "ikonę Pokaż tylko oflagowane")|Pokaż tylko oflagowane|Pokazuje stosy wywołań tylko dla wątków, które są oznaczone w innych oknach debugera, takie jak **wątków GPU** okna i **równoległego wyrażenia kontrolnego** okna.|  
|![Przełącz widok metody ikonę](media/parallel_toolbar3.png "ikonę Przełącz widok metody")|Przełącz **widok — metoda**|Przełącza pomiędzy widokami stos wywołań i **widoku metody**. Aby uzyskać więcej informacji, zobacz [widoku metody](#method-view).|  
|![Automatycznie przewiń do bieżącej ikony](media/parallel_toolbar4.png "automatycznie przewiń do bieżącej ikony")|Automatycznie przewiń do bieżącej ramki stosu|Autoscrolls wykres, aby bieżącego stosu ramki znajduje się w widoku. Ta funkcja jest przydatna w przypadku zmiany bieżącej ramki stosu z innymi oknami lub uruchom nowy punkt przerwania w dużych wykresów.|  
|![Ikona powiększenia Przełącz](media/parallel_toolbar5.png "ikona przełączania powiększenia")|Przełącz kontrolkę powiększenia|Pokazuje lub ukrywa kontrolka powiększania w lewej części okna. <br /><br />Niezależnie od tego, widoczność kontrolka powiększania w ten sam efekt, naciskając klawisz **Ctrl** i włączenie kółka myszy lub przez naciśnięcie klawisza **Ctrl**+**Shift** + **+** do powiększania i **Ctrl**+**Shift** + **-** Aby pomniejszyć. |  
  
### <a name="stack-frame-icons"></a>Ikony ramki stosu
Następujące ikony zawierają informacje o ramkach stosu active i bieżących we wszystkich widokach:

|Ikona|Opis|  
|-|-|  
|![Żółta strzałka](media/icon_parallelyellowarrow.gif)|Wskazuje bieżącą lokalizację bieżącego wątku (Aktywna ramka stosu).|
|![Ikona wątków](media/icon_parallelthreads.gif)|Wskazuje bieżącą lokalizację (Aktywna ramka stosu) innym niż bieżący wątek.|
|![Zielona strzałka](media/icon_parallelgreenarrow.gif)|Wskazuje bieżącą ramkę stosu (bieżący kontekst debugera). Nazwa metody jest pogrubiony wszędzie tam, gdzie pojawia się.|  

### <a name="context-menu-items"></a>Elementy menu kontekstowego  
Dostępne są następujące elementy menu skrótów, po kliknięciu prawym przyciskiem myszy metodę w **wątków** widoku lub **zadania** widoku. Ostatnie sześć elementów są takie same jak w [oknie wywołania stosu](how-to-use-the-call-stack-window.md).  

![Menu skrótów okna stosów równoległych](../debugger/media/parallel_contmenu.png "menu skrótów okna stosów równoległych")  

|Element menu|Opis|  
|-|-|  
|**Flaga**|Flagi wybranego elementu.|  
|**Usuń flagę**|Unflags wybranego elementu.|  
|**blokowanie**|Zawiesza się wybrany element.|  
|**Odblokowywanie**|Thaws wybranego elementu.|  
|**Przełącz do ramki**|Takie same jak odpowiednie menu poleceń w **stos wywołań** okna. Jednak w **stosów równoległych** oknie jedna metoda może być kilka ramek. Możesz wybrać ramkę, którą chcesz, aby w podmenu dla tego elementu. W przypadku jednej ramki stosu w bieżącym wątku, ramki jest domyślnie zaznaczona, w podmenu.|  
|**Przejdź do zadania** lub **przejdź do wątku**|Przełącza do **zadań** lub **wątków** widoku i przechowuje takie same stosu ramki wyróżnione.|  
|**Przejdź do kodu źródłowego**|Przejście do odpowiedniej lokalizacji w oknie kodu źródłowego. |  
|**Przejdź do demontażu**|Przechodzi do odpowiedniej lokalizacji w **dezasemblacji** okna.|  
|**Pokaż kod zewnętrzny**|Pokazuje lub ukrywa kod zewnętrzny.|  
|**Wyświetlanie szesnastkowe**|Przełącza pomiędzy wyświetlania dziesiętną, a szesnastkową.|  
|**Pokaż wątki w źródle**|Flagi lokalizacji wątku w oknie kodu źródłowego. |  
|**Informacje o ładowaniu symboli**|Otwiera **informacje o ładowaniu symboli** okno dialogowe.|  
|**Ustawienia symboli**|Otwiera **ustawienia symboli** okno dialogowe. |  
  
## <a name="threads-view"></a>Widok wątków  

W **wątków** wyświetlić ramki stosu i ścieżki wywołań bieżącego wątku będą wyróżnione na niebiesko. Żółta strzałka wyświetlana jest lokalizacja bieżącego wątku. 

Aby zmienić bieżącą ramkę stosu, kliknij dwukrotnie innej metody. Może to również przełączyć bieżący wątek, w zależności od tego, czy metoda, którą wybierzesz jest częścią bieżącego wątku lub inny wątek. 

Gdy **wątków** Wyświetl wykres jest zbyt duży, aby mieściły się w oknie **ptaka** kontroli pojawia się w oknie. Możesz przenieść ramki w formancie, aby przejść do różnych części wykresu.  
  
Poniższa ilustracja przedstawia jeden wątek, który przechodzi z głównego do zarządzanego, do którego nastąpi przejście z kodu natywnego. Sześć wątki są w bieżącej metodzie. Jeden w dalszym ciągu Thread.Sleep i kontynuuje innego elementu Console.WriteLine, a następnie SyncTextWriter.WriteLine.  

 ![Widok okna stosów równoległych wątków](../debugger/media/parallel_stack1.png "wątki widoku okna stosów równoległych")  

W poniższej tabeli opisano główne funkcje **wątków** widoku:  
  
|Objaśnienie|Nazwa elementu|Opis|  
|-|-|-|  
|1|Segment stosu wywołań lub węzła|Zawiera szereg metod dla jednego lub więcej wątków. Jeśli ramki nie ma do niego podłączone wierszy strzałkę, ramki przedstawia całą wywołania dla wątków.|  
|2|Niebieskie podkreślenie|Wskazuje ścieżkę wywołań bieżącego wątku.|  
|3|Strzałka wierszy|Łączenie węzłów, tworząc ścieżkę wywołania całej wątki.|  
|4|Nagłówek węzła|Pokazuje liczbę procesów i wątków dla węzła.|  
|5|Metoda|Reprezentuje jedną lub więcej ramek stosu w tej samej metody.|  
|6|Etykietka narzędzia na — metoda|Pojawia się po najechaniu kursorem na metodę. W **wątków** widoku etykietki narzędzia jest wyświetlana wszystkie wątki w podobny do tabeli **wątków** okna. |  

## <a name="tasks-view"></a>Widok zadania  
Jeśli aplikacja używa <xref:System.Threading.Tasks.Task?displayProperty=fullName> obiektów (kod zarządzany) lub `task_handle` obiektów (kodu natywnego) do wyrażania równoległości, można użyć **zadania** widoku. **Zadania** widok pokazuje stosy wywołań zadań zamiast wątków. 

W **zadania** widoku:  
  
- Stosy wywołań wątków, które nie są uruchomione zadania nie są wyświetlane.  
- Stosy wywołań wątków, które są uruchomione zadania wizualnie są usuwane u góry i u dołu, aby wyświetlić najbardziej istotnych ramki dla zadania.  
- Po kilku zadań znajdują się w jednym wątku, stosy wywołań tych zadań są wyświetlane w osobnych węzłach.  

Aby wyświetlić cały stos wywołań, przejdź z powrotem do **wątków** widoku, klikając prawym przyciskiem myszy ramkę stosu i wybierając polecenie **przejdź do wątku**.  

Poniższa ilustracja przedstawia **wątków** widok na początku, a odpowiedni **zadania** widoku u dołu.  

![Widoki wątkach i zadaniach](../debugger/media/parallel_threads-tasks.png "wątkach i zadaniach widoków")  

Umieść kursor nad metodę, aby wyświetlić etykietkę narzędzia z dodatkowymi informacjami. W **zadania** widoku etykietka narzędzia pokazuje wszystkie zadania w tabeli podobne do **zadania** okna. 

Na poniższej ilustracji przedstawiono etykietkę narzędzia dla metody w **wątków** widoku u góry, a dla odpowiedniego **zadania** widoku u dołu.  

![Etykietki narzędzi wątkach i zadaniach](../debugger/media/parallel_threads-tasks-tooltips.png "wątkach i zadaniach etykietek narzędzi")  

## <a name="method-view"></a>Widok — metoda  
Z poziomu **wątków** widoku lub **zadania** widoku wykresu na bieżącą metodę można przestawiać, wybierając **Przełącz widok metody** ikonę na pasku narzędzi. **Metoda widoku** przedstawiono w skrócie wszystkie metody we wszystkich wątkach, które są wywoływane przy bieżącej metody lub wywołania. Na poniższej ilustracji przedstawiono, jak wygląda te same informacje **wątków** wyświetlanie po lewej stronie i w **widoku metody** po prawej stronie.  

![Wątki widoku oraz widoku metody](../debugger/media/parallel_methodview.png "wątki widoku oraz widoku — metoda")  
  
Jeśli przełączysz się do nowej ramki stosu, można utworzyć tej metody bieżącej metody i **widoku metody** pokazuje wszystkie obiekty wywołujące i wywoływane dla nowej metody. Może to spowodować, że niektóre wątki wyświetlone lub znikają z widoku, w zależności od tego, czy ta metoda jest wyświetlana na ich stosy wywołań. Aby powrócić do widoku stosu wywołań, wybierz **widoku metody** ponownie ikonę paska narzędzi.  
  
## <a name="see-also"></a>Zobacz także  
 [Rozpoczynanie debugowania aplikacji wielowątkowych](../debugger/get-started-debugging-multithreaded-apps.md)   
 [Przewodnik: Debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Pierwsze spojrzenie na debugera](../debugger/debugger-feature-tour.md) [debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)   
 [Programowanie równoległe](/dotnet/standard/parallel-programming/index)   
 [Korzystanie z okna zadań](../debugger/using-the-tasks-window.md)   
 [Task — klasa](../extensibility/debugger/task-class-internal-members.md)
