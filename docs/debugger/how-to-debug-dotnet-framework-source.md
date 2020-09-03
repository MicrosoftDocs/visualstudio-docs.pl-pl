---
title: Jak debugować źródło .NET Framework | Microsoft Docs
ms.date: 11/19/2018
ms.topic: how-to
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3f043aae44231608fb514e87a05717f4aeb924bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350098"
---
# <a name="how-to-debug-net-framework-source"></a>Instrukcje: debugowanie źródła .NET Framework

Aby debugować źródło .NET Framework, musisz:

- Włącz krokowe przechodzenie do .NET Framework źródła.

- Mieć dostęp do symboli debugowania dla kodu.

  Możesz wybrać opcję pobrania symboli debugowania natychmiast lub ustawić opcje do późniejszego pobrania. Jeśli symbole nie zostaną pobrane natychmiast, zostaną pobrane przy następnym uruchomieniu debugowania aplikacji. Podczas debugowania można także użyć **modułów** lub okien **stosu wywołań** do pobierania i ładowania symboli.

### <a name="to-enable-stepping-into-net-framework-source"></a>Aby włączyć przechodzenie do .NET Framework źródła

1. W obszarze **Narzędzia** (lub **Debuguj**) > **Opcje**  >  **debugowania**  >  **Ogólne**wybierz pozycję **Włącz .NET Framework Źródło**.

   - Jeśli Tylko mój kod włączone, okno dialogowe ostrzeżenia informuje, że Tylko mój kod jest teraz wyłączone. Wybierz pozycję **OK**.

   - Jeśli nie masz ustawionej lokalnej pamięci podręcznej symboli, okno dialogowe ostrzeżenia informuje, że ustawiono domyślną pamięć podręczną symboli. Wybierz pozycję **OK**.

1. Wybierz **przycisk OK** , aby zamknąć okno dialogowe **Opcje** .

### <a name="to-set-or-change-symbol-source-locations-and-loading-behavior"></a>Aby ustawić lub zmienić lokalizację źródłową symboli i zachowanie ładowania

1. Wybierz kategorię **symbole** w obszarze **Narzędzia** (lub **Debuguj**) > **Options**  >  **debugowanie**opcji.

1. Na stronie **symbole** w obszarze **lokalizacje pliku symboli (. pdb)** wybierz pozycję **serwery symboli firmy Microsoft** , aby uzyskać dostęp do symboli z publicznych serwerów symboli firmy Microsoft. Wybierz przyciski paska narzędzi, aby dodać inne lokalizacje symboli i zmienić kolejność ładowania.

1. Aby zmienić pamięć podręczną symboli lokalnych, edytuj lub przejdź do innej lokalizacji w obszarze **symbole pamięci podręcznej w tym katalogu**.

1. Aby natychmiast pobrać symbole, wybierz pozycję **Załaduj wszystkie symbole**. Ten przycisk jest dostępny tylko podczas debugowania.

   Jeśli nie pobierzesz symboli teraz, zostaną one pobrane przy następnym uruchomieniu debugowania.

1. Wybierz **przycisk OK** , aby zamknąć okno dialogowe **Opcje** .

### <a name="to-load-symbols-from-the-modules-or-call-stack-windows"></a>Aby załadować symbole z modułów lub okien stosu wywołań

1. Podczas debugowania Otwórz okno, wybierając kolejno **opcje Debuguj**  >  **moduły systemu Windows**  >  **Modules** (lub naciśnij **klawisze CTRL + ALT + U**) lub **Debuguj**  >  **Windows**  >  **stos wywołań** systemu Windows (**Ctrl + Alt + C**).

1. Kliknij prawym przyciskiem myszy moduł, dla którego symbole nie zostały załadowane. W oknie **moduły** stan ładowania symboli znajduje się w kolumnie **Stan symboli** . W oknie **stos wywołań** stan znajduje się w kolumnie **stan ramki** i ramka jest wyszarzona.

   - Wybierz pozycję **Załaduj symbole** z menu, aby zlokalizować i załadować pliki symboli z folderu na komputerze.

   - Wybierz pozycję **Informacje o ładowaniu symboli** , aby pokazać lokalizacje, w których debuger szuka symboli.

   - Wybierz pozycję **Ustawienia symboli** , aby otworzyć stronę **symbole** . Na stronie **symbole** w obszarze **lokalizacje pliku symboli (. pdb)** wybierz pozycję **serwery symboli firmy Microsoft** , aby uzyskać dostęp do symboli z publicznych serwerów symboli firmy Microsoft. Wybierz przyciski paska narzędzi, aby dodać inne lokalizacje symboli i zmienić kolejność ładowania. Wybierz **przycisk OK** , aby zamknąć okno dialogowe.

### <a name="see-also"></a>Zobacz też
- [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)
- [Określanie symboli (. pdb) i plików źródłowych](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)