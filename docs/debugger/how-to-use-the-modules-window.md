---
title: Wyświetlanie bibliotek DLL i plików wykonywalnych
description: Wyświetlanie bibliotek DLL i plików wykonywalnych (.exe plików), których aplikacja używa w oknie Moduły podczas sesji debugowania w Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: Visual Studio Modules window
ms.date: 11/04/2018
ms.topic: how-to
f1_keywords:
- vs.debug.modules
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f82b8a5051cf1c338c4b1aab6e78209fb2bc08b0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385412"
---
# <a name="view-dlls-and-executables-in-the-modules-window-c-c-visual-basic-f"></a>Wyświetlanie bibliotek DLL i plików wykonywalnych w oknie Moduły (C#, C++, Visual Basic, F#)

Podczas Visual Studio w **oknie Modules** (Moduły) są dostępne informacje o plikach DLL i plikach wykonywalnych *(.exe* plików), których używa aplikacja.

> [!NOTE]
> Okno Moduły nie jest dostępne dla debugowania kodu SQL lub skryptu.

## <a name="use-the-modules-window"></a>Korzystanie z okna Moduły

Aby otworzyć okno Moduły podczas debugowania, wybierz pozycję **Debuguj** moduły systemu Windows (lub naciśnij  >    >   **klawisze Ctrl + Alt + U).**

Domyślnie okno Moduły **sortuje** moduły według kolejności ładowania. Aby posortować według dowolnej kolumny okna, wybierz nagłówek w górnej części kolumny.

## <a name="load-symbols"></a>Ładowanie symboli

Kolumna **Stan symboli** w **oknie Moduły** pokazuje, które moduły mają załadowane symbole debugowania. Jeśli stan to **Pominięto** symbole ładowania, Nie można odnaleźć lub otworzyć pliku **PDB** lub Ładowanie wyłączone przez ustawienie **dołączania/wykluczania**, można załadować symbole ręcznie. Aby uzyskać więcej informacji na temat ładowania i używania symboli, zobacz [Określanie symboli (.pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

**Aby ręcznie załadować symbole:**

1. W **oknie** Moduły kliknij prawym przyciskiem myszy moduł, dla którego symbole nie zostały załadowane.

   - Wybierz **pozycję Informacje o ładowanych symbolach,** aby uzyskać szczegółowe informacje o tym, dlaczego symbole nie załadowały się.

   - Wybierz **pozycję Załaduj** symbole, aby ręcznie załadować symbole.

1. Jeśli symbole nie zostaną załadowane, wybierz pozycję **Ustawienia symboli,** aby otworzyć **okno** dialogowe Opcje, a następnie określ lub zmień lokalizacje ładowania symboli.

   Możesz pobrać symbole z publicznych serwerów symboli firmy Microsoft lub innych serwerów albo załadować symbole z folderu na komputerze. Aby uzyskać szczegółowe informacje, [zobacz Określanie lokalizacji symboli i zachowanie podczas ładowania](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior).

**Aby zmienić ustawienia zachowania ładowania symboli:**

1. W **oknie Moduły** kliknij prawym przyciskiem myszy dowolny moduł.

1. Wybierz **pozycję Ustawienia symboli.**

1. Wybierz **pozycję Załaduj wszystkie** symbole lub wybierz moduły, które mają być dołączane lub wykluczane.

1. Wybierz przycisk **OK**. Zmiany zostaną wprowadzone w następnej sesji debugowania.

**Aby zmienić zachowanie ładowania symboli dla określonego modułu:**

1. W **oknie Moduły** kliknij prawym przyciskiem myszy moduł.

1. W menu po kliknięciu prawym przyciskiem myszy wybierz lub usuń zaznaczenie pozycji **Zawsze ładuj automatycznie.** Zmiany zostaną wprowadzone w następnej sesji debugowania.

## <a name="see-also"></a>Zobacz też
- [Wykonywanie przerywania](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))
- [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)
- [Określanie plików symboli (pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)