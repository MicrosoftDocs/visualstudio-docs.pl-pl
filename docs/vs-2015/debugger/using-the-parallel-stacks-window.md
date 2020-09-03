---
title: Korzystanie z okna stosów równoległych | Microsoft Docs
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
ms.openlocfilehash: e89125c8e1dea25ab02fe64c21b8166e9d65194a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542223"
---
# <a name="using-the-parallel-stacks-window"></a>Korzystanie z okna stosów równoległych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno **stosów równoległych** jest przydatne podczas debugowania aplikacji wielowątkowych. **Widok wątków** wyświetla informacje o stosie wywołań dla wszystkich wątków w aplikacji. Umożliwia nawigowanie między wątkami i ramkami stosu w tych wątkach. W kodzie zarządzanym **widok zadania** pokazuje stosy wywołań <xref:System.Threading.Tasks.Task?displayProperty=fullName> obiektów. W kodzie natywnym **widok zadania** przedstawia stosy wywołań [grup zadań](https://msdn.microsoft.com/library/42f05ac3-2098-494a-ba84-737fcdcad077), [algorytmów równoległych](https://msdn.microsoft.com/library/045dca7b-4d73-4558-a44c-383b88a28473), [agentów asynchronicznych](https://msdn.microsoft.com/library/6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a)i prostych [zadań](https://msdn.microsoft.com/library/9aba278c-e0c9-4ede-b7c6-fedf7a365d90).  
  
## <a name="threads-view"></a>Widok wątków  
 Na poniższej ilustracji przedstawiono jeden wątek, który został przeszedł od elementu Main do A do B, a następnie do pewnego kodu zewnętrznego. Dwa inne wątki rozpoczęte od pewnego kodu zewnętrznego, a następnie przeprowadziły do, ale jeden z wątków przeszedł do B, a następnie do pewnego kodu zewnętrznego, a drugi wątek do C, a następnie do niektórych AnonymousMethod.  
  
 ![Widok wątków w oknie stosów równoległych](../debugger/media/parallel-stacksthread.png "Parallel_StacksThread")  
  
 Na ilustracji ścieżka wywołania bieżącego wątku jest wyróżniona na niebiesko, a aktywna Ramka stosu jest oznaczona żółtą strzałką. Bieżącą ramkę stosu można zmienić, wybierając inną metodę w oknie **stosów równoległych** . Może to spowodować również przełączenie bieżącego wątku, w zależności od tego, czy wybrana metoda jest częścią bieżącego wątku, czy też z innego wątku. W poniższej tabeli opisano główne funkcje okna **stosów równoległych** , jak pokazano na ilustracji.  
  
|Litera objaśnienia|Nazwa elementu|Opis|  
|--------------------|------------------|-----------------|  
|A|Segment lub węzeł stosu wywołań|Zawiera serię kontekstów metody dla co najmniej jednego wątku. Jeśli węzeł nie ma połączonych linii strzałek, reprezentuje całą ścieżkę wywołania dla wątków.|  
|B|Wyróżnianie niebieskie|Wskazuje ścieżkę wywołania bieżącego wątku.|  
|C|Linie strzałek|Połącz węzły, aby utworzyć całą ścieżkę wywołania dla wątków.|  
|D|Etykietka narzędzia w nagłówku węzła|Pokazuje identyfikator i nazwę zdefiniowaną przez użytkownika dla każdego wątku, którego ścieżka wywołania ma udział w tym węźle.|  
|E|Kontekst metody|Reprezentuje co najmniej jedną ramkę stosu w tej samej metodzie.|  
|F|Etykietka narzędzia w kontekście metody|W widoku wątki pokazuje wszystkie wątki w tabeli podobne do okna **wątki** . W widoku zadań pokazuje wszystkie zadania w tabeli podobne do okna **zadań równoległych** .|  
  
 Ponadto Okno stosów równoległych pokazuje ikonę **widoku oka ptaka** w okienku głównym, gdy wykres jest zbyt duży, aby dopasować go do okna. Możesz kliknąć ikonę, aby wyświetlić cały wykres w oknie.  
  
## <a name="method-context-icons"></a>Ikony kontekstu metody  
 W poniższej tabeli opisano ikony, które zawierają informacje o aktywnych i bieżących ramkach stosu:  
  
