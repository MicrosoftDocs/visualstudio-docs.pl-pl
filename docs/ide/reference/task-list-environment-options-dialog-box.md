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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 05c337a6e809f85490e651fecf405b44e9f28930
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75592012"
---
# <a name="options-dialog-box-environment--task-list"></a>Okno dialogowe \> Opcje: Lista zadań środowiska

Ta strona Opcje umożliwia dodawanie, usuwanie i zmienianie tokenów komentarzy, które generują przypomnienia **o liście zadań.** Aby wyświetlić te ustawienia, wybierz polecenie **Opcje** z menu **Narzędzia,** rozwiń folder **Środowisko** i wybierz pozycję **Lista zadań**.

## <a name="task-list-tokens"></a>Tokeny listy zadań

Po wstawieniu komentarza do kodu, którego tekst zaczyna się od tokenu z **listy Token,** **lista zadań** wyświetla komentarz jako nowy wpis, gdy plik jest otwierany do edycji. Kliknij wpis **Lista zadań,** aby przejść bezpośrednio do wiersza komentarza w kodzie. Aby uzyskać więcej informacji, zobacz [Korzystanie z listy zadań](../../ide/using-the-task-list.md).

Lista tokenów\
Wyświetla listę tokenów i umożliwia dodawanie lub usuwanie tokenów niestandardowych. Tokeny komentarzy są rozróżniane wielkość liter w językach C# i C++, ale nie w języku Visual Basic.

> [!NOTE]
> Jeśli żądany token nie zostanie wpisany dokładnie tak, jak pojawia się na liście tokenów, zadanie komentarza nie będzie wyświetlane na **liście zadań**.

Priorytet\
Ustawia priorytet zadań, które używają wybranego tokenu (niski, normalny lub wysoki). Komentarze zadań, które zaczynają się od tego tokenu, są automatycznie przypisywane wyznaczonemu priorytetowi na **liście zadań**.

Nazwa\
Wprowadź ciąg tokenu w tym miejscu, a następnie kliknij przycisk **Dodaj,** aby dodać ciąg do listy tokenów.

Dodaj\
Włączono po wprowadzeniu nowej **nazwy**. Kliknij, aby dodać nowy ciąg tokenu przy użyciu wartości wprowadzonych w polach **Nazwa** i **Priorytet.**

Usuń\
Kliknij, aby usunąć wybrany token z listy tokenów. Nie można usunąć domyślnego tokenu komentarza.

Zmień\
Kliknij, aby wprowadzić zmiany w istniejącym tokenie przy użyciu wartości wprowadzonych w polach **Nazwa** i **Priorytet.**

> [!NOTE]
> Nie można zmienić nazwy lub usunąć domyślnego tokenu komentarza, ale można zmienić jego poziom priorytetu.

## <a name="see-also"></a>Zobacz też

- [Korzystanie z listy zadań](../../ide/using-the-task-list.md)
- [Zakładki Sett w kodzie](../../ide/setting-bookmarks-in-code.md)
