---
title: Korzystanie z okna zadań | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65684035"
---
# <a name="using-the-tasks-window"></a>Korzystanie z okna zadań
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Zadania** przypomina okna **wątków** okna, z wyjątkiem, że przedstawia informacje na temat <xref:System.Threading.Tasks.Task?displayProperty=fullName>, [task_handle](https://msdn.microsoft.com/library/b4af5b28-227d-4488-8194-0a0d039173b7), lub [WinJS.Promise ](https://msdn.microsoft.com/library/windows/apps/br211867.aspx) obiekty zamiast każdego wątku. Takie jak wątki zadania reprezentują operacje asynchroniczne, które można uruchomić jednocześnie; Jednak wiele zadań może działać na tym samym wątku. Zobacz [asynchronicznego programowania w języku JavaScript (aplikacje Windows Store)](https://msdn.microsoft.com/library/windows/apps/hh700330.aspx) Aby uzyskać więcej informacji.  
  
 W kodzie zarządzanym można używać **zadania** okna podczas pracy z <xref:System.Threading.Tasks.Task?displayProperty=fullName> obiektów lub za pomocą **await** i **async** słowa kluczowe (**Await** i **Async** w języka Visual Basic). Aby uzyskać więcej informacji o zadaniach w kodzie zarządzanym, zobacz [programowania równoległego](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d).  
  
 W kodzie natywnym można użyć **zadania** okna podczas pracy z [grupy zadań](https://msdn.microsoft.com/library/42f05ac3-2098-494a-ba84-737fcdcad077), [równoległe algorytmy](https://msdn.microsoft.com/library/045dca7b-4d73-4558-a44c-383b88a28473), [agentów asynchronicznych](https://msdn.microsoft.com/library/6cf6ccc6-87f1-4e14-af15-ea8ba58fef1a), i [zadań lekkich](https://msdn.microsoft.com/library/9aba278c-e0c9-4ede-b7c6-fedf7a365d90). Aby uzyskać więcej informacji o zadaniach w kodzie natywnym, zobacz [współbieżność środowiska wykonawczego](https://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c).  
  
 W języku JavaScript można użyć okna zadań podczas pracy z kodem .then promise.  
  
 Możesz użyć **zadania** okna zawsze wtedy, gdy wkroczenia do debugera. Dostęp na **debugowania** menu, klikając **Windows** , a następnie klikając polecenie **zadania**. Poniższa ilustracja przedstawia **zadania** okna trybu domyślnego.  
  
 ![Okno zadań równoległych](../debugger/media/parallel-tasks-window.png "Parallel_Tasks_Window")  
  
> [!NOTE]
> W kodzie zarządzanym <xref:System.Threading.Tasks.Task> , ma stan <xref:System.Threading.Tasks.TaskStatus>, <xref:System.Threading.Tasks.TaskStatus>, lub <xref:System.Threading.Tasks.TaskStatus> nie mogą być wyświetlane w oknie zadania, gdy zarządzane wątki są w stanie uśpienia lub sprzężenia.  
  
## <a name="tasks-column-information"></a>Informacje o kolumnach zadania  
 Kolumny w **zadania** okna są wyświetlane następujące dane.  
  
|Nazwa kolumny|Opis|  
|-----------------|-----------------|  
|**flagi**|Umożliwia Flagowanie zadania lub i przedstawia zadania, które są oznaczone.|  
|**Ikony**|Żółta strzałka wskazuje bieżącego zadania. Bieżące zadanie jest zadaniem najważniejsze dla bieżącego wątku.<br /><br /> Biały strzałek wskazuje zadania istotne, czyli ten, który były aktualne, gdy debuger został wywołany.<br /><br /> Ikona Wstrzymaj wskazuje zadanie, które są zablokowane przez użytkownika. Można Zablokuj i Odblokuj zadania, klikając prawym przyciskiem myszy na liście.|  
|**Identyfikator**|Liczba dostarczane przez system dla zadania. W kodzie natywnym jest to adres zadania.|  
|**Status**|Bieżący stan (zaplanowane, aktywne, prawdopodobnie zakleszczone, oczekuje lub ukończone) zadania. Zaplanowane zadanie to taki, który nie został jeszcze uruchomiony i dlatego nie ma jeszcze stos wywołań, przypisany wątek lub powiązane informacje.<br /><br /> Aktywne zadanie to taki, który był wykonywany kod przed przerwanie w debugerze.<br /><br /> Zadanie oczekujące to taki, który jest zablokowane, ponieważ trwa oczekiwanie na zdarzenie ma być zasygnalizowany, blokady mogą być wprowadzane lub inne zadanie, aby zakończyć.<br /><br /> Prawdopodobnie zakleszczone zadanie jest zadanie oczekujące, w których wątek jest zakleszczone przez inny wątek.<br /><br /> Umieść kursor nad **stan** komórki dla zadanie prawdopodobnie zakleszczone lub oczekuje, aby zobaczyć więcej informacji na temat tego bloku. **Ostrzeżenie:**  **Zadania** okna raporty zakleszczenia tylko w przypadku zablokowanych zadanie, które używa podstawowego synchronizacji, który jest obsługiwany przez przejście przez łańcuch oczekiwania (WCT). Na przykład prawdopodobnie zakleszczone <xref:System.Threading.Tasks.Task> obiektu, który używa WCT, debuger raporty **oczekujące, zakleszczone**. Prawdopodobnie zakleszczone zadania, który jest zarządzany przez środowisko uruchomieniowe współbieżności, która nie korzysta z WCT, raportów jest debugera **oczekiwania**. Aby uzyskać więcej informacji na temat WCT zobacz [oczekiwania przechodzenie łańcucha](https://msdn.microsoft.com/library/ms681622\(VS.85\).aspx).|  
|**Godzina rozpoczęcia**|Czas, w którym zadanie stały się aktywne.|  
|**Czas trwania**|Liczba sekund, które zadania była aktywna.|  
|**Czas ukończenia**|Czas, w którym zadanie jest ukończone.|  
|**Lokalizacja**|Bieżąca lokalizacja w stosie wywołań zadania. Umieść kursor nad tej komórki, aby zobaczyć cały stos wywołań dla zadania. Zaplanowane zadania nie mają wartości w tej kolumnie.|  
|**Zadanie**|Metoda początkowa i argumenty, które zostały przekazane do zadania, gdy został on utworzony.|  
|**Nadrzędny**|Identyfikator zadania, które utworzył to zadanie. Jeśli to pole jest puste, zadania jest Brak elementu nadrzędnego. Dotyczy tylko programów zarządzanych.|  
|**Wątek przypisania**|Identyfikator i nazwa wątku, na którym działa zadanie.|  
|**Status powrotu**|Stan zadania po jego zakończeniu. Wartości zwracane stan **Powodzenie**, **odwołania**, i **błąd**.|  
|**AppDomain**|Dla kodu zarządzanego, domeny aplikacji, w którym zadanie jest wykonywane.|  
|**task_group**|Dla kodu natywnego adresu [task_group](https://msdn.microsoft.com/library/b4af5b28-227d-4488-8194-0a0d039173b7) obiekt, który zaplanowane zadanie. Dla agentów asynchronicznych i zadań lekkich ta kolumna jest równa 0.|  
|Proces|Identyfikator procesu, który zadanie jest uruchomione.|  
|Stan Async|Dla kodu zarządzanego, stan zadania. Domyślnie ta kolumna jest ukryta. Aby wyświetlić tę kolumnę, otwórz menu kontekstowe dla jednego z nagłówków kolumn. Wybierz **kolumn**, **AsyncState**.|  
  
 Kliknij prawym przyciskiem myszy nagłówek kolumny, a następnie wybrać kolumny, które chcesz, możesz dodać kolumny do widoku. (Usunąć kolumny, usuwając zaznaczenie opcji). Można również zmienić kolejność kolumn, przeciągając je w lewo lub w prawo. Menu skrótów w kolumnie jest wyświetlany na poniższej ilustracji.  
  
 ![Menu Widok skrótów na liście okno zadań równoległych](../debugger/media/parallel-tasks-contextmenu.png "Parallel_Tasks_ContextMenu")  
  
## <a name="sorting-tasks"></a>Sortowanie zadania  
 Aby posortować zadania według kryteriów kolumny, kliknij nagłówek kolumny. Na przykład klikając **identyfikator** nagłówek kolumny można posortować zadania według Identyfikatora zadania: 1,2,3,4,5 i tak dalej. Aby odwrócić porządek sortowania, kliknij nagłówek kolumny ponownie. Według bieżącej kolumny i sortowania kolejności sortowania jest wskazywany przez strzałkę w kolumnie.  
  
## <a name="grouping-tasks"></a>Grupowania zadań  
 Można grupować zadania oparte na dowolną kolumnę w widoku listy. Na przykład, klikając prawym przyciskiem myszy **stan** nagłówek kolumny, a następnie klikając polecenie **grupa statusem**, można grupować wszystkie zadania, które mają ten sam stan. Szybko można na przykład, zobacz oczekujących zadań, dzięki czemu możesz skupić się na dlaczego są blokowane. Można również zwinąć grupy, która nie jest przedmiotem zainteresowania podczas sesji debugowania. W ten sam sposób można grupować według innych kolumn. Grupa może być (NZ) po prostu przez kliknięcie przycisku obok nagłówka grupy. Poniższa ilustracja przedstawia **zadania** okna w trybie zgrupowane.  
  
 ![Tryb zgrupowane w okno zadań równoległych](../debugger/media/parallel-tasks-groupedmode.png "Parallel_Tasks_GroupedMode")  
  
## <a name="parent-child-view"></a>Nadrzędny widok podrzędny  
 (W tym widoku jest dostępne tylko dla kodu zarządzanego). Kliknij prawym przyciskiem myszy nagłówek kolumny, a następnie klikając polecenie **widok podrzędny nadrzędnego**, można zmienić na liście zadań do hierarchiczny widok, w której każdy podrzędny zadanie jest podwęźle, które mogą być wyświetlane lub ukryte w jego obiektu nadrzędnego. Na poniższej ilustracji przedstawiono zadania w widoku nadrzędny podrzędny.  
  
 ![Nadrzędny&#45;widok podrzędny w okno zadań równoległych](../debugger/media/parallel-tasks-parentchildview.png "Parallel_Tasks_ParentChildView")  
  
## <a name="flagging-tasks"></a>Flagowanie zadania  
 Można flagę wątku, na liście zadań, na którym działa zadanie, wybierając zadanie, element, a następnie wybierając **flagi** z menu kontekstowego lub klikając ikonę flagi w pierwszej kolumnie. Jeśli flaga jest kilka zadań, następnie można sortować na kolumna flagi, aby wyświetlić oflagowanych zadań u góry, dzięki czemu można skupić się właśnie na nich. Można również użyć **stosów równoległych** okna, aby wyświetlić tylko oflagowane zadania. Pozwala to odfiltrować zadania, które nie jest konieczne w celu debugowania. Flagi nie są zachowywane między sesjami debugowania.  
  
## <a name="freezing-and-thawing-tasks"></a>Zawiesza się i odblokowania zadania  
 Można zamrozić wątku, na którym działa zadanie, kliknij prawym przyciskiem myszy element listy zadań, a następnie klikając polecenie **Blokuj przypisany wątek**. (Jeśli zadanie jest już zablokowany, polecenie jest **Odblokuj przypisany wątek**.) Po zablokowaniu wątku, który wątek nie zostanie wykonany po przejść przez kod po bieżącym punktu przerwania. **Zablokuj wszystkie wątki, ale ten** polecenie zawiesza się wszystkie wątki z wyjątkiem tego, który wykonuje element listy zadań.  
  
 Poniższa ilustracja przedstawia innymi elementami menu dla każdego zadania.  
  
 ![Menu skrótów wątku na liście okno zadań równoległych](../debugger/media/parallel-tasks-contextmenu2.png "Parallel_Tasks_ContextMenu2")  
  
## <a name="see-also"></a>Zobacz też  
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)   
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)   
 [Programowanie równoległe](https://msdn.microsoft.com/library/4d83c690-ad2d-489e-a2e0-b85b898a672d)   
 [Współbieżność środowiska wykonawczego](https://msdn.microsoft.com/library/874bc58f-8dce-483e-a3a1-4dcc9e52ed2c)   
 [Korzystanie z okna stosów równoległych](../debugger/using-the-parallel-stacks-window.md)   
 [Przewodnik: Debugowanie aplikacji równoległej](../debugger/walkthrough-debugging-a-parallel-application.md)