|Ikona|Opis|  
|-|-|
|![Żółta strzałka Parallel Stacks](../debugger/media/icon-parallelyellowarrow.gif "Icon_ParallelYellowArrow")|Wskazuje, że kontekst metody zawiera aktywną ramkę stosu bieżącego wątku.|  
|![Ikona stosów równoległych wątków](../debugger/media/icon-parallelthreads.gif "Icon_ParallelThreads")|Wskazuje, że kontekst metody zawiera aktywną ramkę stosu, która nie jest bieżącym wątkiem.|  
|![Zielona strzałka na stosach równoległych](../debugger/media/icon-parallelgreenarrow.gif "Icon_ParallelGreenArrow")|Wskazuje, że kontekst metody zawiera bieżącą ramkę stosu. Ta nazwa metody jest pogrubiona we wszystkich węzłach, w których występuje.|  
  
## <a name="toolbar-controls"></a>Kontrolki paska narzędzi  
 Poniższa ilustracja i tabela zawiera opis formantów, które są dostępne na pasku narzędzi stosów równoległych.  
  
 ![Pasek narzędzi w oknie stosów równoległych](../debugger/media/parallel-stackstoolbar.png "Parallel_StacksToolbar")  
  
|Litera objaśnienia|Kontrola|Opis|  
|--------------------|-------------|-----------------|  
|A|Pole kombi wątki/zadania|Przełącza widok między stosami wywołań wątków i wywołań stosów zadań. Aby uzyskać więcej informacji, zobacz Widok zadań i wątki.|  
|B|Pokaż tylko Oflagowane|Pokazuje stosy wywołań tylko dla wątków, które są oflagowane w innych oknach debugowania, takich jak okno **wątków GPU** i okno **czujki równoległej** .|  
|C|Przełącz widok metody|Przełącza między widokiem stosu a widokiem metody. Aby uzyskać więcej informacji, zobacz widok metody.|  
|D|Automatyczne przewijanie do bieżącej ramki stosu|Autoprzewija diagram, aby bieżąca Ramka stosu była w widoku. Ta funkcja jest przydatna w przypadku zmiany bieżącej ramki stosu z innych okien lub po naciśnięciu nowego punktu przerwania w dużych diagramach.|  
|E|Przełącz kontrolkę powiększenia|Pokazuje lub ukrywa kontrolkę powiększenia. Możesz również powiększać przez naciśnięcie klawisza CTRL i przekształcenie kółka myszy, niezależnie od widoczności kontrolki powiększenia lub przy użyciu **kombinacji klawiszy Ctrl + Shift + ' + '** , aby powiększyć i **nacisnąć klawisze Ctrl + Shift + '-'** , aby pomniejszyć. Naciśnięcie **klawiszy Ctrl + F8** powróci do ekranu.|  
  
### <a name="context-menu-items"></a>Elementy menu kontekstowego  
 Poniższa ilustracja i tabela zawiera opis elementów menu skrótów, które są dostępne po kliknięciu prawym przyciskiem myszy kontekstu metody w widoku wątków lub widoku zadań. Ostatnie szóste elementy są popożyczone bezpośrednio z okna stosu wywołań i nie wprowadzają nowych zachowań.  
  
 ![Menu skrótów w oknie stosów równoległych](../debugger/media/parallel-contmenu.png "Parallel_ContMenu")  
  
