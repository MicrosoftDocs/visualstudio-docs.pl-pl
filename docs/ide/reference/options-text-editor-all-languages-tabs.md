---
title: Opcje, edytor tekstu, wszystkie języki, karty
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs
- VS.ToolsOptionsPages.Text_Editor.Basic.Tabs
- VS.ToolsOptionsPages.Text_Editor.CSharp.Tabs
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Tabs
- VS.ToolsOptionsPages.Text_Editor.CoffeeScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.CSS.Tabs
- VS.ToolsOptionsPages.Text_Editor.Dockerfile.Tabs
- VS.ToolsOptionsPages.Text_Editor.F%2523.Tabs
- VS.ToolsOptionsPages.Text_Editor.HQL.Tabs
- VS.ToolsOptionsPages.Text_Editor.HTML.Tabs
- VS.ToolsOptionsPages.Text_Editor.HTMLX.Tabs
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.TypeScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.JSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.LESS.Tabs
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.Tabs
- VS.ToolsOptionsPages.Text_Editor.ResJSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.SCSS.Tabs
- VS.ToolsOptionsPages.Text_Editor.SQL_Server_Tools.Tabs
- VS.ToolsOptionsPages.Text_Editor.StreamAnalytics.Tabs
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.Tabs
- VS.ToolsOptionsPages.Text_Editor.U-SQL.Tabs
- VS.ToolsOptionsPages.Text_Editor.XAML.Tabs
- VS.ToolsOptionsPages.Text_Editor.XML.Tabs
helpviewer_keywords:
- indents, Code Editor
- Code Editor, default behavior
- tabs, setting in Code Editor
- All Languages Text Editor Options dialog box
- editors, Code Editor
- Code Editor, indenting
- Code Editor, tabs
ms.assetid: 7e208e1d-5e3a-4bf7-a27b-4417e3e049c7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fc169960cf757e4e334d5f77b06ff70b0d6da7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75594750"
---
# <a name="options-text-editor-all-languages-tabs"></a>Opcje, edytor tekstu, wszystkie języki, karty

To okno dialogowe umożliwia zmianę domyślnego zachowania edytora kodu. Te ustawienia mają zastosowanie również do innych edytorów w oparciu o Edytor kodu, taki jak widok źródła projektanta HTML. Aby wyświetlić te opcje, wybierz opcję **Opcje** z menu **Narzędzia** . W folderze **Edytor tekstu** rozwiń podfolder **wszystkie języki** , a następnie wybierz pozycję **karty**.

> [!CAUTION]
> Ta strona służy do ustawiania opcji domyślnych dla wszystkich języków deweloperskich. Pamiętaj, że Resetowanie opcji w tym oknie dialogowym spowoduje zresetowanie opcji tabulatorów we wszystkich językach do wybranych opcji. Aby zmienić opcje edytora tekstu dla tylko jednego języka, rozwiń podfolder dla tego języka i wybierz jego strony opcji.

Jeśli na stronach opcji kart są wybrane różne ustawienia dla określonych języków programowania, komunikat "Ustawienia wcięć dla pojedynczych formatów tekstu kolidują ze sobą" jest wyświetlany w przypadku różnych opcji **wcięć** ; a komunikat "ustawienia tabulacji dla pojedynczych formatów tekstu kolidują ze sobą," jest wyświetlany dla różnych opcji **tabulacji** . Na przykład to przypomnienie jest wyświetlane, jeśli wybrano opcję **inteligentnego tworzenia wcięć** dla Visual Basic, ale dla Visual C++ zostanie wybrana opcja " **wcięcia bloku** ".

## <a name="indenting"></a>Wcięcia

Brak

Po wybraniu nie są wcięte wcięcia. Punkt wstawiania zostanie umieszczony w pierwszej kolumnie nowego wiersza.

Zablokowanie

Po wybraniu zostaną automatycznie zastosowane wcięcia nowych wierszy. Punkt wstawiania jest umieszczany w tym samym punkcie początkowym co poprzedni wiersz.

Inteligentnych

Po wybraniu nowe wiersze są pozycjonowane w celu dopasowania do kontekstu kodu, według innych ustawień formatowania kodu i Konwencji IntelliSense dla języka deweloperskiego. Ta opcja nie jest dostępna dla wszystkich języków deweloperskich.

Na przykład wiersze ujęte w nawias klamrowy otwierającego ({) i zamykającego nawiasu klamrowego (}) mogą automatycznie powodować wcięcie dodatkowego tabulatora od pozycji wyrównanych nawiasów klamrowych.

## <a name="tabs"></a>Karty

Rozmiar karty

Ustawia odległość między tabulatorami. Wartość domyślna to cztery spacje.

Wcięcie rozmiaru

Ustawia rozmiar w odstępach automatycznego wcięcia. Wartość domyślna to cztery spacje. Znaki tabulacji, znaki spacji lub oba zostaną wstawione w celu wypełnienia określonego rozmiaru.

Wstaw spacje

Po wybraniu wcięcia operacje wstawiają tylko znaki spacji, a nie znaki TABULACJi. Jeśli **Rozmiar wcięcia** jest ustawiony na 5, na przykład po naciśnięciu klawisza TAB lub przycisku **Zwiększ wcięcie** na pasku narzędzi **formatowania** zostanie wstawionych pięć znaków spacji.

Zachowaj karty

Po zaznaczeniu tej operacji wcięcia wstawiają dowolną liczbę znaków TABULACJi. Każdy znak TABULACJi wypełnia liczbę spacji określoną w polu **rozmiar karty**. Jeśli **Rozmiar wcięcia** nie jest parzystą wielokrotnością **rozmiaru karty**, znaki spacji są dodawane do wypełnienia różnic.

## <a name="see-also"></a>Zobacz też

- [Opcje, edytor tekstu, wszystkie języki](../../ide/reference/options-text-editor-all-languages.md)
- [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
