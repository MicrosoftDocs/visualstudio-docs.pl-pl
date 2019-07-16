---
title: Korzystanie z listy zadań | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
ms.assetid: f46a75a8-47b3-4cb6-bb59-b72e3356a664
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9c9526b2deaafb36e991afce6d29ace47f8564ba
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68179353"
---
# <a name="using-the-task-list"></a>Korzystanie z listy zadań
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Użyj **listy zadań** do śledzenia komentarzy do kodu, które używać tokenów, takich jak `TODO` i `HACK`, lub tokeny niestandardowe i zarządzać skróty, które powodują przejście bezpośrednio do wstępnie zdefiniowanej lokalizacji w kodzie. Kliknij element na liście, aby przejść do jego lokalizacji w kodzie źródłowym.  
  
 W tym temacie:  
  
- [W oknie Lista zadań](../ide/using-the-task-list.md#taskListWindow)  
  
- [Zadania użytkownika](../ide/using-the-task-list.md#userTasks)  
  
- [Tokeny i komentarze](../ide/using-the-task-list.md#tokensComments)  
  
- [Tokeny niestandardowe](../ide/using-the-task-list.md#customTokens)  
  
- [Komentarze C++ TODO](../ide/using-the-task-list.md#cppComments)  
  
- [Skróty](../ide/using-the-task-list.md#shortcuts)  
  
## <a name="taskListWindow"></a> W oknie Lista zadań  
 Gdy **listy zadań** jest otwarty, wygląda na to, w dolnej części okna aplikacji.  
  
#### <a name="to-open-the-task-list"></a>Aby otworzyć Listę zadań  
  
- Na **widoku** menu, wybierz **listy zadań** (klawiatury: CTRL+\\, T).  
  
     ![Okno listy zadań](../ide/media/vs2015-task-list.png "vs2015_task_list")  
  
#### <a name="to-change-the-sort-order-of-the-list"></a>Aby zmienić kolejność sortowania listy  
  
- Kliknij nagłówek dowolnej kolumny. Aby dalej zawęzić wyniki wyszukiwania, naciśnij klawisz Shift i kliknij nagłówek drugiej kolumny.  
  
     Alternatywnie, w menu skrótów wybierz **sortować według**i wybierz nagłówek. Aby dalej zawęzić wyniki wyszukiwania, naciśnij klawisz Shift i wybierz drugi nagłówek.  
  
#### <a name="to-show-or-hide-columns"></a>Aby pokazać lub ukryć kolumny  
  
- W menu skrótów wybierz **Pokaż kolumny**. Wybierz kolumny, które chcesz pokazać lub ukryć.  
  
#### <a name="to-change-the-order-of-the-columns"></a>Aby zmienić kolejność kolumn  
  
- Przeciągnij dowolny nagłówek kolumny do żądanej lokalizacji.  
  
## <a name="userTasks"></a> Zadania użytkownika  
 Funkcja zadania użytkownika zostało usunięte w programie Visual Studio 2015. Po otwarciu rozwiązania, który zawiera dane zadania użytkownika z programu Visual Studio 2013 wcześniej w programie Visual Studio 2015 danych zadania użytkownika w pliku .suo nie zostaną zmienione, a zadania użytkownika nie będą wyświetlane na liście zadań.  
  
 Jeśli chcesz w dalszym ciągu dostęp i uaktualniają danych zadania użytkownika, należy otworzyć projekt w programie Visual Studio 2013 i skopiuj zawartość każdego zadania użytkownika do narzędzia do zarządzania projektem preferowanych usługi (takie jak Team Foundation Server).  
  
## <a name="tokensComments"></a> Tokeny i komentarze  
 Komentarz w kodzie poprzedzony przez znacznik komentarza i wstępnie zdefiniowany token pojawi się również w **listy zadań** okna. Na przykład, poniższy komentarz C# ma trzy oddzielne części:  
  
- Znacznik komentarza (`//`)  
  
- Token, na przykład (`TODO`)  
  
- Komentarz (reszta tekstu)  
  
```  
// TODO: Load state from previously suspended application  
```  
  
 Ponieważ `TODO` jest wstępnie zdefiniowany token, ten komentarz jest wyświetlany jako `TODO` zadanie na liście.  
  
### <a name="customTokens"></a> Tokeny niestandardowe  
 Domyślnie środowisko Visual Studio zawiera następujące tokeny: HACK, TODO, COFNIĘTA, NALEŻY PAMIĘTAĆ. Nie są z uwzględnieniem wielkości liter.  
  
 Można również utworzyć własne niestandardowe tokeny.  
  
##### <a name="to-create-a-custom-token"></a>Aby utworzyć niestandardowy token  
  
1. Na **narzędzia** menu, wybierz **opcje**.  
  
2. Otwórz **środowiska** folder, a następnie wybierz **listy zadań**.  
  
     [Okno dialogowe Opcje listy zadań, środowisko,](../ide/reference/task-list-environment-options-dialog-box.md) jest wyświetlana.  
  
     ![Lista zadań w programie Visual Studio](../ide/media/vs2015-task-list-options.png "vs2015_task_list_options")  
  
3. W **tokenów** kategorii w **nazwa** polu tekstowym wprowadź nazwę tokenu, na przykład "błąd".  
  
4. W **priorytet** listy rozwijanej wybierz domyślny priorytet dla nowego tokenu. Wybierz **Dodaj** przycisku.  
  
### <a name="cppComments"></a> Komentarze C++ TODO  
 Domyślnie, komentarze C++ TODO są wyświetlane w **listy zadań** okna. Możesz zmienić to zachowanie.  
  
##### <a name="to-turn-off-c-todo-comments"></a>Aby wyłączyć komentarze C++ TODO  
  
1. Na **narzędzia** przejdź do menu **opcje &#124; edytora tekstów &#124; C/C++ &#124; widoku &#124; Wylicz zadania komentarza** i ustaw wartość false.  
  
2. W **opcje** po otwarciu okna dialogowego **edytora tekstów**.  
  
3. W obszarze **C/C++** , wybierz **widoku**, a następnie ustaw **Wylicz zadania komentarza** do **False**.  
  
## <a name="shortcuts"></a> Skróty  
 A *skrótów* to zakładka w kodzie, który jest śledzona w **listy zadań**; ma inną ikonę niż regularne zakładki. Kliknij dwukrotnie skrót **listy zadań** można przejść do odpowiedniej lokalizacji w kodzie.  
  
 ![Ikona skrót listy zadań programu Visual Studio](../ide/media/vs2015-task-list-bookmark.png "vs2015_task_list_bookmark")  
  
#### <a name="to-create-a-shortcut"></a>Aby utworzyć skrót  
  
- Wstaw wskaźnik do kodu, w którym chcesz umieścić skrót. Wybierz **Edytuj &#124; zakładki &#124; Dodaj skrót do listy zadań** lub naciśnij (klawiatury: CTRL + K, Ctrl + H).  
  
     Do nawigowania w skrótach w kodzie, wybierz skrót na liście, a następnie wybierz **następne zadanie** lub **poprzednie zadanie** z menu skrótów.  
  
## <a name="see-also"></a>Zobacz też  
 [Lista zadań, Środowisko, Opcje — okno dialogowe](../ide/reference/task-list-environment-options-dialog-box.md)
