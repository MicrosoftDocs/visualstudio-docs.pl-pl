---
title: Opcje, edytor tekstu, C#, IntelliSense
description: Dowiedz się, jak modyfikować ustawienia wpływające na zachowanie funkcji IntelliSense dla języka C# przy użyciu strony IntelliSense w sekcji języka C#.
ms.custom: SEO-VS-2020
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8e727fad6d3cb15f70cf630b1077170d16d28b7f
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039747"
---
# <a name="options-text-editor-c-intellisense"></a>Opcje, edytor tekstu, C#, IntelliSense

Na stronie opcje **IntelliSense** można modyfikować ustawienia wpływające na zachowanie funkcji IntelliSense dla języka C#. Aby uzyskać dostęp do tej strony opcji **Tools**, wybierz  >  **Opcje** narzędzia, a następnie wybierz **Edytor tekstu**  >  **C#**  >  **IntelliSense**.

Strona Opcje **IntelliSense** zawiera następujące opcje:

## <a name="completion-lists"></a>Listy uzupełniania

- Pokaż listę uzupełniania po wpisaniu znaku *

   Po wybraniu tej opcji funkcja IntelliSense automatycznie wyświetla listę uzupełniania po rozpoczęciu wpisywania. Gdy ta opcja nie jest zaznaczona, uzupełnianie IntelliSense jest nadal dostępne z menu **IntelliSense** lub przez naciśnięcie klawisza **Ctrl** + **Space**.

- Pokaż listę uzupełniania po usunięciu znaku

- Wyróżnij pasujące fragmenty elementów listy uzupełniania

- Pokaż filtry elementów ukończenia

## <a name="snippets-behavior"></a>Zachowanie fragmentów kodu

- Nigdy nie dołączaj fragmentów kodu

   Po wybraniu tej opcji funkcja IntelliSense nigdy nie dodaje aliasów dla fragmentów kodu C# do listy uzupełniania.

- Zawsze dołączaj fragmenty kodu

   Po wybraniu tej opcji technologia IntelliSense dodaje aliasy dla fragmentów kodu C# do listy uzupełniania. W przypadku, gdy alias fragmentu kodu jest taki sam jak słowo kluczowe, na przykład, [Klasa](/dotnet/csharp/language-reference/keywords/class), słowo kluczowe jest zastępowane skrótem. Aby uzyskać więcej informacji, zobacz [fragmenty kodu w języku C#](../../ide/visual-csharp-code-snippets.md).

- Dołącz fragmenty kodu, gdy?-Tab jest wpisana po identyfikatorze

   Po wybraniu tej opcji technologia IntelliSense dodaje aliasy dla wstawek kodu C# do listy uzupełniania, gdy **?** + Naciśnięcie klawisza **Tab** po identyfikatorze

## <a name="enter-key-behavior"></a>Zachowanie klawisza ENTER

- Nigdy nie dodawaj nowego wiersza po wprowadzeniu

   Określa, że nowy wiersz nigdy nie jest dodawany automatycznie po wybraniu elementu na liście uzupełniania i naciśnięciu klawisza **Enter**.

- Dodaj nowy wiersz po zakończeniu w pełni wpisanego wyrazu.

   Określa, że po wpisaniu wszystkich znaków dla wpisu na liście uzupełniania, a następnie naciśnięciu klawisza **Enter**, nowy wiersz zostanie dodany automatycznie, a kursor zostanie przeniesiony do nowego wiersza.

   Na przykład, jeśli wpiszesz, `else` a następnie naciśniesz klawisz **Enter**, w edytorze zostanie wyświetlony następujący komunikat:

   `else`

   `|` (Lokalizacja kursora)

   Jeśli jednak wpiszesz polecenie, `el` a następnie naciśniesz klawisz **Enter**, w edytorze zostanie wyświetlony następujący komunikat:

   `else|` (Lokalizacja kursora)

- Zawsze dodawaj nowy wiersz po wprowadzeniu

   Określa, że po wpisaniu *dowolnego* ze znaków dla wpisu na liście uzupełniania, a następnie naciśnięciu klawisza **Enter**, nowy wiersz zostanie dodany automatycznie, a kursor zostanie przeniesiony do nowego wiersza.

## <a name="show-name-suggestions"></a>Pokaż sugestie dotyczące nazw

Wykonuje automatyczne uzupełnianie nazw obiektów dla elementów członkowskich, które zostały ostatnio wybrane.

## <a name="see-also"></a>Zobacz też

- [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
- [Korzystanie z funkcji IntelliSense](../../ide/using-intellisense.md)
