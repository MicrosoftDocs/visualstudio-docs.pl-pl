---
title: Lista zadań, środowisko, opcje — Okno dialogowe
ms.date: 03/28/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.Task_List
- VS.ToolsOptionsPages.Environment.TaskList
- VS.Environment.Task List
helpviewer_keywords:
- Token List
- tokens
- icons, in Task List
- Task List, customizing environment
- Options dialog box, Task List environment
- exclamation points
- comments, comment tasks in Task List
- tokens, and the Task List
- Task List, comment tasks
ms.assetid: 88327e04-fa3e-48db-995b-ad89e0dc4ed2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b2fc59a2f04dc30ef8b052e93fc6ffdf030e054
ms.sourcegitcommit: b14b7a938a2aba9fcce4d5e813aadf2040b0dcda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/29/2019
ms.locfileid: "58647222"
---
# <a name="options-dialog-box-environment--task-list"></a>Okno dialogowe Opcje: Środowisko \> listy zadań

Ta strona opcji pozwala na dodawanie, usuwanie i zmienianie tokenami komentarzy, które generują **listy zadań** przypomnienia. Aby wyświetlić te ustawienia, wybierz **opcje** z **narzędzia** menu, rozwiń węzeł **środowiska** folderu i wybierz polecenie **listy zadań**.

## <a name="task-list-tokens"></a>Tokeny listy zadań

Po wstawieniu komentarz w kodzie, którego tekst zaczyna się od tokenu z **listy Token**, **listy zadań** Wyświetla komentarz jako nowy wpis, zawsze wtedy, gdy plik jest otwarty do edycji. Kliknij przycisk **listy zadań** wpis, aby bezpośrednio przejść do wiersza komentarza w kodzie. Aby uzyskać więcej informacji, zobacz [korzystanie z listy zadań](../../ide/using-the-task-list.md).

List\ tokenu
Wyświetla listę tokenów i umożliwia dodawanie lub usuwanie tokeny niestandardowe. Tokeny komentarza jest uwzględniana wielkość liter w C# i C++, ale nie w języku Visual Basic.

> [!NOTE]
> Jeśli nie wpiszesz żądanego tokenu dokładnie tak, jak wygląda na to, na liście tokenów, komentarz zadania nie będą wyświetlane w **listy zadań**.

Priority\
Ustawia priorytet zadania korzystające z wybranego tokenu (niska, normalna lub wysoka). Komentarze do zadań, które zaczynają się od tego tokenu są automatycznie przypisywane wyznaczonym priorytet w **listy zadań**.

Name\
Wprowadź tutaj ciąg tokenu, a następnie kliknij przycisk **Dodaj** dodać ciąg do listy tokenów.

Add\
Włączony podczas wprowadzania nowej **nazwa**. Kliknij, aby dodać nowy ciąg tokenu przy użyciu wartościami podanymi w **nazwa** i **priorytet** pola.

Delete\
Kliknij, aby usunąć wybrany token z listy tokenów. Nie można usunąć domyślny token komentarz.

Change\
Kliknij, aby wprowadzić zmiany do istniejącego tokenu przy użyciu wartościami podanymi w **nazwa** i **priorytet** pola.

> [!NOTE]
> Nie można zmienić ani usunąć domyślny token komentarz, ale można zmienić jego priorytet.

## <a name="see-also"></a>Zobacz także

- [Korzystanie z listy zadań](../../ide/using-the-task-list.md)
- [Ustawianie zakładek w kodzie](../../ide/setting-bookmarks-in-code.md)
- [Środowisko, Opcje — okno dialogowe](../../ide/reference/environment-options-dialog-box.md)