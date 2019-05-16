---
title: Za pomocą równoległych stosów okna | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.parallelstacks
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: f50efb78-5206-4803-bb42-426ef8133f2f
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: df764ac38f437be33b71e7a816709a46234f751e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65684218"
---
# <a name="using-the-parallel-stacks-window"></a>Korzystanie z okna stosów równoległych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Stosów równoległych** okno jest przydatne podczas debugowania aplikacji wielowątkowych. Jego **Widok wątków** pokazuje informacje stosu wywołań dla wszystkich wątków w aplikacji. Dzięki temu można przechodzić między wątkami i ramki stosu w tych wątkach. W kodzie zarządzanym **widoku zadania** pokazuje Wywołaj stosy <xref:System.Threading.Tasks.Task?displayProperty=fullName> obiektów. W kodzie natywnym **widoku zadania** pokazuje Wywołaj stosy [grupy zadań](https://msdn.microsoft.com/library/42f05ac3-2098-494a-ba84-737fcdcad077), [równoległe algorytmy](https://msdn.microsoft.com/library/045dca7b-4d73-4558-a44c-383b88a28473), [agentów asynchronicznych](https://msdn.microsoft.com/library/6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a)i [zadań lekkich](https://msdn.microsoft.com/library/9aba278c-e0c9-4ede-b7c6-fedf7a365d90).  
  
## <a name="threads-view"></a>Widok wątków  
 Poniższa ilustracja przedstawia jeden wątek, który wystąpił z głównym a, B, a następnie kodu zewnętrznego. Dwie inne wątki pracę z zewnętrznego kodu, a następnie przeszedł do A, ale jeden z wątków, ciąg dalszy B, a następnie zewnętrznego kodu i innego wątku ciąg dalszy C, a następnie niektóre AnonymousMethod.  
  
 ![Widok okna stosów równoległych wątków](../debugger/media/parallel-stacksthread.png "Parallel_StacksThread")  
  
 Na ilustracji ścieżka wywołań bieżącego wątku jest wyróżnione na niebiesko i aktywną ramkę stosu jest oznaczona żółtą strzałką. Bieżąca ramka stosu można zmienić, wybierając inną metodę w **stosów równoległych** okna. Może to spowodować również przełączanie bieżącego wątku, w zależności od tego, czy wybrana metoda jest częścią już bieżącego wątku lub inny wątek. W poniższej tabeli opisano główne funkcje **stosów równoległych** okna, jak pokazano na ilustracji.  
  
|Objaśnienie list|Nazwa elementu|Opis|  
|--------------------|------------------|-----------------|  
|ELEMENT|Segment stosu wywołań lub węzła|Zawiera szereg metoda konteksty dla jednego lub więcej wątków. Jeśli węzeł nie ma do niego podłączone wierszy strzałkę, jego reprezentuje ścieżkę całego wywołania dla wątków.|  
|B|Niebieskie podkreślenie|Wskazuje ścieżkę wywołań bieżącego wątku.|  
|C|Strzałka wierszy|Łączenie węzłów, tworząc ścieżkę wywołania całej wątki.|  
|D|Etykietka narzędzia w nagłówku węzła|Zawiera identyfikator i zdefiniowanych przez użytkownika nazwa każdego wątku, którego ścieżka wywołanie udziałów tego węzła.|  
|E|Kontekst — metoda|Reprezentuje jedną lub więcej ramek stosu w tej samej metody.|  
|F|Etykietka narzędzia w kontekście — metoda|W widoku wątków pokazuje wszystkie wątki w tabeli podobne do **wątków** okna. W widoku zadań pokazuje wszystkie zadania w tabeli podobne do **zadań równoległych** okna.|  
  
 Ponadto przedstawiono okna stosów równoległych **ptaka** ikonę w okienku głównym, gdy wykres jest zbyt duży, aby mieściły się w oknie. Możesz kliknąć ikonę, aby zobaczyć cały wykres w oknie.  
  
## <a name="method-context-icons"></a>Ikony kontekstu — metoda  
 W poniższej tabeli opisano ikony, które zawierają informacje dotyczące ramek stosu aktywnych i bieżące:  
  
