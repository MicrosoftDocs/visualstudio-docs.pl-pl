---
title: Korzystanie z okna zadania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.paralleltasks
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, parallel tasks window
ms.assetid: bd5e0612-a0dc-41cf-a7af-1e87d0d5c35f
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 267a04e0d717bde311423aae7f35fba07ca6f39b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684035"
---
# <a name="using-the-tasks-window"></a>Korzystanie z okna zadań
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Okno **zadania** przypomina okno **wątków** , z tą różnicą, że wyświetla informacje o <xref:System.Threading.Tasks.Task?displayProperty=fullName> obiektach, [task_handle](https://msdn.microsoft.com/library/b4af5b28-227d-4488-8194-0a0d039173b7)lub [WinJS. Promise](https://msdn.microsoft.com/library/windows/apps/br211867.aspx) obiektów zamiast poszczególnych wątków. Podobnie jak wątki, zadania reprezentują operacje asynchroniczne, które mogą być uruchamiane współbieżnie; można jednak uruchomić wiele zadań w tym samym wątku. Aby uzyskać więcej informacji, zobacz [programowanie asynchroniczne w języku JavaScript (aplikacje ze sklepu Windows)](https://msdn.microsoft.com/library/windows/apps/hh700330.aspx) .  
  
 W kodzie zarządzanym można użyć okna **zadania** podczas pracy z <xref:System.Threading.Tasks.Task?displayProperty=fullName> obiektami lub z słowami kluczowymi **await** i **Async** (**await** i **Async** w języku VisualBasic). Aby uzyskać więcej informacji o zadaniach w kodzie zarządzanym, zobacz  [programowanie równoległe](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d).  
  
 W kodzie natywnym można użyć okna **zadania** podczas pracy z [grupami zadań](https://msdn.microsoft.com/library/42f05ac3-2098-494a-ba84-737fcdcad077), [algorytmami równoległymi](https://msdn.microsoft.com/library/045dca7b-4d73-4558-a44c-383b88a28473), [agentami asynchronicznymi](https://msdn.microsoft.com/library/6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a)i [zadaniami uproszczonymi](https://msdn.microsoft.com/library/9aba278c-e0c9-4ede-b7c6-fedf7a365d90). Aby uzyskać więcej informacji o zadaniach w kodzie natywnym, zobacz [środowisko uruchomieniowe współbieżności](https://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c).  
  
 W języku JavaScript można użyć okna zadania podczas pracy z obietnicą. Następnie kod.  
  
 Okna **zadania** można użyć po każdym przerwaniu w debugerze. Możesz uzyskać do niego dostęp w menu **Debuguj** , klikając pozycję **Windows** , a następnie klikając pozycję **zadania**. Poniższa ilustracja przedstawia okno **zadania** w jego domyślnym trybie.  
  
 ![Okno zadań równoległych](../debugger/media/parallel-tasks-window.png "Parallel_Tasks_Window")  
  
> [!NOTE]
> W kodzie zarządzanym, <xref:System.Threading.Tasks.Task> który ma stan <xref:System.Threading.Tasks.TaskStatus> , <xref:System.Threading.Tasks.TaskStatus> , lub <xref:System.Threading.Tasks.TaskStatus> może nie być wyświetlany w oknie zadania, gdy zarządzane wątki są w stanie uśpienia lub przyłączania.  
  
## <a name="tasks-column-information"></a>Informacje o kolumnie zadania  
 W kolumnach okna **zadania** są wyświetlane poniższe informacje.  
  
|Nazwa kolumny|Opis|  
|-----------------|-----------------|  
|**Znaczników**|Pokazuje, które zadania są oflagowane i umożliwiają Flagowanie lub usuwanie flagi zadania.|  
|**Ikony**|Żółta strzałka wskazuje bieżące zadanie. Bieżące zadanie to zadanie najwyższego poziomu w bieżącym wątku.<br /><br /> Biała Strzałka wskazuje zadanie przerywania, czyli bieżące, gdy debuger został wywołany.<br /><br /> Ikona Wstrzymaj oznacza zadanie, które zostało zamrożone przez użytkownika. Zadanie można zablokować i odblokować, klikając je prawym przyciskiem myszy na liście.|  
|**ID**|Numer dostarczony przez system dla zadania. W kodzie natywnym jest to adres zadania.|  
|**Stan**|Bieżący stan (zaplanowany, aktywny, zakleszczony, oczekujący lub ukończony) zadania. Zaplanowane zadanie to takie, które nie zostało jeszcze uruchomione i dlatego nie zawiera jeszcze stosu wywołań, przypisanego wątku ani powiązanych informacji.<br /><br /> Aktywne zadanie to takie, które wykonywało kod przed przerwaniem w debugerze.<br /><br /> Zadanie oczekujące to takie, które jest blokowane, ponieważ oczekuje na zdarzenie, które ma być sygnalizowane, blokadę do zwolnienia lub inne zadanie do zakończenia.<br /><br /> Zazakleszczony zadanie to oczekujące zadanie, którego wątek jest zakleszczony przy użyciu innego wątku.<br /><br /> Umieść kursor nad komórką **stanu** dla zadania zakleszczenie lub oczekujące, aby wyświetlić więcej informacji na temat bloku. **Ostrzeżenie:**  Okno **zadania** raportuje zakleszczenie tylko dla zablokowanego zadania, które używa elementu podstawowego synchronizacji, który jest obsługiwany przez przechodzenie łańcucha oczekiwania (WCT). Na przykład w przypadku zakleszczenia <xref:System.Threading.Tasks.Task> obiektu, który używa WCT, debuger zgłasza **oczekiwanie na zakleszczenie**. W przypadku zadania, które jest zarządzane przez środowisko uruchomieniowe współbieżności, które nie korzysta z WCT, debuger zgłasza **oczekiwanie**. Aby uzyskać więcej informacji na temat WCT, zobacz [przechodzenie łańcucha oczekiwania](https://msdn.microsoft.com/library/ms681622\(VS.85\).aspx).|  
|**Godzina rozpoczęcia**|Godzina, o której zadanie stało aktywne.|  
|**Czas trwania**|Liczba sekund, przez jaką zadanie jest aktywne.|  
|**Czas ukończenia**|Godzina ukończenia zadania.|  
|**Lokalizacja**|Bieżąca lokalizacja w stosie wywołań zadania. Umieść kursor nad tą komórką, aby zobaczyć cały stos wywołań dla zadania. Zaplanowane zadania nie mają wartości w tej kolumnie.|  
|**Zadanie**|Metoda początkowa i wszystkie argumenty, które zostały przekazane do zadania podczas jego tworzenia.|  
|**Nadrzędny**|Identyfikator zadania, które spowodowało utworzenie tego zadania. Jeśli to pole jest puste, zadanie nie ma elementu nadrzędnego. Ma to zastosowanie tylko w przypadku programów zarządzanych.|  
|**Przypisanie wątku**|Identyfikator i nazwa wątku, w którym jest uruchomione zadanie.|  
|**Stan powrotu**|Stan zadania po zakończeniu. Wartości stanu powrotu to **sukces**, **anulowane**i **błąd**.|  
|**Wywołując**|Dla kodu zarządzanego, domena aplikacji, w której wykonywane jest zadanie.|  
|**task_group**|Dla kodu natywnego, adres [task_group](https://msdn.microsoft.com/library/b4af5b28-227d-4488-8194-0a0d039173b7) obiektu, który zaplanował zadanie. W przypadku agentów asynchronicznych i uproszczonych zadań ta kolumna jest ustawiona na 0.|  
|Proces|Identyfikator procesu, w którym uruchomiono zadanie.|  
|Stan asynchroniczny|Dla kodu zarządzanego zadanie ma stan. Domyślnie ta kolumna jest ukryta. Aby wyświetlić tę kolumnę, otwórz menu kontekstowe dla jednego z nagłówków kolumn. Wybierz **kolumny**, **AsyncState**.|  
  
 Kolumny do widoku można dodać, klikając prawym przyciskiem myszy nagłówek kolumny, a następnie wybierając odpowiednie kolumny. (Usuń kolumny przez wyczyszczenie opcji). Możesz również zmienić kolejność kolumn, przeciągając je w lewo lub w prawo. Menu skrótów kolumny jest pokazane na poniższej ilustracji.  
  
 ![Menu Widok skrótu w oknie zadania równoległe](../debugger/media/parallel-tasks-contextmenu.png "Parallel_Tasks_ContextMenu")  
  
## <a name="sorting-tasks"></a>Sortowanie zadań  
 Aby posortować zadania według kryteriów kolumn, kliknij nagłówek kolumny. Na przykład klikając nagłówek kolumny **Identyfikator** , można sortować zadania według identyfikatora zadania: 1, 2, 3, 4, 5 itd. Aby odwrócić porządek sortowania, ponownie kliknij nagłówek kolumny. Bieżąca kolumna sortowania i porządek sortowania jest wskazywany przez strzałkę w kolumnie.  
  
## <a name="grouping-tasks"></a>Grupowanie zadań  
 Zadania można grupować na podstawie dowolnej kolumny w widoku listy. Na przykład klikając prawym przyciskiem myszy nagłówek kolumny **stan** , a następnie klikając pozycję **Grupuj według stanu**, można zgrupować wszystkie zadania, które mają ten sam stan. Można na przykład szybko zobaczyć oczekujące zadania, aby skoncentrować się na tym, dlaczego są one zablokowane. Możesz również zwinąć grupę, która nie jest interesująca podczas sesji debugowania. W ten sam sposób można grupować według innych kolumn. Grupa może być (cofnięta) oflagowana po kliknięciu przycisku obok nagłówka grupy. Poniższa ilustracja przedstawia okno **zadania** w trybie grupowania.  
  
 ![Tryb grupowania w oknie zadań równoległych](../debugger/media/parallel-tasks-groupedmode.png "Parallel_Tasks_GroupedMode")  
  
## <a name="parent-child-view"></a>Nadrzędny widok podrzędny  
 (Ten widok jest dostępny tylko dla kodu zarządzanego). Klikając prawym przyciskiem myszy nagłówek kolumny, a następnie klikając pozycję **nadrzędny widok podrzędny**, można zmienić listę zadań na hierarchiczny widok, w którym każde zadanie podrzędne jest węzłem podrzędnym, który może być wyświetlany lub ukryty w obszarze nadrzędnym. Na poniższej ilustracji przedstawiono zadania w widoku nadrzędny-podrzędny.  
  
 ![Widok nadrzędny&#45;podrzędny w oknie zadań równoległych](../debugger/media/parallel-tasks-parentchildview.png "Parallel_Tasks_ParentChildView")  
  
## <a name="flagging-tasks"></a>Oflagowanie zadań  
 Można oflagować wątek, w którym uruchamiane jest zadanie, zaznaczając element listy zadań, a następnie wybierając **flagę** z menu kontekstowego lub klikając ikonę flagi w pierwszej kolumnie. Jeśli oflagujesz kilka zadań, Możesz sortować według kolumny flag, aby przenieść wszystkie oflagowane zadania do góry, aby można było skupić się na nich. Można również użyć okna **stosów równoległych** do wyświetlania tylko oflagowanych zadań. Pozwala to na odfiltrowanie zadań, które nie są interesujące do debugowania. Flagi nie są utrwalane między sesjami debugowania.  
  
## <a name="freezing-and-thawing-tasks"></a>Zamrażanie i odblokowywanie zadań  
 Można zablokować wątek, w którym uruchomiono zadanie, klikając prawym przyciskiem myszy element listy zadań, a następnie klikając polecenie **Zablokuj przypisany wątek**. (Jeśli zadanie jest już zamrożone, polecenie jest **odblokowanie przypisanego wątku**). Po zablokowaniu wątku ten wątek nie zostanie wykonany po przejściu przez kod po bieżącym punkcie przerwania. **Zablokuj wszystkie wątki, ale to** polecenie blokuje wszystkie wątki z wyjątkiem tego, który wykonuje element listy zadań.  
  
 Na poniższej ilustracji przedstawiono pozostałe elementy menu dla każdego zadania.  
  
 ![Menu wątku skrótu w oknie zadań równoległych](../debugger/media/parallel-tasks-contextmenu2.png "Parallel_Tasks_ContextMenu2")  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)   
 [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)   
 [Programowanie równoległe](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [środowisko uruchomieniowe współbieżności](https://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)   
 [Korzystanie z okna stosów równoległych](../debugger/using-the-parallel-stacks-window.md)   
 [Przewodnik: debugowanie aplikacji równoległych](../debugger/walkthrough-debugging-a-parallel-application.md)
