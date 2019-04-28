---
title: Opcje, edytor tekstu, C#, IntelliSense
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
helpviewer_keywords:
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d7e7e76e025c2c426a83f00c1cf2af830eb1c26a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778687"
---
# <a name="options-text-editor-c-intellisense"></a>Opcje, edytor tekstu, C#, IntelliSense

Użyj **IntelliSense** Strona opcji, aby zmodyfikować ustawienia, które wpływają na działanie technologii IntelliSense dla C#. Dostępu do tej opcji strony, wybierz **narzędzia** > **opcje**, a następnie wybierz **edytora tekstów**  >  **C#**  >  **IntelliSense**.

**IntelliSense** opcje strona zawiera następujące opcje:

## <a name="completion-lists"></a>Listy uzupełniania

- Pokaż listę uzupełniania po wpisaniu znaku *

   Gdy ta opcja jest zaznaczona, IntelliSense wyświetla automatycznie na liście uzupełniania po rozpoczęciu wpisywania. Gdy ta opcja nie jest zaznaczona, uzupełnianie przez funkcję IntelliSense są nadal dostępne z poziomu **IntelliSense** menu lub naciskając **Ctrl**+**miejsca**.

- Pokaż listę uzupełniania po usunięciu znak

- Podświetl pasujące fragmenty elementów listy uzupełniania

- Pokaż filtry elementów uzupełniania

## <a name="snippets-behavior"></a>Zachowanie fragmentów kodu

- Nigdy nie dołączaj fragmentów kodu

   Gdy ta opcja jest zaznaczona, IntelliSense nigdy nie dodaje aliasy dla C# fragmenty do listy uzupełniania kodu.

- Zawsze dołączaj fragmenty kodu

   Gdy ta opcja jest zaznaczona, IntelliSense dodaje aliasy we fragmentach kodu języka C# na liście uzupełniania. W przypadku, gdy alias fragment kodu jest taka sama jak słowo kluczowe, na przykład [klasy](/dotnet/csharp/language-reference/keywords/class), słowo kluczowe zastępuje skrót. Aby uzyskać więcej informacji, zobacz [ C# fragmenty kodu](../../ide/visual-csharp-code-snippets.md).

- Dołącz fragmenty kodu podczas?-bezpośrednio po identyfikator karty

   Gdy ta opcja jest zaznaczona, IntelliSense dodaje aliasy dla C# listy fragmentów kodu do wykonania, kiedy **?** + **Kartę** wciśnięto po identyfikatorze

## <a name="enter-key-behavior"></a>Zachowanie klawisza ENTER

- Nigdy nie dodawaj nowy wiersz po naciśnięciu klawisza enter

   Określa nowy wiersz nigdy nie były automatycznie dodawane po wybraniu elementu na liście uzupełniania i naciskając klawisz **Enter**.

- Tylko wtedy dodawaj nowy wiersz po naciśnięciu klawisza enter po zakończeniu pełnego wpisanego wyrazu

   Określa, że jeśli wpisz wszystkie znaki dla wpisu na liście uzupełniania, a następnie naciśnij klawisz **Enter**, nowy wiersz jest automatycznie dodawany i kursor przesuwa się do nowego wiersza.

   Na przykład, jeśli wpiszesz `else` , a następnie naciśnij klawisz **Enter**, następujące pojawi się w edytorze:

   `else`

   `|` (Lokalizacja kursora)

   Jednakże jeśli wpiszesz tylko `el` , a następnie naciśnij klawisz **Enter**, następujące pojawi się w edytorze:

   `else|` (Lokalizacja kursora)

- Zawsze dodawaj nowy wiersz po naciśnięciu klawisza enter

   Określa, że jeśli wpiszesz *wszelkie* znaków dla pozycji w liście uzupełniania, a następnie naciśnij klawisz **Enter**, nowy wiersz jest automatycznie dodawany i kursor przesuwa się do nowego wiersza.

## <a name="show-name-suggestions"></a>Pokaż sugestie dotyczące nazwy

Wykonuje uzupełnianie nazw obiektów automatycznych ostatnio wybrane elementy członkowskie.

## <a name="see-also"></a>Zobacz także

- [Ogólne, Środowisko, Opcje — okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
- [Korzystanie z funkcji IntelliSense](../../ide/using-intellisense.md)