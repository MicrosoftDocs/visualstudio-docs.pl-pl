---
title: Opcje, Edytor tekstu, C-C + +, formatowanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- C++
helpviewer_keywords:
- Text Editor Options dialog box, formatting
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5ad06dfb32c301985eb4976f6c89c7be1e0e68da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662339"
---
# <a name="options-text-editor-cc-formatting"></a>Opcje, edytor tekstu, C/C++, formatowanie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pozwala zmienić domyślne zachowanie Edytora kodu podczas programowania w C lub C++.

 Aby uzyskać dostęp do tej strony, w oknie dialogowym **Opcje** w okienku po lewej stronie rozwiń pozycję **Edytor tekstu**, rozwiń węzeł **C/C++**, a następnie kliknij pozycję **Formatowanie**.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień deweloperskich w programie Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="cc-options"></a>Opcje C/C++
 **Włącz automatyczne szybkie informacje etykietki narzędzi** Włącza lub wyłącza funkcję IntelliSense z szybkimi informacjami.

## <a name="inactive-code"></a>Kod nieaktywny
 **Pokaż nieaktywne bloki kodu** Kod, który jest nieaktywny z powodu `#ifdef` deklaracji ma odmienny kolor, aby ułatwić jego identyfikację.

 **Wyłącz nieprzezroczystość nieaktywnego kodu** Nieaktywny kod można zidentyfikować za pomocą koloru zamiast przezroczystości.

 **Procent nieprzezroczystości nieaktywnego kodu** Stopień nieprzezroczystości bloków kodu nieaktywnych można dostosować.

## <a name="indentation"></a>Wcięcie
 **Wcięcie nawiasów klamrowych** Można skonfigurować sposób, w jaki nawiasy klamrowe są wyrównane po naciśnięciu klawisza ENTER po rozpoczęciu bloku kodu, na przykład funkcja lub `for` pętla. Nawiasy klamrowe mogą być wyrównane względem pierwszego znaku bloku kodu lub wcięte.

 **Automatyczne wcięcie na karcie** Można skonfigurować, co się dzieje w bieżącym wierszu kodu po naciśnięciu klawisza TAB. Albo wiersz zostaje wcięty, albo zostaje wstawiony tabulator.

## <a name="miscellaneous"></a>Różne
 **Wylicz komentarze w oknie Lista zadań** Edytor może skanować pliki Open Source dla wstępnie ustawionych słów w komentarzach. Tworzy wpis w oknie **Lista zadań** dla dowolnych słów kluczowych, które znajdzie.

 **Wyróżnij pasujące tokeny** Gdy kursor znajduje się obok nawiasu klamrowego, Edytor może wyróżnić pasujący nawias klamrowy, aby można było łatwiej zobaczyć zawarty kod.

## <a name="outlining"></a>Tworzenie konspektu
 **Wejdź do trybu konspektu przy otwieraniu plików** Po przełączeniu pliku do edytora tekstów można włączyć funkcję tworzenia konspektu. Aby uzyskać więcej informacji, zobacz [Tworzenie konspektu](../../ide/outlining.md). Gdy ta opcja jest zaznaczona, tworzenie konspektów jest włączone po otwarciu pliku.

 **Automatyczne tworzenie konspektu bloków #pragma regionów** Gdy ta opcja jest zaznaczona, automatyczne tworzenie konspektu dla [dyrektyw pragma](https://msdn.microsoft.com/library/9867b438-ac64-4e10-973f-c3955209873f) jest włączone. Dzięki temu można rozwinąć lub zwinąć bloki regionów pragmy w trybie konspektu.

 **Automatyczne tworzenie konspektu bloków instrukcji** Gdy ta opcja jest zaznaczona, automatyczne tworzenie konspektu jest włączone dla następujących konstrukcji instrukcji:

- [if-else](https://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2)

- [switch — instrukcja (C++)](https://msdn.microsoft.com/library/6c3f3ed3-5593-463c-8f4b-b33742b455c6)

- [While — Instrukcja (C++)](https://msdn.microsoft.com/library/358dbe76-5e5e-4af5-b575-c2293c636899)

## <a name="see-also"></a>Zobacz też
 [Ogólne, środowisko, Opcje — okno dialogowe](../../ide/reference/general-environment-options-dialog-box.md) [przy użyciu funkcji IntelliSense](../../ide/using-intellisense.md)
