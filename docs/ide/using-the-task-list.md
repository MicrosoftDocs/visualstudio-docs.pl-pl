---
title: Korzystanie z listy zadań
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- TaskListWindow
- VS.TaskList
- tasklist
helpviewer_keywords:
- task list
- Visual Studio, task list
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0b30abf88a00934670ba2d34873ad883c833aae8
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53831105"
---
# <a name="use-the-task-list"></a>Korzystanie z listy zadań

Użyj **listy zadań** do śledzenia komentarzy do kodu, które używać tokenów, takich jak `TODO` i `HACK`, lub tokeny niestandardowe oraz zarządzania skrótami, które przejście bezpośrednio do wstępnie zdefiniowanej lokalizacji w kodzie. Kliknij element na liście, aby przejść do jego lokalizacji w kodzie źródłowym.

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Dla programu Visual Studio dla komputerów Mac, zobacz [zadań komentarzy (Visual Studio dla komputerów Mac)](/visualstudio/mac/task-comments).

## <a name="the-task-list-window"></a>Okno Lista zadań

Gdy **listy zadań** jest otwarty, wygląda na to, w dolnej części okna aplikacji.

Aby otworzyć **listy zadań**, wybierz opcję **widoku** > **listy zadań**, lub naciśnij klawisze klawiatury **Ctrl** + **\\**,**T**.

![okno listy zadań](../ide/media/vs2015_task_list.png)

Aby zmienić kolejność sortowania listy, wybierz nagłówek dowolnej kolumny. Aby dalej zawęzić wyniki wyszukiwania, naciśnij klawisz **Shift** i kliknij nagłówek drugiej kolumny. Alternatywnie w menu skrótów wybierz **sortować według**, a następnie wybierz nagłówek. Aby dalej zawęzić wyniki wyszukiwania, naciśnij klawisz **Shift** i wybierz drugi nagłówek.

Aby pokazać lub ukryć kolumny, w menu skrótów wybierz **Pokaż kolumny**. Wybierz kolumny, które chcesz pokazać lub ukryć.

Aby zmienić kolejność kolumn, przeciągnij dowolny nagłówek kolumny do dowolnej lokalizacji.

## <a name="user-tasks"></a>Zadania użytkownika

Funkcja zadania użytkownika został usunięty w programie Visual Studio 2015. Po otwarciu rozwiązania, na które ma dane zadania użytkownika z programu Visual Studio 2013 lub starszej, użytkownik zadań danych w Twojej *.suo* nie wpływa na plik, ale zadania użytkownika nie są wyświetlane na liście zadań.

Jeśli chcesz w dalszym ciągu uzyskać dostęp i zaktualizować swoje dane zadanie, otwórz projekt w programie Visual Studio 2013 i skopiuj zawartość każdego zadania użytkownika do narzędzia do zarządzania projektem preferowanych usługi (takie jak Team Foundation Server).

## <a name="tokens-and-comments"></a>Tokeny i komentarze

Komentarz w kodzie poprzedzony przez znacznik komentarza i wstępnie zdefiniowany token pojawi się również w **listy zadań**. Na przykład, poniższy komentarz C# ma trzy oddzielne części:

- Znacznik komentarza (`//`)

- Token, na przykład (`TODO`)

- Komentarz (reszta tekstu)

```csharp
// TODO: Load state from previously suspended application
```

Ponieważ `TODO` jest wstępnie zdefiniowany token, ten komentarz jest wyświetlany jako `TODO` zadanie na liście.

### <a name="custom-tokens"></a>Tokeny niestandardowe

Domyślnie program Visual Studio zawiera następujące tokeny: `HACK`, `TODO`, `UNDONE`, i `UnresolvedMergeConflict`. Nie są one uwzględniana wielkość liter. Można również utworzyć własne niestandardowe tokeny.

Aby utworzyć niestandardowy token:

1. Na **narzędzia** menu, wybierz **opcje**.

2. Otwórz **środowiska** folder, a następnie wybierz **listy zadań**.

   [Strona Opcje listy zadań](../ide/reference/task-list-environment-options-dialog-box.md) jest wyświetlana.

   ![Lista zadań w programie Visual Studio](../ide/media/vs2015_task_list_options.png)

3. W **nazwa** tekst na przykład wprowadź nazwę tokenu, **USTERKI**.

4. W **priorytet** listy rozwijanej wybierz domyślny priorytet dla nowego tokenu.

5. Wybierz **Dodaj**.

### <a name="c-todo-comments"></a>Komentarze C++ TODO

Domyślnie, komentarze C++ TODO są wyświetlane w **listy zadań**.

Aby wyłączyć komentarze C++ TODO na **narzędzia** menu, wybierz **opcje** > **edytora tekstów** > **C/C++**  >  **Widoku** > **Wylicz zadania komentarza**, a następnie ustaw wartość **false**.

## <a name="shortcuts"></a>Skróty

A *skrótów* to zakładka w kodzie, który jest śledzona w **listy zadań**. Ma inną ikonę niż regularne zakładki. Kliknij dwukrotnie skrót **listy zadań** można przejść do odpowiedniej lokalizacji w kodzie.

![Ikona skrót listy zadań programu Visual Studio](../ide/media/vs2015_task_list_bookmark.png)

### <a name="create-a-shortcut"></a>Utwórz skrót

Aby utworzyć skrót, Wstaw wskaźnik do kodu, w którym chcesz umieścić skrót. Wybierz **Edytuj** > **zakładki** > **Dodaj skrót do listy zadań** lub naciśnij **Ctrl** + **K**, **Ctrl**+**H**.

Do nawigowania w skrótach w kodzie, wybierz skrót na liście, a następnie wybierz **następne zadanie** lub **poprzednie zadanie** z menu skrótów.

## <a name="see-also"></a>Zobacz także

- [Lista, środowisko, opcje, okno dialogowe zadań](../ide/reference/task-list-environment-options-dialog-box.md)
- [Komentarze do zadań (Visual Studio dla komputerów Mac)](/visualstudio/mac/task-comments)
