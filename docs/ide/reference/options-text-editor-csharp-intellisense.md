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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 87a167a75f3b06522da77d562b0137df89757975
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596219"
---
# <a name="options-text-editor-c-intellisense"></a>Opcje, edytor tekstu, C#, IntelliSense

Strona opcji **IntelliSense** służy do modyfikowania ustawień, które wpływają na zachowanie intellisense dla języka C#. Aby uzyskać dostęp do tej strony opcji, wybierz pozycję**Opcje** **narzędzi** > , a następnie wybierz pozycję **Edytor** > tekstu**C#** > **IntelliSense**.

Strona opcji **IntelliSense** zawiera następujące opcje:

## <a name="completion-lists"></a>Listy uzupełnień

- Pokaż listę uzupełnień po wpisaniu znaku*

   Po wybraniu tej opcji program IntelliSense automatycznie wyświetla listę uzupełnień po rozpoczęciu wpisywania. Jeśli ta opcja nie jest zaznaczona, zakończenie intelliSense jest nadal dostępne w menu **IntelliSense** lub po naciśnięciu **klawisza Ctrl**+**Space**.

- Pokaż listę uzupełnień po usunięciu znaku

- Wyróżnianie pasujących części elementów listy uzupełnień

- Pokaż filtry elementów ukończenia

## <a name="snippets-behavior"></a>Zachowanie urywków

- Nigdy nie dołączaj urywków

   Po wybraniu tej opcji intellisense nigdy nie dodaje aliasów dla fragmentów kodu języka C# do listy uzupełniania.

- Zawsze dołączaj urywki

   Po wybraniu tej opcji intellisense dodaje aliasy dla fragmentów kodu języka C# do listy uzupełniania. W przypadku, gdy alias fragmentu kodu jest taki sam jak słowo kluczowe, na przykład [klasa](/dotnet/csharp/language-reference/keywords/class), słowo kluczowe jest zastępowane skrótem. Aby uzyskać więcej informacji, zobacz [Urywki kodu języka C#.](../../ide/visual-csharp-code-snippets.md)

- Dołączanie urywków, gdy po identyfikatorze jest wpisywany ?-Tab

   Gdy ta opcja jest zaznaczona, IntelliSense dodaje aliasy dla fragmentów kodu języka C# do listy uzupełnień, **gdy?** + **Karta** jest wciskana po identyfikatorze

## <a name="enter-key-behavior"></a>Wprowadź zachowanie klucza

- Nigdy nie dodawaj nowego wiersza po wprowadzeniu

   Określa, że nowy wiersz nigdy nie jest dodawany automatycznie po wybraniu elementu na liście uzupełnień i naciśnięciu **klawisza Enter**.

- Dodaj nowy wiersz na enter po zakończeniu w pełni wpisanego wyrazu

   Określa, że jeśli wpiszesz wszystkie znaki wpisu na liście zakończenia, a następnie naciśniesz **klawisz Enter,** nowy wiersz zostanie dodany automatycznie, a kursor zostanie przeniesiony do nowego wiersza.

   Na przykład, jeśli `else` wpiszesz, a następnie naciśnij **klawisz Enter,** w edytorze pojawi się następujący komunikat:

   `else`

   `|`(lokalizacja kursora)

   Jeśli jednak wpiszesz tylko, `el` a następnie naciśnij klawisz **Enter,** w edytorze pojawi się następujący komunikat:

   `else|`(lokalizacja kursora)

- Zawsze dodawaj nowy wiersz po wprowadzeniu

   Określa, że jeśli wpiszesz *dowolny* ze znaków wpisu na liście uzupełnień, a następnie naciśniesz **klawisz Enter,** nowy wiersz zostanie dodany automatycznie, a kursor zostanie przeniesiony do nowego wiersza.

## <a name="show-name-suggestions"></a>Pokaż sugestie dotyczące nazw

Wykonuje automatyczne uzupełnianie nazwy obiektu dla członków, które zostały niedawno wybrane.

## <a name="see-also"></a>Zobacz też

- [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
- [Korzystanie z IntelliSense](../../ide/using-intellisense.md)
