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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f2d0ba45ffea940ddb57a6da1e6df55e3da8867b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72644858"
---
# <a name="options-dialog-box-environment--task-list"></a>Opcje — okno dialogowe: \> środowiska Lista zadań

Ta strona opcji pozwala dodawać, usuwać i zmieniać tokeny komentarza generujące **Lista zadań** przypomnień. Aby wyświetlić te ustawienia, wybierz **Opcje** z menu **Narzędzia** , rozwiń folder **środowisko** i wybierz **Lista zadań**.

## <a name="task-list-tokens"></a>Tokeny Lista zadań

Po wstawieniu komentarza do kodu, którego tekst zaczyna się od tokenu z **listy tokenów**, **Lista zadań** wyświetla komentarz jako nowy wpis za każdym razem, gdy plik zostanie otwarty do edycji. Kliknij wpis **Lista zadań** , aby przejść bezpośrednio do wiersza komentarza w kodzie. Aby uzyskać więcej informacji, zobacz [używanie Lista zadań](../../ide/using-the-task-list.md).

Lista tokenów \
Wyświetla listę tokenów i umożliwia dodawanie lub usuwanie tokenów niestandardowych. W tokenach komentarzy jest rozróżniana wielkość liter w C# i C++, ale nie w Visual Basic.

> [!NOTE]
> Jeśli żądany token nie zostanie wpisany dokładnie tak, jak pojawia się na liście tokenów, zadanie komentarza nie będzie wyświetlane w **Lista zadań**.

Priorytet
Ustawia priorytet zadań, które używają wybranego tokenu (niska, normalna lub wysoka). Komentarze do zadań zaczynające się od tego tokenu są automatycznie przypisywane przez wyznaczony priorytet w **Lista zadań**.

Nazwij
Wprowadź ciąg tokenu tutaj, a następnie kliknij przycisk **Dodaj** , aby dodać ciąg do listy tokenów.

Dodana
Włączone po wprowadzeniu nowej **nazwy**. Kliknij, aby dodać nowy ciąg tokenu przy użyciu wartości wprowadzonych w polach **Nazwa** i **priorytet** .

Usunięty
Kliknij, aby usunąć wybrany token z listy tokenów. Nie można usunąć domyślnego tokenu komentarza.

Stąp
Kliknij, aby wprowadzić zmiany w istniejącym tokenie przy użyciu wartości wprowadzonych w polach **Nazwa** i **priorytet** .

> [!NOTE]
> Nie można zmienić ani usunąć domyślnego tokenu komentarza, ale można zmienić jego poziom priorytetu.

## <a name="see-also"></a>Zobacz także

- [Korzystanie z listy zadań](../../ide/using-the-task-list.md)
- [Ustawien zakładek w kodzie](../../ide/setting-bookmarks-in-code.md)