|||  
|-|-|  
|Ikona|Opis|  
|![Żółta strzałka stosów równoległych](../debugger/media/icon-parallelyellowarrow.gif "Icon_ParallelYellowArrow")|Wskazuje, że kontekst metody zawiera aktywną ramkę stosu bieżącego wątku.|  
|![Ikona wątków stosów równoległych](../debugger/media/icon-parallelthreads.gif "Icon_ParallelThreads")|Wskazuje, że kontekst metody zawiera aktywną ramkę stosu wątku innej niż bieżąca.|  
|![Zielona strzałka stosów równoległych](../debugger/media/icon-parallelgreenarrow.gif "Icon_ParallelGreenArrow")|Wskazuje, czy kontekst metody zawiera bieżącą ramkę stosu. Nazwa tej metody jest pogrubiony w wszystkie węzły, w których występuje.|  
  
## <a name="toolbar-controls"></a>Formanty paska narzędzi  
 Ilustracja i tabela poniżej opisano formanty, które są dostępne na pasku narzędzi stosów równoległych.  
  
 ![Pasek narzędzi okna stosów równoległych](../debugger/media/parallel-stackstoolbar.png "Parallel_StacksToolbar")  
  
|Objaśnienie list|formant|Opis|  
|--------------------|-------------|-----------------|  
|ELEMENT|Pole kombi wątków/zadań|Przełącza widok między Wywołaj stosy wątków i Wywołaj stosy zadania. Aby uzyskać więcej informacji zobacz widoku zadania i Widok wątków.|  
|B|Pokaż tylko oflagowane|Pokazuje stosy wywołań tylko dla wątków, które są oznaczone w innych oknach debugowania, takie jak **wątków GPU** okna i **równoległego wyrażenia kontrolnego** okna.|  
|C|Przełącz widok metody|Przełącza między widokiem stosu i metody. Aby uzyskać więcej informacji zobacz widoku metody.|  
|D|Automatycznie przewiń do bieżącej ramki stosu|Autoscrolls diagramu, aby bieżącego stosu ramki znajduje się w widoku. Ta funkcja jest przydatna, gdy w przypadku zmiany bieżącej ramki stosu w innych oknach lub w przypadku osiągnięcia nowy punkt przerwania w dużych diagramów.|  
|E|Przełącz kontrolkę powiększenia|Pokazuje lub ukrywa Kontrolka powiększenia. Ten sam efekt, naciskając klawisz CTRL i włączenie kółka myszy, niezależnie od tego, widoczność Kontrolka powiększenia lub używając **CTRL + SHIFT + '+'** Aby powiększyć i **CTRL + SHIFT + "-"** Aby pomniejszyć. Naciśnięcie klawisza **CTRL + F8** będzie Dopasuj widok do rozmiaru ekranu.|  
  
### <a name="context-menu-items"></a>Elementy Menu kontekstowego  
 Ilustracja i tabela poniżej opisano elementy menu skrótów, które są dostępne po kliknięciu prawym przyciskiem myszy w kontekście metody, w widoku wątków lub zadania. Ostatnie sześć elementów są pobierają bezpośrednio z okna stosu wywołań i powodować nie nowe zachowanie.  
  
 ![Menu skrótów okna stosów równoległych](../debugger/media/parallel-contmenu.png "Parallel_ContMenu")  
  
