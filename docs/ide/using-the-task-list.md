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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594230"
---
# <a name="use-the-task-list"></a>Korzystanie z listy zadań

**Użyj listy zadań,** aby śledzić komentarze `TODO` `HACK`kodu, które używają tokenów, takich jak i , lub tokeny niestandardowe, i zarządzać skrótami, które zadają bezpośrednio do wstępnie zdefiniowanej lokalizacji w kodzie. Kliknij element na liście, aby przejść do jego lokalizacji w kodzie źródłowym.

> [!NOTE]
> W tym temacie stosuje się do programu Visual Studio w systemie Windows. W przypadku programu Visual Studio dla komputerów Mac zobacz [Komentarze do zadań (Visual Studio dla komputerów Mac).](/visualstudio/mac/task-comments)

## <a name="the-task-list-window"></a>Okno Lista zadań

Gdy **lista zadań** jest otwarta, pojawia się u dołu okna aplikacji.

Aby otworzyć **listę zadań**, wybierz **pozycję Wyświetl** > **listę zadań**lub z klawiatury naciśnij klawisz **Ctrl**+**\\**,**T**.

![okno listy zadań](../ide/media/vs2015_task_list.png)

Aby zmienić kolejność sortowania listy, zaznacz nagłówek dowolnej kolumny. Aby jeszcze bardziej uściślić wyniki wyszukiwania, naciśnij **klawisz Shift** i kliknij nagłówek drugiej kolumny. Alternatywnie w menu skrótów wybierz polecenie **Sortuj według**, a następnie wybierz nagłówek. Aby jeszcze bardziej uściślić wyniki wyszukiwania, naciśnij klawisz **Shift** i wybierz drugi nagłówek.

Aby wyświetlić lub ukryć kolumny, w menu **skrótów**wybierz polecenie Pokaż kolumny . Zaznacz kolumny, które chcesz pokazać lub ukryć.

Aby zmienić kolejność kolumn, przeciągnij dowolny nagłówek kolumny do odpowiedniego miejsca.

## <a name="user-tasks"></a>Zadania użytkownika

Funkcja zadania użytkownika została usunięta w programie Visual Studio 2015. Po otwarciu rozwiązania, które ma dane zadania użytkownika z programu Visual Studio 2013 i wcześniejszych, dane zadania użytkownika w pliku *.suo* nie ma wpływu, ale zadania użytkownika nie są wyświetlane na liście zadań.

Jeśli chcesz nadal uzyskiwać dostęp do danych zadań użytkownika i aktualizować je, otwórz projekt w programie Visual Studio 2013 i skopiuj zawartość wszystkich zadań użytkownika do preferowanego narzędzia do zarządzania projektami (takiego jak Team Foundation Server).

## <a name="tokens-and-comments"></a>Tokeny i komentarze

Komentarz w kodzie poprzedzony znacznikiem komentarza i wstępnie zdefiniowanym tokenem pojawia się również na **liście zadań**. Na przykład, poniższy komentarz C# ma trzy oddzielne części:

- Znacznik komentarza`//`( )

- Token, na przykład`TODO`( )

- Komentarz (reszta tekstu)

```csharp
// TODO: Load state from previously suspended application
```

Ponieważ `TODO` jest wstępnie zdefiniowany token, ten `TODO` komentarz pojawia się jako zadanie na liście.

> [!NOTE]
> Tokeny domyślne są dostępne tylko dla języków C/C++, C#i VB. W przypadku innych języków zobacz sekcję **Tokeny niestandardowe.**

### <a name="custom-tokens"></a>Tokeny niestandardowe

Domyślnie program Visual Studio zawiera `HACK`następujące `TODO` `UNDONE`tokeny: , , i `UnresolvedMergeConflict`. Wielkość liter nie jest w nich uwzględniana. Można również utworzyć własne niestandardowe tokeny.

Aby utworzyć token niestandardowy:

1. W menu **Narzędzia** wybierz polecenie **Opcje**.

2. Otwórz folder **Środowisko,** a następnie wybierz pozycję **Lista zadań**.

   Zostanie wyświetlona [strona Opcje listy zadań.](../ide/reference/task-list-environment-options-dialog-box.md)

   ![Lista zadań programu Visual Studio](../ide/media/vs2015_task_list_options.png)

3. W polu **tekstowym Nazwa** wprowadź nazwę tokenu, na przykład **BUG**.

4. Na liście rozwijanej **Priorytet** wybierz domyślny priorytet dla nowego tokenu.

5. Wybierz **pozycję Dodaj**.

> [!TIP]
> Przycisk **Dodaj** zostanie włączony po wprowadzeniu nazwy. Przed kliknięciem przycisku **Dodaj**należy wprowadzić nazwę.

### <a name="c-todo-comments"></a>Komentarze C++ TODO

Domyślnie komentarze TODO języka C++ są wyświetlane na **liście zadań**.

Aby wyłączyć komentarze WDO języka C++ w menu **Narzędzia** wybierz polecenie **Opcje** > **Edytor** > tekstu**C/C++** > Wyświetl**wyliczanie****View** > zadań komentarza i ustaw wartość **false**.

## <a name="shortcuts"></a>Skróty

*Skrót* to zakładka w kodzie śledzonym na **liście zadań**. Ma inną ikonę niż zwykła zakładka. Kliknij dwukrotnie skrót na **liście zadań,** aby przejść do odpowiedniej lokalizacji w kodzie.

![Ikona skrótu listy zadań programu Visual Studio](../ide/media/vs2015_task_list_bookmark.png)

### <a name="create-a-shortcut"></a>Tworzenie skrótu

Aby utworzyć skrót, wstaw wskaźnik do kodu, w którym chcesz umieścić skrót. Wybierz **pozycję Edytuj** > **zakładki** > Dodaj skrót listy**zadań** lub naciśnij **klawisze Ctrl**+**K**, **Ctrl**+**H**.

Aby poruszać się po skrótach w kodzie, wybierz skrót na liście, a następnie wybierz polecenie **Następne zadanie** lub **Poprzednie zadanie** z menu skrótów.

## <a name="see-also"></a>Zobacz też

- [Okno dialogowe Lista zadań, Środowisko, Opcje](../ide/reference/task-list-environment-options-dialog-box.md)
- [Komentarze do zadań (Visual Studio dla komputerów Mac)](/visualstudio/mac/task-comments)
