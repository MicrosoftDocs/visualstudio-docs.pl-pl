---
title: Opcje, edytor tekstów, ogólne
ms.date: 01/18/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General
- VS.ToolsOptionsPages.Text_Editor.SQL.General
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.T-SQL80.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- VS.ToolsOptionsPages.Text_Editor.PL/SQL.General
- VS.ToolsOptionsPages.Text_Editor
- VS.ToolsOptionsPages.Text_Editor.XOML.General
- VS.ToolsOptionsPages.Text_Editor.SQL
- VS.ToolsOptionsPages.Text_Editor.SQL_Script
- VS.ToolsOptionsPages.Text_Editor.General
- VS.ToolsOptionsPages.Text_Editor.Python
- VS.ToolsOptionsPages.Text_Editor.R
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9a7bcf7b57c6cdc7e0ff4ff5a851397b7c96b345
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62778668"
---
# <a name="options-text-editor-general"></a>Opcje, edytor tekstów, ogólne

To okno dialogowe umożliwia zmianę ustawień globalnych dla edytora kodu i tekstu programu Visual Studio. Aby wyświetlić to okno dialogowe, wybierz **opcje** na **narzędzia** menu, rozwiń węzeł **edytora tekstów** folder, a następnie wybierz **ogólne**.

## <a name="settings"></a>Ustawienia

### <a name="drag-and-drop-text-editing"></a>Przeciąganie i upuszczanie edycji tekstu

Gdy zaznaczone, umożliwia przenoszenie tekstu, wybierając ją i przeciągając je za pomocą myszy do innej lokalizacji w obrębie bieżącego dokumentu lub dowolnego otwartego dokumentu.

### <a name="automatic-delimiter-highlighting"></a>Automatyczne wyróżnianie ograniczników

Po wybraniu znaki ogranicznika, oddzielające parametry lub par wartości elementu, a także parowanych nawiasów klamrowych, zostały wyróżnione.

### <a name="track-changes"></a>Śledzenie zmian

Po wybraniu edytora kodu żółta linia pionowa pojawia się w margines zaznaczania, aby oznaczyć kodu, które uległy zmianie od czasu ostatniego został zapisany plik. Po zapisaniu zmian pionowe linie stają się zielony.

### <a name="auto-detect-utf-8-encoding-without-signature"></a>Automatyczne wykrywanie kodowania bez podpisu UTF-8

Domyślnie Edytor wykrywa, kodowanie, wyszukując znaczniki kolejności bajtów lub tagi zestaw znaków. Jeśli nie zostanie znaleziony w bieżącym dokumencie, Edytor kodu próbuje Autowykrywanie UTF-8 kodowania przez skanowanie sekwencji bajtów. Aby wyłączyć automatycznego wykrywania kodowania, usuń zaznaczenie tej opcji.

### <a name="follow-project-coding-conventions"></a>Postępuj zgodnie z Konwencji kodowania projektu

Po wybraniu określonego Konwencji kodowania projektu musi zostać zastąpiona Konwencji kodowania, używane w osobistych projektach.

### <a name="enable-mouse-click-to-perform-go-to-definition"></a>Włącz kliknięcie myszą wykonać polecenie Przejdź do definicji

Wybranie tej opcji, możesz nacisnąć przycisk **Ctrl** i umieść kursor nad elementem, a następnie kliknij przycisk myszy. To spowoduje przejście do definicji wybranego elementu. Istnieje również możliwość albo **Alt** lub **Ctrl** + **Alt** z **klawisz modyfikujący użyj** listy rozwijanej.

Wybierz **Otwórz definicję w widoku podglądu** pole wyboru, aby wyświetlić w oknie definicji elementu, bez konieczności opuszczania Twojej bieżącej lokalizacji w edytorze kodu.

## <a name="display"></a>Monitor

### <a name="selection-margin"></a>Margines zaznaczania

Po wybraniu Wyświetla pionowego marginesu wzdłuż lewej krawędzi obszaru tekstu edytora. Możesz kliknąć margines w ten sposób, aby zaznaczyć cały wiersz tekstu, lub kliknij i przeciągnij, aby zaznaczyć następujące po sobie wierszy tekstu.

|Margines zaznaczania na|Margines zaznaczania wyłączone|
| - | - |
|![HTMLpageSelectionMarginOn — zrzut ekranu](../../ide/reference/media/vxselmaron.gif)|![HTMLpageSelectionMarginOff — zrzut ekranu](../../ide/reference/media/vxselmaroff.gif)|

### <a name="indicator-margin"></a>Margines wskaźnika

Po wybraniu Wyświetla pionowego marginesu poza lewej krawędzi obszaru tekstu edytora. Po kliknięciu tego marginesie są wyświetlane ikonę i etykietkę narzędzia, które są powiązane z tekstu. Na przykład punkt przerwania lub zadania skróty listy są wyświetlane w margines wskaźnika. Wskaźnik marży informacje nie są drukowane.

### <a name="highlight-current-line"></a>Wyróżnij bieżący wiersz

Po wybraniu Wyświetla szary prostokąt wokół linii kodu, w którym znajduje się kursor.

### <a name="show-structure-guide-lines"></a>Pokaż linie prowadnic struktury

Po wybraniu wyświetlane pionowe linie w edytorze tego wiersza się przy użyciu bloków kodu ze strukturą, co pozwala łatwo identyfikować poszczególnych bloków kodu.

## <a name="see-also"></a>Zobacz także

- [Opcje, Edytor tekstów, Wszystkie języki](../../ide/reference/options-text-editor-all-languages.md)
- [Opcje, Edytor tekstów, Wszystkie języki, Karty](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Opcje, Edytor tekstów, Rozszerzenie pliku](../../ide/reference/options-text-editor-file-extension.md)
- [Identyfikowanie i dostosowywanie skrótów klawiaturowych](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)
- [Dostosowywanie edytora](../../ide/customizing-the-editor.md)
- [Korzystanie z funkcji IntelliSense](../../ide/using-intellisense.md)