|Element menu|Opis|  
|---------------|-----------------|  
|Flaga|Flaguje wybrany element.|  
|Usuń flagę z|Usuń flagę wybranego elementu.|  
|Funkcja|Powoduje zablokowanie wybranego elementu.|  
|Odblokuj|Umożliwia odblokowanie wybranego elementu.|  
|Przejdź do zadania (wątek)|Wykonuje tę samą funkcję, co pole kombi na pasku narzędzi, ale zachowuje tę samą ramkę stosu wyróżnioną.|  
|Przejdź do kodu źródłowego|Nawiguje do lokalizacji w kodzie źródłowym, która odnosi się do ramki stosu, którą kliknięto prawym przyciskiem myszy.|  
|Przełącz do ramki|Analogicznie jak odpowiednie polecenie menu w oknie stosu wywołań. Jednak w przypadku stosów równoległych wiele ramek może odpowiadać jednemu kontekstowi metody. W związku z tym element menu zawiera podmenu, z których każdy reprezentuje konkretną ramkę stosu. Jeśli jedna z ramek stosu znajduje się w bieżącym wątku, jest wybierane menu odpowiadające tej klatce stosu.|  
|Przejdź do demontażu|Nawiguje do lokalizacji w oknie demontażu, która odnosi się do ramki stosu, którą kliknięto prawym przyciskiem myszy.|  
|Pokaż kod zewnętrzny|Pokazuje lub ukrywa kod zewnętrzny.|  
|Wyświetlanie szesnastkowe|Przełącza między liczbą dziesiętną i szesnastkową.|  
|Informacje dotyczące załadowania symboli|Wyświetla odpowiednie okno dialogowe.|  
|Ustawienia symboli|Wyświetla odpowiednie okno dialogowe.|  
  
## <a name="tasks-view"></a>Widok zadań  
 Jeśli aplikacja korzysta <xref:System.Threading.Tasks.Task?displayProperty=fullName> z obiektów (kod zarządzany) lub `task_handle` obiektów (kod natywny) do wyrażania równoległości, można użyć pola kombi na pasku narzędzi okna stosów równoległych, aby przełączyć się do *widoku zadań*. Widok zadań pokazuje stosy wywołań zadań zamiast wątków. Widok zadań różni się od widoku wątków w następujący sposób:  
  
- Stosy wywołań wątków, które nie są uruchomione, nie są wyświetlane.  
  
- Stosy wywołań wątków, na których działają zadania, są przycinane w górę i w dół, aby pokazać najbardziej odpowiednie ramki, które odnoszą się do zadań.  
  
- Gdy kilka zadań znajduje się w jednym wątku, stosy wywołań tych zadań są podzielone na oddzielne węzły.  
  
  Na poniższej ilustracji przedstawiono widok zadań stosów równoległych po prawej stronie i widok odpowiednich wątków po lewej stronie.  
  
  ![Widok zadań w oknie stosów równoległych](../debugger/media/parallel-tasksview.png "Parallel_TasksView")  
  
  Aby wyświetlić cały stos wywołań, po prostu przełącz się z powrotem do widoku wątków, klikając prawym przyciskiem myszy ramkę stosu, a następnie klikając polecenie **Przejdź do wątku**.  
  
  Zgodnie z opisem w wcześniejszej tabeli przez umieszczenie kursora nad kontekstem metody, można wyświetlić dodatkowe informacje. Na poniższej ilustracji przedstawiono informacje w etykietce narzędzia dla widoku wątki i widok zadania.  
  
  ![Etykietki narzędzi w oknie stosów równoległych](../debugger/media/parallel-stack-tooltips.png "Parallel_Stack_Tooltips")  
  
## <a name="method-view"></a>Widok metody  
 W widokach wątków lub widoku zadań można przestawiać wykres na bieżącą metodę, klikając ikonę widoku metody na pasku narzędzi. Widok metody pokazuje na bieżąco wszystkie metody we wszystkich wątkach wywoływanych lub wywoływanych przez bieżącą metodę. Na poniższej ilustracji przedstawiono Widok wątków, a także sposób, w jaki te same informacje wyglądają w widoku metody.  
  
 ![Widok metody w oknie stosów równoległych](../debugger/media/parallel-methodview.png "Parallel_MethodView")  
  
 Przełączenie do nowej ramki stosu oznacza, że ta metoda jest bieżącą metodą i powoduje, że okno wyświetla wszystkie obiekty wywołujące i wywoływane dla nowej metody. Może to spowodować, że niektóre wątki pojawiają się lub znikają z widoku, w zależności od tego, czy ta metoda pojawia się na stosach wywołań. Aby powrócić do widoku stosu, kliknij przycisk paska narzędzi widoku metody.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: debugowanie aplikacji równoległej](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)   
 [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)   
 [Programowanie równoległe](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [Korzystanie z okna zadania](../debugger/using-the-tasks-window.md)   
 [Przewodnik: debugowanie aplikacji równoległej](../debugger/walkthrough-debugging-a-parallel-application.md)   
 [Task, klasa](../extensibility/debugger/task-class-internal-members.md)
