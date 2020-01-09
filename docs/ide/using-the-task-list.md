---
title: Korzystanie z listy zadań
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: db39850350f99e6c046996f6408973cbc6543868
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594230"
---
# <a name="use-the-task-list"></a>Korzystanie z listy zadań

Użyj **Lista zadań** do śledzenia komentarzy do kodu, które używają tokenów, takich jak `TODO` i `HACK`lub tokenów niestandardowych, oraz do zarządzania skrótami, które umożliwiają bezpośrednie przejście do wstępnie zdefiniowanej lokalizacji w kodzie. Kliknij element na liście, aby przejść do jego lokalizacji w kodzie źródłowym.

> [!NOTE]
> Ten temat dotyczy programu Visual Studio w Windows. Aby uzyskać Visual Studio dla komputerów Mac, zobacz [Komentarze zadań (Visual Studio dla komputerów Mac)](/visualstudio/mac/task-comments).

## <a name="the-task-list-window"></a>Okno Lista zadań

Gdy **Lista zadań** jest otwarty, pojawia się u dołu okna aplikacji.

Aby otworzyć **Lista zadań**, wybierz **pozycję Wyświetl** > **Lista zadań**lub na klawiaturze naciśnij+**kombinację klawiszy CTRL +** **\\** ,**t**.

![okno listy zadań](../ide/media/vs2015_task_list.png)

Aby zmienić kolejność sortowania listy, wybierz nagłówek dowolnej kolumny. Aby dokładniej udoskonalić wyniki wyszukiwania, naciśnij klawisz **SHIFT** i kliknij nagłówek drugiej kolumny. Alternatywnie w menu skrótów wybierz polecenie **Sortuj według**, a następnie wybierz nagłówek. Aby dokładniej udoskonalić wyniki wyszukiwania, naciśnij klawisz **SHIFT** i wybierz drugi nagłówek.

Aby pokazać lub ukryć kolumny, w menu skrótów wybierz polecenie **Pokaż kolumny**. Wybierz kolumny, które chcesz pokazać lub ukryć.

Aby zmienić kolejność kolumn, przeciągnij dowolny nagłówek kolumny do lokalizacji, której chcesz użyć.

## <a name="user-tasks"></a>Zadania użytkownika

Funkcja zadania użytkownika została usunięta w programie Visual Studio 2015. Po otwarciu rozwiązania, które zawiera dane zadania użytkownika z Visual Studio 2013 i wcześniejszych, nie ma to zmian w danych zadania użytkownika w pliku *. suo* , ale zadania użytkownika nie są wyświetlane na liście zadań.

Jeśli chcesz nadal uzyskiwać dostęp do danych zadania użytkownika i aktualizować je, Otwórz projekt w Visual Studio 2013 i skopiuj zawartość wszystkich zadań użytkownika do preferowanego narzędzia do zarządzania projektami (na przykład Team Foundation Server).

## <a name="tokens-and-comments"></a>Tokeny i komentarze

Komentarz w kodzie poprzedzony znacznikiem komentarza i wstępnie zdefiniowany token pojawia się również w **Lista zadań**. Na przykład, poniższy komentarz C# ma trzy oddzielne części:

- Znacznik komentarza (`//`)

- Token, na przykład (`TODO`)

- Komentarz (reszta tekstu)

```csharp
// TODO: Load state from previously suspended application
```

Ponieważ `TODO` jest wstępnie zdefiniowanym tokenem, ten komentarz jest wyświetlany jako zadanie `TODO` na liście.

> [!NOTE]
> Tokeny domyślne są dostępne tylko dla języków CC++/ C#, i VB. W przypadku innych języków zapoznaj się z sekcją **tokeny niestandardowe** .

### <a name="custom-tokens"></a>{1&gt;Tokeny niestandardowe&lt;1}

Domyślnie program Visual Studio zawiera następujące tokeny: `HACK`, `TODO`, `UNDONE`i `UnresolvedMergeConflict`. Wielkość liter nie jest w nich uwzględniana. Można również utworzyć własne niestandardowe tokeny.

Aby utworzyć token niestandardowy:

1. Na **narzędzia** menu, wybierz **opcje**.

2. Otwórz folder **środowisko** , a następnie wybierz **Lista zadań**.

   Zostanie wyświetlona [Strona opcje Lista zadań](../ide/reference/task-list-environment-options-dialog-box.md) .

   ![Lista zadań programu Visual Studio](../ide/media/vs2015_task_list_options.png)

3. W polu tekstowym **Nazwa** wprowadź nazwę tokenu, na przykład **usterka**.

4. Z listy rozwijanej **priorytet** wybierz domyślny priorytet dla nowego tokenu.

5. Wybierz **Dodaj**.

> [!TIP]
> Przycisk **Dodaj** zostanie włączony po wprowadzeniu nazwy. Musisz wprowadzić nazwę przed kliknięciem przycisku **Dodaj**.

### <a name="c-todo-comments"></a>Komentarze C++ TODO

Domyślnie Komentarze do C++ zrobienia są wyświetlane w **Lista zadań**.

C++ Aby wyłączyć Komentarze z zadaniami do wykonania, w menu **Narzędzia** wybierz polecenie **Opcje** > **Edytor tekstu** > **C++ C/**  > **Widok** > **Wyliczenie komentarzy**i ustaw wartość **false**.

## <a name="shortcuts"></a>Skróty

*Skrót* jest zakładką w kodzie, który jest śledzony w **Lista zadań**. Ma inną ikonę niż zwykła Zakładka. Kliknij dwukrotnie skrót w **Lista zadań** , aby przejść do odpowiedniej lokalizacji w kodzie.

![Ikona skrótu Lista zadań programu Visual Studio](../ide/media/vs2015_task_list_bookmark.png)

### <a name="create-a-shortcut"></a>Tworzenie skrótu

Aby utworzyć skrót, Wstaw wskaźnik do kodu, w którym chcesz umieścić skrót. Wybierz **edytuj** > **zakładki** > **dodaj skrót Lista zadań** lub naciśnij+**klawisze CTRL +** **K**, **Ctrl**+**H**.

Aby nawigować przez skróty w kodzie, wybierz skrót z listy, a następnie wybierz **następne zadanie** lub **poprzednie zadanie** z menu skrótów.

## <a name="see-also"></a>Zobacz także

- [Lista zadań, środowisko, Opcje — okno dialogowe](../ide/reference/task-list-environment-options-dialog-box.md)
- [Komentarze do zadań (Visual Studio dla komputerów Mac)](/visualstudio/mac/task-comments)