|Element menu|Opis|  
|---------------|-----------------|  
|Flaga|Flagi wybranego elementu.|  
|Usuń flagę|Unflags wybranego elementu.|  
|Freeze|Zawiesza się wybrany element.|  
|Odblokowywanie|Thaws wybranego elementu.|  
|Przejdź do zadania (wątek)|Pełni taką samą funkcję jak pole kombi na pasku narzędzi, ale utrzymuje ten sam ramki stosu wyróżnione.|  
|Przejdź do kodu źródłowego|Powoduje przejście do lokalizacji w kodzie źródłowym, odpowiadający ramki stosu, który kliknięto prawym przyciskiem myszy użytkownika.|  
|Przełącz do ramki|Taka sama jak odpowiednie polecenie menu w oknie stosu wywołań. Jednak za pomocą stosów równoległych większą liczbę ramek może odpowiadać jednej metody kontekstu. Dlatego element menu ma podmenu, z których każdy reprezentuje ramki określonego stosu. W przypadku jednej ramki stosu w bieżącym wątku, menu, który odnosi się do tej ramki stosu jest zaznaczone.|  
|Przejdź do demontażu|Powoduje przejście do lokalizacji w oknie demontażu odpowiadający ramki stosu, który kliknięto prawym przyciskiem myszy użytkownika.|  
|Pokaż kod zewnętrzny|Pokazuje lub ukrywa kod zewnętrzny.|  
|Wyświetlanie szesnastkowe|Przełącza pomiędzy wyświetlania dziesiętną, a szesnastkową.|  
|Informacje dotyczące załadowania symboli|Wyświetla odpowiednie okno dialogowe.|  
|Ustawienia symboli|Wyświetla odpowiednie okno dialogowe.|  
  
## <a name="tasks-view"></a>Widok zadania  
 Jeśli aplikacja wykorzystuje <xref:System.Threading.Tasks.Task?displayProperty=fullName> obiektów (kod zarządzany) lub `task_handle` obiektów (kodu natywnego) do wyrażania równoległości umożliwia pola kombi na pasku narzędzi okna stosów równoległych przełączyć się do *widoku zadania*. Widok zadania przedstawia stosy wywołań zadań zamiast wątków. Widok zadania różni się od widoku wątków w następujący sposób:  
  
- Stosy wywołań wątków, które nie zostały uruchomione zadania nie są wyświetlane.  
  
- Stosy wywołań wątków, które są uruchomione zadania wizualnie są usuwane u góry i u dołu, aby wyświetlić najbardziej istotnych ramek, które odnoszą się do zadań.  
  
- W przypadku wielu zadań w jednym wątku, stosy wywołań tych zadań są dzielone na osobne węzły.  
  
  Na poniższej ilustracji przedstawiono równoległych stosów widoku zadania po prawej stronie i odpowiedniego widoku wątków po lewej stronie.  
  
  ![Zadania widoku okna stosów równoległych](../debugger/media/parallel-tasksview.png "Parallel_TasksView")  
  
  Aby wyświetlić cały stos wywołań, wystarczy przełączyć do widoku wątków przez kliknięcie prawym przyciskiem myszy ramkę stosu, a następnie klikając polecenie **przejdź do wątku**.  
  
  Zgodnie z opisem w tabeli wcześniej, ustawiając kursor w kontekście metody, można przeglądać dodatkowe informacje. Na poniższej ilustracji przedstawiono informacje w etykietce narzędzia, widok wątki i widoku zadań.  
  
  ![Etykietki narzędzi w okna stosów równoległych](../debugger/media/parallel-stack-tooltips.png "Parallel_Stack_Tooltips")  
  
## <a name="method-view"></a>Widok — metoda  
 Widok wątków lub widoku zadań można przestawiać wykresu na bieżącą metodę, klikając ikonę widoku metody, na pasku narzędzi. Metoda widoku wyświetlane są w skrócie wszystkie metody we wszystkich wątkach, które są wywoływane przy bieżącej metody lub wywołania. Na poniższej ilustracji przedstawiono widok wątków, a także wygląd te same informacje w widoku metody.  
  
 ![Metoda widok okna stosów równoległych](../debugger/media/parallel-methodview.png "Parallel_MethodView")  
  
 Przełączając się do nowej ramki stosu, można spowodować tej metody bieżącej metody i okna pokazać wszystkie obiekty wywołujące i wywoływane dla nowej metody. Może to spowodować, że niektóre wątki wyświetlone lub znikają z widoku, w zależności od tego, czy ta metoda jest wyświetlana na ich stosy wywołań. Aby powrócić do widoku stosu, kliknij ponownie przycisk paska narzędzi widoku metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)   
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)   
 [Programowanie równoległe](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [Korzystanie z okna zadań](../debugger/using-the-tasks-window.md)   
 [Przewodnik: Debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Task, klasa](../extensibility/debugger/task-class-internal-members.md)
