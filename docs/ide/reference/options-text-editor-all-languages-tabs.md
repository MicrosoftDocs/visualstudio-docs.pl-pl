---
title: Opcje, edytor tekstu, wszystkie języki, karty
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.ResJSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs
helpviewer_keywords:
- indents, Code Editor
- Code Editor, default behavior
- tabs, setting in Code Editor
- All Languages Text Editor Options dialog box
- editors, Code Editor
- Code Editor, indenting
- Code Editor, tabs
ms.assetid: 7e208e1d-5e3a-4bf7-a27b-4417e3e049c7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: dc369162c4bb81b7cda7487bd9149aad7493d2fb
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388416"
---
# <a name="options-text-editor-all-languages-tabs"></a>Opcje, edytor tekstu, wszystkie języki, karty

To okno dialogowe pozwala zmienić domyślne zachowanie edytora kodu. Te ustawienia mają zastosowanie również do innych edytorów oparte na kod edytora, takiego jak widok źródła w Projektancie HTML. Aby wyświetlić te opcje, wybierz **opcje** z **narzędzia** menu. W ramach **edytora tekstów** rozwiń folder **wszystkie języki** podfolder, a następnie wybierz **karty**.

> [!CAUTION]
> Ta strona ustawia domyślne opcje dla wszystkich języków programowania. Należy pamiętać, że zresetowanie opcji, w tym oknie dialogowym przywróci Opcje kart we wszystkich językach niezależnie od opcji wybranych są w tym miejscu. Aby zmienić opcje edytora tekstowego dla tylko jednego języka, rozwiń podfolder dla danego języka, a następnie wybierz jego stron opcji.

W przypadku różnych ustawień na stronach opcji karty dla określonych języków programowania, a następnie komunikat "Ustawienia wcięć dla pojedynczych tekstu formatów będących w konflikcie ze sobą" jest wyświetlana dla różniących się **Indenting**opcje; i wyświetlany jest komunikat "Ustawienia tabulacji dla pojedynczych tekstu formatów będących w konflikcie ze sobą," dla różniących się **kartę** opcje. Na przykład tego monitu jest wyświetlana, jeśli **inteligentnego wcięcia** opcja jest zaznaczona dla języka Visual Basic, ale **Block wcięcia** został wybrany do Visual C++.

## <a name="indenting"></a>Wcięcia

Brak

Po wybraniu nowe wiersze są nie będą wcięte. Punkt wstawiania znajduje się w pierwszej kolumnie znakiem nowego wiersza.

Blok

Po wybraniu nowych wierszy tworzone jest wcięcie automatycznie. Punkt wstawiania znajduje się w tym samym punkcie wyjścia, jak poprzedni wiersz.

Inteligentne

Po wybraniu nowe wiersze są umieszczone w celu dopasowania kontekst kodu według innych kodów formatowania, ustawienia i konwencje technologii IntelliSense dla języka programowania. Ta opcja nie jest dostępny dla wszystkich języków programowania.

Na przykład wiersze ujęte w nawias klamrowy otwierający ({}) i zamykający nawias klamrowy (}) może być automatycznie wcięty dodatkowe tabulatora od pozycji wyrównany nawiasów klamrowych.

## <a name="tabs"></a>Karty

Rozmiar tabulatora

Ustawia odległość w spacji między kartę zatrzymuje. Wartość domyślna to cztery miejsca do magazynowania.

Wcięcie

Określa rozmiar w obszarach automatyczne wcięcia. Wartość domyślna to cztery miejsca do magazynowania. Znaki tabulacji i/lub spacjami zostanie wstawiony do wypełnienia określonego rozmiaru.

Wstawiaj odstępy

Po wybraniu operacji wcięcie wstawić tylko znaki spacji, nie znaki TABULACJI. Jeśli **wcięcie** jest ustawiony na 5, na przykład, następnie pięć znaków spacji są wstawiane po naciśnięciu klawisza TAB lub **Zwiększ wcięcie** znajdujący się na **formatowanie** pasek narzędzi.

Utrzymaj tabulacje

Po wybraniu operacji wcięcie Wstaw tyle znaków TABULACJI jak to możliwe. Każdy znak TABULACJI Wstawia liczbę spacji określoną w **wielkość tabulatora**. Jeśli **wcięcie** nie jest całkowitą wielokrotnością **wielkość tabulatora**, spacje są dodawane do Wypełnij różnica.

## <a name="see-also"></a>Zobacz także

- [Opcje, Edytor tekstów, Wszystkie języki](../../ide/reference/options-text-editor-all-languages.md)
- [Ogólne, Środowisko, Opcje — okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)