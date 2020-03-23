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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594750"
---
# <a name="options-text-editor-all-languages-tabs"></a>Opcje, edytor tekstu, wszystkie języki, karty

To okno dialogowe umożliwia zmianę domyślnego zachowania Edytora kodu. Te ustawienia dotyczą również innych edytorów na podstawie Edytora kodu, takich jak widok źródłowy projektanta HTML. Aby wyświetlić te opcje, wybierz **polecenie Opcje** z menu **Narzędzia.** W folderze **Edytor tekstu** rozwiń podfolder **Wszystkie języki,** a następnie wybierz pozycję **Karty**.

> [!CAUTION]
> Ta strona ustawia domyślne opcje dla wszystkich języków programowania. Pamiętaj, że zresetowanie opcji w tym oknie dialogowym spowoduje zresetowanie opcji kart we wszystkich językach do wyboru, niezależnie od wybranych tutaj opcji. Aby zmienić opcje edytora tekstu tylko dla jednego języka, rozwiń podfolder dla tego języka i wybierz jego strony opcji.

Jeśli na stronach opcji tabulatory dla poszczególnych języków programowania zaznaczono różne ustawienia, wyświetlane są komunikat "Ustawienia wcięcie dla poszczególnych formatów tekstu są ze sobą sprzeczne", aby uzyskać różne opcje **wcięcie;** i komunikat "Ustawienia karty dla poszczególnych formatów tekstu są ze sobą sprzeczne", jest wyświetlany dla różnych opcji **karty.** Na przykład to przypomnienie jest wyświetlane, jeśli opcja **Inteligentne wcięcie** jest zaznaczona dla języka Visual Basic, ale **wcięcie bloku** jest zaznaczone dla programu Visual C++.

## <a name="indenting"></a>Wcięcia

Brak

Po wybraniu tej opcji nowe wiersze nie są wcięte. Punkt wstawiania jest umieszczany w pierwszej kolumnie nowego wiersza.

Blok

Gdy ta opcja jest zaznaczona, nowe wiersze są automatycznie wcięte. Punkt wstawiania jest umieszczany w tym samym punkcie początkowym co poprzednia linia.

Inteligentne

Po wybraniu tej opcji nowe wiersze są umieszczane w celu dopasowania do kontekstu kodu, dla innych ustawień formatowania kodu i konwencji IntelliSense dla języka programowania. Ta opcja nie jest dostępna dla wszystkich języków programowania.

Na przykład linie zamknięte między nawiasem klamrowym otwierającym ( { ) a nawiasem zamykającym ( } ) mogą być automatycznie wcięte dodatkowe gołym okiem od pozycji wyrównanych nawiasów klamrowych.

## <a name="tabs"></a>Karty

Rozmiar karty

Ustawia odległość w przestrzeniach między tabulatorami. Wartość domyślna to cztery spacje.

Rozmiar wcięcie

Ustawia rozmiar w przestrzeniach automatycznego wcięci. Wartość domyślna to cztery spacje. Znaki tabulatora, znaki spacji lub oba zostaną wstawione w celu wypełnienia określonego rozmiaru.

Wstawianie spacji

Gdy ta opcja jest zaznaczona, operacje wcięciowe wstawiają tylko znaki spacji, a nie znaki TAB. Jeśli na przykład **rozmiar wcięcie** jest ustawiony na 5, po każdym naciśnięciu klawisza TAB lub przycisku **Zwiększ wcięcie** na pasku narzędzi **Formatowanie** wstawianie jest wstawiane pięcioma znakami spacji.

Zachowaj karty

Gdy ta opcja jest zaznaczona, operacje wcięć wstawiają jak najwięcej znaków TAB. Każdy znak TAB wypełnia liczbę spacji określoną w **rozmiarze karty**. Jeśli **rozmiar Wcięcie** nie jest nawet wielokrotnością **rozmiaru karty,** znaki spacji są dodawane w celu wypełnienia różnicy.

## <a name="see-also"></a>Zobacz też

- [Opcje, edytor tekstu, wszystkie języki](../../ide/reference/options-text-editor-all-languages.md)
- [Ogólne, środowisko, opcje — Okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md)
