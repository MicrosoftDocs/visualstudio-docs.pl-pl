---
title: 'Instrukcje: Debugowanie źródła .NET Framework | Dokumentacja firmy Microsoft'
ms.date: 11/19/2018
ms.topic: conceptual
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 430f50c1ccac8ea7e9cc02dd117dda1048747aba
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55019310"
---
# <a name="how-to-debug-net-framework-source"></a>Instrukcje: Debugowanie źródła programu .NET Framework

Aby debugować źródła .NET Framework, musisz mieć:

- Włącz przechodzenie krok po kroku do źródła .NET Framework.  
  
- Mają dostęp do symboli debugowania dla kodu. 
  
  Użytkownik chce pobrać symboli debugowania natychmiast lub ustawianie opcji późniejszego pobrania. Jeśli nie od razu pobrać symbole, pobierają przy następnym uruchomieniu debugowania aplikacji. Podczas debugowania, możesz również użyć **modułów** lub **stos wywołań** systemu windows, aby pobrać i załadować symbole.  
  
### <a name="to-enable-stepping-into-net-framework-source"></a>Aby umożliwić stepping do źródła .NET Framework 
  
1. W obszarze **narzędzia** (lub **debugowania**) > **opcje** > **debugowania** > **ogólne**, wybierz opcję **Włącz .NET Framework źródła stepping**.  
   
   - Jeśli masz włączoną opcję tylko mój kod, okno dialogowe ostrzeżenia informuje, że tylko mój kod jest teraz wyłączony. Kliknij przycisk **OK**.  
   
   - Jeśli nie masz pamięci podręcznej symboli zestawu, okno dialogowe ostrzeżenia informuje, że ustawiono domyślny pamięci podręcznej symboli. Kliknij przycisk **OK**.  
   
1. Wybierz **OK** zamknąć **opcje** okna dialogowego.
  
### <a name="to-set-or-change-symbol-source-locations-and-loading-behavior"></a>Aby ustawić lub zmienić lokalizacje źródłowe symboli i zachowanie ładowania

1. Wybierz **symbole** kategorię w obszarze **narzędzia** (lub **debugowania**) > **opcje** > **debugowanie**.  
  
1. Na **symbole** w obszarze **symboli (.pdb) lokalizacji**, wybierz opcję **serwery symboli firmy Microsoft** symbole dostępu z publicznych serwerów symboli firmy Microsoft. Wybierz przyciski paska narzędzi, aby dodać inne lokalizacje symboli i zmienić kolejność ładowania. 
   
1. Aby zmienić pamięć podręczną symboli lokalnych, edytować, lub przejdź do innej lokalizacji w obszarze **pamięci podręcznej symboli w tym katalogu**.  
   
1. Aby pobrać symbole natychmiast, zaznacz **Załaduj wszystkie symbole**. Ten przycisk jest dostępny tylko podczas debugowania.  
   
   Jeśli nie można pobrać symboli teraz, one będą pobierane przy następnym uruchomieniu debugowania.  
   
1. Wybierz **OK** zamknąć **opcje** okna dialogowego.  
  
### <a name="to-load-symbols-from-the-modules-or-call-stack-windows"></a>Aby załadować symbole z modułów lub stos wywołań systemu windows  
  
1. Podczas debugowania, Otwórz okno, wybierając **debugowania** > **Windows** > **modułów** (lub naciśnij **Ctrl + Alt + U**) lub **debugowania** > **Windows** > **stos wywołań** (**Ctrl + Alt + C**). 
   
1. Kliknij prawym przyciskiem myszy moduł, dla którego nie załadowano symboli. W **modułów** oknie symbol podczas ładowania stanu jest **stan symboli** kolumny. W **stos wywołań** oknie Stan jest **stan ramki** kolumny i ramki jest wyszarzona. 
   
   - Wybierz **załadować symbole** menu do lokalizowania i ładowania plików symboli z folderu na komputerze. 
   
   - Wybierz **informacje o ładowaniu symboli** do wyświetlenia w lokalizacjach, debuger wyszukiwane symboli.  
   
   - Wybierz **ustawienia symboli** otworzyć **symbole** strony. Na **symbole** w obszarze **symboli (.pdb) lokalizacji**, wybierz opcję **serwery symboli firmy Microsoft** symbole dostępu z publicznych serwerów symboli firmy Microsoft. Wybierz przyciski paska narzędzi, aby dodać inne lokalizacje symboli i zmienić kolejność ładowania. Wybierz **OK** aby zamknąć okno dialogowe. 
  
### <a name="see-also"></a>Zobacz także  
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)   
 [Określanie plików symboli (.pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)