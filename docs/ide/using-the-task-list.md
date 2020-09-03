---
title: Korzystanie z listy zadań
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: abd6d73c7b312cf00062307370ba2f7aebe6694e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85768620"
---
# <a name="use-the-task-list"></a>Korzystanie z listy zadań

Użyj **Lista zadań** do śledzenia komentarzy do kodu, które używają tokenów, takich jak `TODO` i `HACK` , lub tokenów niestandardowych, oraz do zarządzania skrótami, które przełączeją bezpośrednio do wstępnie zdefiniowanej lokalizacji w kodzie. Kliknij element na liście, aby przejść do jego lokalizacji w kodzie źródłowym.

> [!NOTE]
> Ten temat ma zastosowanie do programu Visual Studio w systemie Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [Komentarze zadań (Visual Studio dla komputerów Mac)](/visualstudio/mac/task-comments).

## <a name="the-task-list-window"></a>Okno Lista zadań

Gdy **Lista zadań** jest otwarty, pojawia się u dołu okna aplikacji.

Aby otworzyć **Lista zadań**, wybierz pozycję **Wyświetl**  >  **Lista zadań**lub na klawiaturze naciśnij klawisz **Ctrl** + **\\** ,**T**.

![okno listy zadań](../ide/media/vs2015_task_list.png)

Aby zmienić kolejność sortowania listy, wybierz nagłówek dowolnej kolumny. Aby dokładniej udoskonalić wyniki wyszukiwania, naciśnij klawisz **SHIFT** i kliknij nagłówek drugiej kolumny. Alternatywnie w menu skrótów wybierz polecenie **Sortuj według**, a następnie wybierz nagłówek. Aby dokładniej udoskonalić wyniki wyszukiwania, naciśnij klawisz **SHIFT** i wybierz drugi nagłówek.

Aby pokazać lub ukryć kolumny, w menu skrótów wybierz polecenie **Pokaż kolumny**. Wybierz kolumny, które chcesz pokazać lub ukryć.

Aby zmienić kolejność kolumn, przeciągnij dowolny nagłówek kolumny do lokalizacji, której chcesz użyć.

## <a name="user-tasks"></a>Zadania użytkownika

Funkcja zadania użytkownika została usunięta w programie Visual Studio 2015. Po otwarciu rozwiązania, które zawiera dane zadania użytkownika z Visual Studio 2013 i wcześniejszych, nie ma to zmian w danych zadania użytkownika w pliku *. suo* , ale zadania użytkownika nie są wyświetlane na liście zadań.

Jeśli chcesz nadal uzyskiwać dostęp do danych zadania użytkownika i aktualizować je, Otwórz projekt w Visual Studio 2013 i skopiuj zawartość wszystkich zadań użytkownika do preferowanego narzędzia do zarządzania projektami (na przykład Team Foundation Server).

## <a name="tokens-and-comments"></a>Tokeny i komentarze

Komentarz w kodzie poprzedzony znacznikiem komentarza i wstępnie zdefiniowany token pojawia się również w **Lista zadań**. Na przykład, poniższy komentarz C# ma trzy oddzielne części:

- Znacznik komentarza ( `//` )

- Token, na przykład ( `TODO` )

- Komentarz (reszta tekstu)

```csharp
// TODO: Load state from previously suspended application
```

Ponieważ `TODO` jest wstępnie zdefiniowanym tokenem, ten komentarz jest wyświetlany jako `TODO` zadanie na liście.

> [!NOTE]
> Tokeny domyślne są dostępne tylko dla języków C/C++, C# i VB. W przypadku innych języków zapoznaj się z sekcją **tokeny niestandardowe** .

### <a name="custom-tokens"></a>Tokeny niestandardowe

Domyślnie program Visual Studio zawiera następujące tokeny: `HACK` , `TODO` , `UNDONE` i `UnresolvedMergeConflict` . Wielkość liter nie jest w nich uwzględniana. Można również utworzyć własne niestandardowe tokeny.

Aby utworzyć token niestandardowy:

1. W menu **Narzędzia** wybierz polecenie **Opcje**.

2. Otwórz folder **środowisko** , a następnie wybierz **Lista zadań**.

   Zostanie wyświetlona [Strona opcje Lista zadań](../ide/reference/task-list-environment-options-dialog-box.md) .

   ![Lista zadań programu Visual Studio](../ide/media/vs2015_task_list_options.png)

3. W polu tekstowym **Nazwa** wprowadź nazwę tokenu, na przykład **usterka**.

4. Z listy rozwijanej **priorytet** wybierz domyślny priorytet dla nowego tokenu.

5. Wybierz pozycję **Dodaj**.

> [!TIP]
> Przycisk **Dodaj** zostanie włączony po wprowadzeniu nazwy. Musisz wprowadzić nazwę przed kliknięciem przycisku **Dodaj**.

### <a name="c-todo-comments"></a>Komentarze C++ TODO

Domyślnie Komentarze do zrobienia w języku C++ są wyświetlane w **Lista zadań**.

Aby wyłączyć Komentarze do wykonania w języku C++, w menu **Narzędzia** wybierz polecenie **Opcje**  >  **Edytor tekstu**  >  **C/C++**  >  **Wyświetl**  >  **Wyliczenie komentarzy zadania**i ustaw wartość **false**.

## <a name="shortcuts"></a>Skróty

*Skrót* jest zakładką w kodzie, który jest śledzony w **Lista zadań**. Ma inną ikonę niż zwykła Zakładka. Kliknij dwukrotnie skrót w **Lista zadań** , aby przejść do odpowiedniej lokalizacji w kodzie.

![Ikona skrótu Lista zadań programu Visual Studio](../ide/media/vs2015_task_list_bookmark.png)

### <a name="create-a-shortcut"></a>Tworzenie skrótu

Aby utworzyć skrót, Wstaw wskaźnik do kodu, w którym chcesz umieścić skrót. Wybierz pozycję **Edytuj**  >  **zakładki**  >  **Dodaj Lista zadań skrót** lub naciśnij **klawisze CTRL** + **K**, **Ctrl** + **H**.

Aby nawigować przez skróty w kodzie, wybierz skrót z listy, a następnie wybierz **następne zadanie** lub **poprzednie zadanie** z menu skrótów.

## <a name="see-also"></a>Zobacz też

- [Lista zadań, środowisko, Opcje — okno dialogowe](../ide/reference/task-list-environment-options-dialog-box.md)
- [Komentarze do zadań (Visual Studio dla komputerów Mac)](/visualstudio/mac/task-comments)
