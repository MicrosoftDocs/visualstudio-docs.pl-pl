---
title: Korzystanie z Lista zadań | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f7537c3007f54480874047f52f186996cf663508
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656410"
---
# <a name="using-the-task-list"></a>Korzystanie z listy zadań
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Użyj **Lista zadań** do śledzenia komentarzy do kodu, które używają tokenów, takich jak `TODO` i `HACK` lub tokenów niestandardowych, oraz do zarządzania skrótami, które przeprowadziją bezpośrednio do wstępnie zdefiniowanej lokalizacji w kodzie. Kliknij element na liście, aby przejść do jego lokalizacji w kodzie źródłowym.

 W tym temacie:

- [Okno Lista zadań](../ide/using-the-task-list.md#taskListWindow)

- [Zadania użytkownika](../ide/using-the-task-list.md#userTasks)

- [Tokeny i Komentarze](../ide/using-the-task-list.md#tokensComments)

- [Tokeny niestandardowe](../ide/using-the-task-list.md#customTokens)

- [C++Komentarze do zrobienia](../ide/using-the-task-list.md#cppComments)

- [Skróty](../ide/using-the-task-list.md#shortcuts)

## <a name="taskListWindow"></a>Okno Lista zadań
 Gdy **Lista zadań** jest otwarty, pojawia się u dołu okna aplikacji.

#### <a name="to-open-the-task-list"></a>Aby otworzyć Listę zadań

- W menu **Widok** wybierz **Lista zadań** (klawiatura: Ctrl + \\, t).

     ![Okno Lista zadań](../ide/media/vs2015-task-list.png "vs2015_task_list")

#### <a name="to-change-the-sort-order-of-the-list"></a>Aby zmienić kolejność sortowania listy

- Kliknij nagłówek dowolnej kolumny. Aby dalej zawęzić wyniki wyszukiwania, naciśnij klawisz Shift i kliknij nagłówek drugiej kolumny.

     Alternatywnie w menu skrótów wybierz polecenie **Sortuj według**i wybierz nagłówek. Aby dalej zawęzić wyniki wyszukiwania, naciśnij klawisz Shift i wybierz drugi nagłówek.

#### <a name="to-show-or-hide-columns"></a>Aby pokazać lub ukryć kolumny

- W menu skrótów wybierz polecenie **Pokaż kolumny**. Wybierz kolumny, które chcesz pokazać lub ukryć.

#### <a name="to-change-the-order-of-the-columns"></a>Aby zmienić kolejność kolumn

- Przeciągnij dowolny nagłówek kolumny do żądanej lokalizacji.

## <a name="userTasks"></a>Zadania użytkownika
 Funkcja zadania użytkownika została usunięta w programie Visual Studio 2015. Po otwarciu rozwiązania, które zawiera dane zadania użytkownika z Visual Studio 2013 i wcześniejszej wersji programu Visual Studio 2015, nie wpłynie to na dane zadania użytkownika w pliku. suo, ale zadania użytkownika nie będą wyświetlane na liście zadań.

 Aby nadal uzyskiwać dostęp do danych zadania użytkownika i aktualizować je, należy otworzyć projekt w Visual Studio 2013 i skopiować zawartość wszystkich zadań użytkownika do preferowanego narzędzia do zarządzania projektami (na przykład Team Foundation Server).

## <a name="tokensComments"></a>Tokeny i Komentarze
 Komentarz w kodzie poprzedzony znacznikiem komentarza i wstępnie zdefiniowany token zostanie również wyświetlony w oknie **Lista zadań** . Na przykład, poniższy komentarz C# ma trzy oddzielne części:

- Znacznik komentarza (`//`)

- Token, na przykład (`TODO`)

- Komentarz (reszta tekstu)

```
// TODO: Load state from previously suspended application
```

 Ponieważ `TODO` jest wstępnie zdefiniowanym tokenem, ten komentarz jest wyświetlany jako zadanie `TODO` na liście.

### <a name="customTokens"></a>Tokeny niestandardowe
 Domyślnie program Visual Studio zawiera następujące tokeny: haker, czynność do wykonania, cofnięta, Uwaga. Nie jest uwzględniana wielkość liter.

 Można również utworzyć własne niestandardowe tokeny.

##### <a name="to-create-a-custom-token"></a>Aby utworzyć niestandardowy token

1. W menu **Narzędzia** wybierz polecenie **Opcje**.

2. Otwórz folder **środowisko** , a następnie wybierz **Lista zadań**.

     Zostanie wyświetlone okno [dialogowe Lista zadań, środowisko, opcje](../ide/reference/task-list-environment-options-dialog-box.md) .

     ![Lista zadań programu Visual Studio](../ide/media/vs2015-task-list-options.png "vs2015_task_list_options")

3. W kategorii **tokeny** w polu tekstowym **Nazwa** wprowadź nazwę tokenu, na przykład "Usterka".

4. Z listy rozwijanej **priorytet** wybierz domyślny priorytet dla nowego tokenu. Wybierz przycisk **Dodaj** .

### <a name="cppComments"></a>C++ Komentarze do zrobienia
 Komentarze do C++ zrobienia są domyślnie wyświetlane w oknie **Lista zadań** . Można zmienić to zachowanie.

##### <a name="to-turn-off-c-todo-comments"></a>C++ Aby wyłączyć Komentarze do wykonania

1. W menu **Narzędzia** przejdź do pozycji  **&#124; opcje &#124; Edytor tekstu CC++ &#124; /Wyświetl &#124; Wyliczenie komentarzy zadania** i ustaw wartość na false.

2. W oknie dialogowym **Opcje** Otwórz **Edytor tekstu**.

3. W obszarze **CC++/** , wybierz pozycję **Widok**, a następnie ustaw polecenie **Wylicz Komentarze** na **wartość FAŁSZ**.

## <a name="shortcuts"></a>Skróty
 *Skrót* jest zakładką w kodzie, który jest śledzony w **Lista zadań**; ma inną ikonę niż zwykła Zakładka. Kliknij dwukrotnie skrót w **Lista zadań** , aby przejść do odpowiedniej lokalizacji w kodzie.

 ![Ikona skrótu Lista zadań programu Visual Studio](../ide/media/vs2015-task-list-bookmark.png "vs2015_task_list_bookmark")

#### <a name="to-create-a-shortcut"></a>Aby utworzyć skrót

- Wstaw wskaźnik do kodu, w którym chcesz umieścić skrót. Wybierz **pozycję &#124; edytuj &#124; zakładki Dodaj Lista zadań skrót** lub naciśnij klawisz (klawiatura: CTRL + K, CTRL + H).

     Aby nawigować przez skróty w kodzie, wybierz skrót z listy, a następnie wybierz **następne zadanie** lub **poprzednie zadanie** z menu skrótów.

## <a name="see-also"></a>Zobacz też
 [Lista zadań, Środowisko, Opcje — okno dialogowe](../ide/reference/task-list-environment-options-dialog-box.md)
