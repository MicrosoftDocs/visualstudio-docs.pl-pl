---
title: Opcje, edytor tekstów, ogólne
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
- VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General
- VS.ToolsOptionsPages.Text_Editor.SQL.General
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.XML.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL80.General
- VS.ToolsOptionsPages.Text_Editor.CSS
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- VS.ToolsOptionsPages.Text_Editor.F#.Tabs
- VS.ToolsOptionsPages.Text_Editor.F#
- VS.ToolsOptionsPages.Text_Editor.PL/SQL.General
- VS.ToolsOptionsPages.Text_Editor.C/C++.General
- VS.ToolsOptionsPages.Text_Editor.Plain_Text
- VS.ToolsOptionsPages.Text_Editor.HTML
- VS.ToolsOptionsPages.Text_Editor.XAML.General
- VS.ToolsOptionsPages.Text_Editor
- VS.ToolsOptionsPages.Text_Editor.F#.General
- VS.ToolsOptionsPages.Text_Editor.XOML.General
- VS.ToolsOptionsPages.Text_Editor.SQL
- vs.toolsoptionspages.text_editor.c/c++
- VS.ToolsOptionsPages.Text_Editor.SQL_Script
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.General
- VS.ToolsOptionsPages.Text_Editor.General
- VS.ToolsOptionsPages.Text_Editor.CSharp
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 75051013e38d4acf5339193cf9f80e6da6758284
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388802"
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

Domyślnie Edytor wykrywa, kodowanie, wyszukując znaczniki kolejności bajtów lub tagi zestaw znaków. Jeśli nie zostanie znaleziony w bieżącym dokumencie, Edytor kodu próbuje automatyczne wykrywanie kodowania UTF-8 przez zeskanowanie sekwencji bajtów. Aby wyłączyć automatyczne wykrywanie kodowania, usuń zaznaczenie tej opcji.

## <a name="display"></a>Monitor

### <a name="selection-margin"></a>Margines zaznaczania

Po wybraniu Wyświetla pionowego marginesu wzdłuż lewej krawędzi obszaru tekstu edytora. Możesz kliknąć margines w ten sposób, aby zaznaczyć cały wiersz tekstu, lub kliknij i przeciągnij, aby zaznaczyć następujące po sobie wierszy tekstu.

|Margines zaznaczania na|Margines zaznaczania wyłączone|
| - | - |
|![HTMLpageSelectionMarginOn — zrzut ekranu](../../ide/reference/media/vxselmaron.gif)|![HTMLpageSelectionMarginOff — zrzut ekranu](../../ide/reference/media/vxselmaroff.gif)|

### <a name="indicator-margin"></a>Margines wskaźnika

Po wybraniu Wyświetla pionowego marginesu poza lewej krawędzi obszaru tekstu edytora. Po kliknięciu tego marginesie są wyświetlane ikonę i etykietkę narzędzia, które są powiązane z tekstu. Na przykład punkt przerwania lub zadania skróty listy są wyświetlane w margines wskaźnika. Informacje o margines wskaźnika do drukowania.

### <a name="highlight-current-line"></a>Wyróżnij bieżący wiersz

Po wybraniu Wyświetla szary prostokąt wokół linii kodu, w którym znajduje się kursor.

## <a name="see-also"></a>Zobacz także

- [Opcje, Edytor tekstów, Wszystkie języki](../../ide/reference/options-text-editor-all-languages.md)
- [Opcje, Edytor tekstów, Wszystkie języki, Karty](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Opcje, Edytor tekstów, Rozszerzenie pliku](../../ide/reference/options-text-editor-file-extension.md)
- [Identyfikowanie i dostosowywanie skrótów klawiaturowych](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)
- [Dostosowywanie edytora](../../ide/customizing-the-editor.md)
- [Korzystanie z funkcji IntelliSense](../../ide/using-intellisense.md)