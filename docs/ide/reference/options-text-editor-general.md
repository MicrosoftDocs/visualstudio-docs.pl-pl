---
title: Opcje, edytor tekstów, ogólne
ms.date: 01/18/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Outlining
- VS.ToolsOptionsPages.Text_Editor.General
- VS.ToolsOptionsPages.Text_Editor.PL/SQL
- VS.ToolsOptionsPages.Text_Editor.PL/SQL.General
- VS.ToolsOptionsPages.Text_Editor.Python
- VS.ToolsOptionsPages.Text_Editor.R
- VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General
- VS.ToolsOptionsPages.Text_Editor.SQL
- VS.ToolsOptionsPages.Text_Editor.SQL.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL80
- VS.ToolsOptionsPages.Text_Editor.T-SQL80.General
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ee7d7ebab51a3edfeb84a95609c6bdad581b6753
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666209"
---
# <a name="options-dialog-box-text-editor--general"></a>Opcje — okno dialogowe: Edytor tekstu \> ogólne

To okno dialogowe pozwala zmienić ustawienia globalne programu Visual Studio Code i edytora tekstu. Aby wyświetlić to okno dialogowe, wybierz opcję **Opcje** w menu **Narzędzia** , rozwiń folder **Edytor tekstu** , a następnie wybierz pozycję **Ogólne**.

## <a name="settings"></a>Ustawienia

### <a name="drag-and-drop-text-editing"></a>Edytowanie tekstu metodą "przeciągnij i upuść"

Gdy ta opcja jest zaznaczona, umożliwia przeniesienie tekstu, zaznaczając go i przeciągając myszą do innej lokalizacji w bieżącym dokumencie lub dowolnym innym otwartym dokumencie.

### <a name="automatic-delimiter-highlighting"></a>Automatyczne Wyróżnianie ogranicznika

Gdy jest zaznaczone, znaki ogranicznika oddzielające parametry lub pary element-wartość, a także pasujące nawiasy klamrowe, są wyróżnione.

### <a name="track-changes"></a>Śledź zmiany

Po wybraniu edytora kodu w marginesie zaznaczenia zostanie wyświetlona pionowa żółta linia, aby oznaczyć kod zmieniony od czasu ostatniego zapisania pliku. Po zapisaniu zmian linie pionowe stają się kolorem zielonym.

### <a name="auto-detect-utf-8-encoding-without-signature"></a>Automatyczne wykrywanie kodowania UTF-8 bez podpisu

Domyślnie Edytor wykrywa kodowanie, wyszukując znaczniki kolejności bajtów lub Tagi charset. Jeśli żaden z nich nie zostanie znaleziony w bieżącym dokumencie, Edytor kodu podejmie próbę automatycznego wykrycia kodowania UTF-8 przez skanowanie sekwencji bajtów. Aby wyłączyć Autowykrywanie kodowania, usuń zaznaczenie tej opcji.

### <a name="follow-project-coding-conventions"></a>Przestrzegaj konwencji kodowania projektu

Po wybraniu zasady kodowania określone dla projektu zastępują wszelkie konwencje kodowania używane w Twoich projektach osobistych.

### <a name="enable-mouse-click-to-perform-go-to-definition"></a>Włącz kliknięcie myszą, aby wykonać operację przejdź do definicji

Po zaznaczeniu można nacisnąć klawisz **Ctrl** i umieścić kursor nad elementem, a następnie klikając myszą. Wykonanie tej operacji spowoduje przejście do definicji wybranego elementu. Możesz również wybrać opcję **Alt** lub **Ctrl**  + **Alt** z listy rozwijanej **Użyj klawisza modyfikującego** .

Zaznacz pole wyboru **Otwórz definicję w widoku wglądu** , aby wyświetlić definicję elementu w oknie bez nawigowania do bieżącej lokalizacji w edytorze kodu.

## <a name="display"></a>Monitor

### <a name="selection-margin"></a>Margines zaznaczenia

Po wybraniu Wyświetla pionowy margines wzdłuż lewej krawędzi obszaru tekstowego edytora. Możesz kliknąć ten margines, aby zaznaczyć cały wiersz tekstu, lub kliknij i przeciągnij, aby zaznaczyć kolejne wiersze tekstu.

|Margines zaznaczenia na|Margines zaznaczenia jest wyłączony|
| - | - |
|![Zrzut ekranu HTMLpageSelectionMarginOn](../../ide/reference/media/vxselmaron.gif)|![Zrzut ekranu HTMLpageSelectionMarginOff](../../ide/reference/media/vxselmaroff.gif)|

### <a name="indicator-margin"></a>Margines wskaźnika

Po wybraniu Wyświetla pionowy margines poza lewą krawędzią obszaru tekstowego edytora. Po kliknięciu tego marginesu zostanie wyświetlona ikona i etykietka narzędzia, które są powiązane z tekstem. Na przykład skróty do punktów przerwania lub listy zadań pojawiają się na marginesie wskaźnika. Informacje o marginesie wskaźnika nie są drukowane.

### <a name="highlight-current-line"></a>Wyróżnij bieżący wiersz

Po wybraniu Wyświetla szare pole wokół wiersza kodu, w którym znajduje się kursor.

### <a name="show-structure-guide-lines"></a>Pokaż linie prowadnic struktury

Po wybraniu linie pionowe pojawiają się w edytorze, który jest wierszem ze strukturą bloków kodu, dzięki czemu można łatwo identyfikować poszczególne bloki kodu.

## <a name="see-also"></a>Zobacz także

- [Opcje, Edytor tekstów, Wszystkie języki](../../ide/reference/options-text-editor-all-languages.md)
- [Opcje, Edytor tekstów, Wszystkie języki, Karty](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Opcje, Edytor tekstów, Rozszerzenie pliku](../../ide/reference/options-text-editor-file-extension.md)
- [Identyfikowanie i dostosowywanie skrótów klawiaturowych](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)
- [Dostosowywanie edytora](../how-to-change-text-case-in-the-editor.md)
- [Korzystanie z funkcji IntelliSense](../../ide/using-intellisense.md)