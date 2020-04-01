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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ed55d65555425b04749696b5510cfe799d2a1194
ms.sourcegitcommit: ce3d0728ec1063ab548dac71c8eaf26d20450acc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80472819"
---
# <a name="options-dialog-box-text-editor--general"></a>Okno dialogowe Opcje: Edytor \> tekstu ogólny

To okno dialogowe umożliwia zmianę ustawień globalnych dla edytora kodu i tekstu programu Visual Studio. Aby wyświetlić to okno dialogowe, wybierz polecenie **Opcje** w menu **Narzędzia,** rozwiń folder **Edytor tekstu,** a następnie wybierz pozycję **Ogólne**.

## <a name="settings"></a>Ustawienia

### <a name="drag-and-drop-text-editing"></a>Przeciągnij i upuść edycję tekstu

Gdy ta opcja jest zaznaczona, można przenieść tekst, zaznaczając go i przeciągając myszą w inne miejsce w bieżącym dokumencie lub innym otwartym dokumencie.

### <a name="automatic-delimiter-highlighting"></a>Automatyczne wyróżnianie ogranicznika

Gdy ta opcja jest zaznaczona, wyróżnione są znaki ogranicznika, które oddzielają parametry lub pary wartości towaru, a także pasujące nawiasy klamrowe.

### <a name="track-changes"></a>Śledzenie zmian

Po wybraniu edytora kodu na marginesie zaznaczenia pojawia się pionowa żółta linia, aby oznaczyć kod, który uległ zmianie od czasu ostatnio zapisanego pliku. Po zapisaniu zmian pionowe linie stają się zielone.

### <a name="auto-detect-utf-8-encoding-without-signature"></a>Automatyczne wykrywanie kodowania UTF-8 bez podpisu

Domyślnie edytor wykrywa kodowanie, wyszukując znaczniki kolejności bajtów lub znaczniki zestawu znaków. Jeśli żaden z nich nie zostanie znaleziony w bieżącym dokumencie, edytor kodu próbuje automatycznie wyekstywać kodowanie UTF-8 przez skanowanie sekwencji bajtów. Aby wyłączyć automatyczne wykrywanie kodowania, wyczyść tę opcję.

### <a name="follow-project-coding-conventions"></a>Postępuj zgodnie z konwencjami kodowania projektów

Po wybraniu tej opcji określone konwencje kodowania projektu zastępują wszystkie konwencje kodowania używane w projektach osobistych.

### <a name="enable-mouse-click-to-perform-go-to-definition"></a>Włącz kliknięcie myszą, aby wykonać przejdź do definicji

Po wybraniu tej opcji można nacisnąć klawisz **Ctrl** i najechać kursorem na element, klikając myszą. W ten sposób prowadzi do definicji wybranego elementu. Z listy rozwijanej **Użyj klawisza modyfikatora** można również wybrać **alt** lub **klawisz Ctrl** + **Alt.**

Zaznacz pole wyboru **Otwórz definicję w widoku wglądu,** aby wyświetlić definicję elementu w oknie bez przechodzenia z dala od bieżącej lokalizacji w edytorze kodu.

## <a name="display"></a>Monitor

### <a name="selection-margin"></a>Margines wyboru

Gdy ta opcja jest zaznaczona, wyświetla pionowy margines wzdłuż lewej krawędzi obszaru tekstowego edytora. Możesz kliknąć ten margines, aby zaznaczyć cały wiersz tekstu, lub kliknąć i przeciągnąć, aby zaznaczyć kolejne wiersze tekstu.

|Margines wyboru na|Margines zaznaczenia wyłączony|
| - | - |
|![HTMLpageSelectionMarginOn zrzut ekranu](../../ide/reference/media/vxselmaron.gif)|![HTMLpageSelectionMarginOff zrzut ekranu](../../ide/reference/media/vxselmaroff.gif)|

### <a name="indicator-margin"></a>Margines wskaźnika

Gdy ta opcja jest zaznaczona, wyświetla pionowy margines poza lewą krawędzią obszaru tekstowego edytora. Po kliknięciu na tym marginesie pojawi się ikona i etykietka narzędzia, które są związane z tekstem. Na przykład skróty do punktu przerwania lub listy zadań są wyświetlane na marginesie wskaźnika. Informacje o marginesie wskaźnika nie są drukowane.

### <a name="highlight-current-line"></a>Wyróżnianie bieżącej linii

Gdy ta opcja jest zaznaczona, wyświetla szare pole wokół linii kodu, w której znajduje się kursor.

### <a name="show-structure-guide-lines"></a>Pokaż linie prowadzące konstrukcji

Po zaznaczeniu tej opcji w edytorze pojawiają się pionowe linie, które są zgodne ze strukturalnymi blokami kodu, co umożliwia łatwą identyfikację poszczególnych bloków kodu.

### <a name="show-file-health-indicator"></a>Pokaż wskaźnik kondycji pliku

Po wybraniu tej opcji pasek wskaźnika kondycji pliku (błędy, ostrzeżenia) z opcjami oczyszczania kodu zostanie wyświetlony w lewym dolnym rogu edytora.

## <a name="see-also"></a>Zobacz też

- [Opcje, edytor tekstu, wszystkie języki](../../ide/reference/options-text-editor-all-languages.md)
- [Opcje, Edytor tekstów, Wszystkie języki, Karty](../../ide/reference/options-text-editor-all-languages-tabs.md)
- [Opcje, Edytor tekstów, Rozszerzenie pliku](../../ide/reference/options-text-editor-file-extension.md)
- [Identyfikowanie i dostosowywanie skrótów klawiaturowych](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)
- [Dopasowywanie edytora](../how-to-change-text-case-in-the-editor.md)
- [Korzystanie z IntelliSense](../../ide/using-intellisense.md)
