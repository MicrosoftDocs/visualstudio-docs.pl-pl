---
title: Lista zadań, środowisko, Opcje — okno dialogowe | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Environment.Task_List
- VS.ToolsOptionsPag.Environment.Task_List
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
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72e5f82fa3ca4b7ca909ee07e5b77a31b3e20879
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650966"
---
# <a name="task-list-environment-options-dialog-box"></a>Lista zadań, środowisko, opcje — Okno dialogowe
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ta strona opcji pozwala dodawać, usuwać i zmieniać tokeny komentarza generujące **Lista zadań** przypomnień. Aby wyświetlić te ustawienia, wybierz **Opcje** z menu **Narzędzia** , rozwiń folder **środowisko** i wybierz **Lista zadań**.

## <a name="task-list-options"></a>Opcje Lista zadań
 Po wybraniu przycisku Potwierdź usunięcie zadań zostanie wyświetlone okno komunikatu, gdy zadanie użytkownika zostanie usunięte z **Lista zadań**, co pozwoli na potwierdzenie usunięcia. Ta opcja jest domyślnie wybrana.

> [!NOTE]
> Aby usunąć komentarz do zadania, Użyj linku, aby znaleźć komentarz, a następnie usuń go z kodu.

 Pokaż nazwy plików tylko wtedy, gdy zaznaczone, kolumna **plik** **Lista zadań** wyświetla tylko nazwy plików do edycji, a nie pełne ścieżki.

## <a name="tokens"></a>Tokeny
 Po wstawieniu komentarza do kodu, którego tekst zaczyna się od tokenu z **listy tokenów**, **Lista zadań** wyświetla komentarz jako nowy wpis za każdym razem, gdy plik zostanie otwarty do edycji. Możesz kliknąć ten **Lista zadań** wpis, aby przejść bezpośrednio do wiersza komentarza w kodzie. Aby uzyskać więcej informacji, zobacz [używanie Lista zadań](../../ide/using-the-task-list.md).

 Lista tokenów wyświetla listę tokenów i umożliwia dodawanie lub usuwanie tokenów niestandardowych. Tokeny komentarzy są rozróżniane wielkości C# liter w C++wizualizacji i wizualizacji, ale nie w Visual Basic.

> [!NOTE]
> Jeśli nie wpiszesz żądanego tokenu dokładnie tak, jak pojawia się na **liście tokenów**, zadanie komentarza nie będzie wyświetlane w **Lista zadań**.

 Priorytet ustawia priorytet zadań, które używają wybranego tokenu. Komentarze do zadań zaczynające się od tego tokenu są automatycznie przypisywane przez wyznaczony priorytet w **Lista zadań**.

 Nazwa wprowadź ciąg tokenu. Spowoduje to włączenie przycisku **Dodaj** . Przy **dodawaniu**ten ciąg zostanie uwzględniony na **liście tokenów**, a Komentarze zaczynające się od tej nazwy będą wyświetlane w **Lista zadań**.

 Dodaj włączone po wprowadzeniu nowej **nazwy**. Kliknij, aby dodać nowy ciąg tokenu przy użyciu wartości wprowadzonych w polach **Nazwa** i **priorytet** .

 Usuń kliknięcie, aby usunąć wybrany token z **listy tokenów**. Nie można usunąć domyślnego tokenu komentarza.

 Zmień kliknięcie, aby wprowadzić zmiany w istniejącym tokenie przy użyciu wartości wprowadzonych w polach **Nazwa** i **priorytet** .

> [!NOTE]
> Nie można zmienić ani usunąć domyślnego tokenu komentarza, ale można zmienić jego poziom priorytetu.

## <a name="see-also"></a>Zobacz też
 [Korzystanie z](../../ide/using-the-task-list.md) [zakładek ustawień lista zadań w](../../ide/setting-bookmarks-in-code.md) [oknie dialogowym Opcje środowiska](../../ide/reference/environment-options-dialog-box.md) kodu
