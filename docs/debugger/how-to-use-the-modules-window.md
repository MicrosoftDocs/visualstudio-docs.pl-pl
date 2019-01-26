---
title: Wyświetlanie plików dll i plików wykonywalnych
titleSuffix: Visual Studio Modules window
ms.custom: seodec18
ms.date: 11/04/2018
ms.topic: conceptual
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
ms.openlocfilehash: cd628869d8a642cc6debad726f6c82df71a3b1ba
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55014032"
---
# <a name="view-dlls-and-executables-in-the-modules-window-c-c-visual-basic-f"></a>Wyświetlanie plików dll i pliki wykonywalne w oknie modułów (C#, C++, Visual Basic F#)
 
Podczas debugowania programu Visual Studio, **modułów** okno wyświetla i zawiera informacje o bibliotekach DLL i plików wykonywalnych (*.exe* pliki) używany przez aplikację. 

> [!NOTE]
> Okno modułów nie jest dostępna dla bazy danych SQL lub debugowania skryptu. 
  
## <a name="use-the-modules-window"></a>Korzystanie z okna modułów

Aby otworzyć okno modułów podczas debugowania, wybierz **debugowania** > **Windows** > **modułów** (lub naciśnij **Ctrl + Alt + U** ). 
  
Domyślnie **modułów** okna sortuje moduły według kolejności ładowania. Aby sortować według dowolnej kolumny okna, wybierz nagłówek w górnej części kolumny.  
  
## <a name="load-symbols"></a>Załaduj symbole  

**Stan symboli** kolumny w **modułów** okno pokazuje, które moduły mają załadowane symbole debugowania. Jeśli stan jest **pominięto ładowanie symboli**, **nie można odnaleźć lub otworzyć pliku PDB**, lub **ładowanie wyłączone przez ustawienie dołączania lub wykluczania**, ręcznie załadować symbole. Aby uzyskać więcej informacji na temat ładowania i używania symboli, zobacz [określanie plików symboli (.pdb) i pliki źródłowe](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

**Aby ręcznie załadować symbole:**  

1. W **modułów** okna, kliknij prawym przyciskiem myszy moduł, dla której symbole nie zostały załadowane. 
   
   - Wybierz **załadować informacji o symbolach w** szczegółowe informacje na temat przyczyn nie zostały załadowane symbole. 
   
   - Wybierz **załadować symbole** ręcznie załadować symbole.  
   
1. Jeśli nie można załadować symboli, wybierz **ustawienia symboli** otworzyć **opcje** okno dialogowe i określ lub Zmień lokalizacje ładowania symboli. 
   
   Możesz pobrać symbole z publicznych serwerów symboli firmy Microsoft lub innych serwerów lub załaduj symbole z folderu na komputerze. Aby uzyskać więcej informacji, zobacz [Określ lokalizacje symboli i zachowanie ładowania](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior).   

**Aby zmienić ustawienia zachowania ładowania symboli:**  

1. W **modułów** okna, kliknij prawym przyciskiem myszy dowolny moduł.  
   
1. Wybierz **ustawienia symboli**.  
  
1. Wybierz **Załaduj wszystkie symbole**, lub wybierz które moduły do dołączania lub wykluczania.  
  
1. Wybierz **OK**. Zmiany wprowadzone w następnej sesji debugowania.  
  
**Aby zmienić zachowanie określonego modułu ładowania symboli:**  

1.  W **modułów** okna, kliknij prawym przyciskiem myszy moduł.  

1.  W menu kliknij prawym przyciskiem myszy, zaznacz lub odznacz opcję **zawsze obciążenia automatycznie**. Zmiany wprowadzone w następnej sesji debugowania.  
  
## <a name="see-also"></a>Zobacz także  
 [Przerwanie wykonywania](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))   
 [Wyświetlanie danych w debugerze](../debugger/viewing-data-in-the-debugger.md)   
 [Określanie plików symboli (.pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)