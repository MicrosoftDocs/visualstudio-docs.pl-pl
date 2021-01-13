---
title: Wyświetlanie bibliotek DLL i plików wykonywalnych
description: Wyświetlanie bibliotek DLL i plików wykonywalnych (pliki exe) używanych przez aplikację w oknie modułów podczas sesji debugowania w programie Visual Studio.
ms.custom: SEO-VS-2020, seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0471aa25b14111271e6f9219e8e849eed49f113f
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150564"
---
# <a name="view-dlls-and-executables-in-the-modules-window-c-c-visual-basic-f"></a>Wyświetlanie bibliotek DLL i plików wykonywalnych w oknie modułów (C#, C++, Visual Basic, F #)

Podczas debugowania programu Visual Studio okna **moduły** wyświetlają i wyświetlają informacje o bibliotekach DLL i plikach wykonywalnych (pliki *exe* ) używane przez aplikację.

> [!NOTE]
> Okno moduły nie jest dostępne na potrzeby debugowania kodu SQL lub skryptu.

## <a name="use-the-modules-window"></a>Korzystanie z okna moduły

Aby otworzyć okno moduły, podczas debugowania wybierz kolejno opcje **Debuguj**  >  **moduły systemu Windows**  >   (lub naciśnij **klawisze CTRL + ALT + U**).

Domyślnie okno **moduły** sortuje moduły według kolejności ładowania. Aby posortować według dowolnej kolumny okna, zaznacz nagłówek w górnej części kolumny.

## <a name="load-symbols"></a>Załaduj symbole

Kolumna **stan symbolu** w oknie **moduły** pokazuje, które moduły mają załadowane symbole debugowania. Jeśli stan jest **pominięty podczas ładowania symboli**, **nie można znaleźć lub otworzyć pliku PDB** lub załadować **wyłączone przez ustawienie Uwzględnij/Wyklucz**, można załadować symbole ręcznie. Aby uzyskać więcej informacji na temat ładowania i używania symboli, zobacz [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

**Aby ręcznie załadować symbole:**

1. W oknie **moduły** kliknij prawym przyciskiem myszy moduł, dla którego symbole nie zostały załadowane.

   - Wybierz pozycję **Informacje o ładowaniu symboli** , aby uzyskać szczegółowe informacje o tym, dlaczego symbole nie zostały załadowane.

   - Wybierz pozycję **Załaduj symbole** , aby ręcznie załadować symbole.

1. Jeśli symbole nie są ładowane, wybierz pozycję **Ustawienia symboli** , aby otworzyć okno dialogowe **Opcje** i określić lub zmienić lokalizacje ładowania symboli.

   Możesz pobrać symbole z publicznych serwerów symboli firmy Microsoft lub innych serwerów, lub załadować symbole z folderu na komputerze. Aby uzyskać szczegółowe informacje, zobacz [Określanie lokalizacji symboli i zachowanie ładowania](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior).

**Aby zmienić ustawienia zachowania ładowania symboli:**

1. W oknie **moduły** kliknij prawym przyciskiem myszy dowolny moduł.

1. Wybierz pozycję **Ustawienia symboli**.

1. Wybierz pozycję **Załaduj wszystkie symbole** lub wybierz moduły do dołączenia lub wykluczenia.

1. Wybierz pozycję **OK**. Zmiany zaczną obowiązywać w następnej sesji debugowania.

**Aby zmienić zachowanie ładowania symboli dla określonego modułu:**

1. W oknie **moduły** kliknij prawym przyciskiem myszy moduł.

1. W menu rozwijanym prawym przyciskiem myszy zaznacz lub usuń zaznaczenie opcji **Zawsze ładuj automatycznie**. Zmiany zaczną obowiązywać w następnej sesji debugowania.

## <a name="see-also"></a>Zobacz także
- [Przerywanie wykonywania](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))
- [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)
- [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)