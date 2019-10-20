---
title: Opcje, Edytor tekstu, ogólne | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- vs.toolsoptionspages.text_editor.visual_jsharp
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
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
caps.latest.revision: 34
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa81b08d6e375da4ad67b2e6eec32f244a779408
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662261"
---
# <a name="options-text-editor-general"></a>Opcje, edytor tekstów, ogólne
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

To okno dialogowe umożliwia zmianę ustawień globalnych dla kodu [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] i edytora tekstu. Aby wyświetlić to okno dialogowe, kliknij przycisk **Opcje** w menu **Narzędzia** , rozwiń folder **Edytor tekstu** , a następnie kliknij pozycję **Ogólne**.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="settings"></a>Ustawienia
 Przeciąganie i upuszczanie edycji tekstu po zaznaczeniu umożliwia przeniesienie tekstu przez zaznaczenie go i przeciągnięcie go z myszą do innej lokalizacji w bieżącym dokumencie lub w innym otwartym dokumencie.

 Automatyczne Wyróżnianie ogranicznika po wybraniu, znaki ogranicznika oddzielające parametry lub pary wartości, a także pasujące nawiasy klamrowe, są podświetlane.

 Śledź zmiany po zaznaczeniu edytora kodu, w marginesie zaznaczenia pojawia się pionowa żółta linia, aby oznaczyć kod zmieniony od czasu ostatniego zapisania pliku. Po zapisaniu zmian linie pionowe stają się kolorem zielonym.

 Automatyczne wykrywanie kodowania UTF-8 bez podpisu domyślnie Edytor wykrywa kodowanie, wyszukując znaczniki kolejności bajtów lub Tagi charset. Jeśli żaden z nich nie zostanie znaleziony w bieżącym dokumencie, Edytor kodu próbuje automatycznie wykryć kodowanie UTF-8 przez skanowanie sekwencji bajtów. Aby wyłączyć Autowykrywanie kodowania, usuń zaznaczenie tej opcji.

## <a name="display"></a>Monitor
 Zaznaczony margines zaznaczenia powoduje wyświetlenie pionowego marginesu wzdłuż lewej krawędzi obszaru tekstowego edytora. Możesz kliknąć ten margines, aby zaznaczyć cały wiersz tekstu, lub kliknij i przeciągnij, aby zaznaczyć kolejne wiersze tekstu.

|Margines zaznaczenia na|Margines zaznaczenia jest wyłączony|
|-------------------------|--------------------------|
|![Zrzut ekranu HTMLpageSelectionMarginOn](../../ide/reference/media/vxselmaron.gif "vxSelmaron")|![Zrzut ekranu HTMLpageSelectionMarginOff](../../ide/reference/media/vxselmaroff.gif "vxSelmaroff")|

 Margines wskaźnika po zaznaczeniu Wyświetla pionowy margines poza lewą krawędzią obszaru tekstowego edytora. Po kliknięciu tego marginesu zostanie wyświetlona ikona i etykietka narzędzia, które są powiązane z tekstem. Na przykład skróty do punktów przerwania lub listy zadań pojawiają się na marginesie wskaźnika. Informacje o marginesie wskaźnika nie są drukowane.

 Pionowy pasek przewijania po zaznaczeniu powoduje wyświetlenie pionowego paska przewijania, który umożliwia przewijanie w górę i w dół w celu wyświetlenia elementów, które znajdują się poza obszarem wyświetlania edytora. Jeśli pionowe paski przewijania nie są dostępne, można użyć klawiszy Page Up, Page Down i Cursor do przewinięcia.

 Poziomy pasek przewijania po zaznaczeniu, wyświetla poziomy pasek przewijania, który umożliwia przewijanie z boku do widoku elementów, które znajdują się poza obszarem wyświetlania edytora. Jeśli poziome paski przewijania są niedostępne, możesz użyć klawiszy kursora do przewinięcia.

 Wyróżnij bieżący wiersz po zaznaczeniu, wyświetla szare pole wokół wiersza kodu, w którym znajduje się kursor.

## <a name="see-also"></a>Zobacz też
 [Opcje, Edytor tekstu, wszystkie opcje języka](../../ide/reference/options-text-editor-all-languages.md) [, Edytor tekstu, wszystkie języki, opcje kart](../../ide/reference/options-text-editor-all-languages-tabs.md) [, Edytor tekstu, rozszerzenie pliku](../../ide/reference/options-text-editor-file-extension.md) [identyfikujący i dostosowujący skróty klawiaturowe](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md) [dostosowujące edytora](../../ide/customizing-the-editor.md) [za pomocą Funkcja IntelliSense](../../ide/using-intellisense.md)
