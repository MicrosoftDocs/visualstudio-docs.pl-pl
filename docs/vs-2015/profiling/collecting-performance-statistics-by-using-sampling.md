---
title: Zbieranie statystyk wydajności przy użyciu próbkowania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,sampling
- sampling profiling method
ms.assetid: 8e36361b-bb3d-40c6-b286-0e68c0ecb915
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0b84674eafde85528e04157ab213913e57d27e60
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64831106"
---
# <a name="collecting-performance-statistics-by-using-sampling"></a>Zbieranie statystyk wydajności za pomocą metody pobierania próbek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Domyślnie [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] Metoda próbkowania narzędzia profilowania zbiera informacje o profilach co 10 000 000 cykli procesora (około każdej jednej setnej sekundy na komputerze z 1 GHz). Metoda próbkowania jest przydatna do znajdowania problemów z użyciem procesora i jest sugerowaną metodą uruchamiania większości badań wydajności.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemach Windows 8 i Windows Server 2012 wymagały znaczących zmian w sposobie, w jaki program Visual Studio profiler zbiera dane na tych platformach. Aplikacje ze sklepu Windows wymagają również nowych technik zbierania danych. Zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Metodę próbkowania można określić za pomocą jednej z następujących procedur:  
  
- Na pierwszej stronie kreatora profilowania kliknij pozycję **próbkowanie procesora (zalecane)**.  
  
- Na **Eksplorator wydajności** pasku narzędzi na liście **Metoda** kliknij pozycję **próbkowanie**.  
  
- Na stronie **Ogólne** okna dialogowego właściwości sesji wydajności kliknij polecenie **próbkowanie**.  
  
## <a name="common-tasks"></a>Typowe zadania  
 Dodatkowe opcje można określić w oknie dialogowym _Performance Session_**strony właściwości** sesji wydajności. Aby otworzyć to okno dialogowe:  
  
- W **Eksplorator wydajności**kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij polecenie **Właściwości**.  
  
  Zadania w poniższej tabeli opisują opcje, które można określić w oknie dialogowym**strony właściwości** _sesji wydajności_podczas profilowania przy użyciu metody próbkowania.  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|Na stronie **Ogólne** Dodaj przydział pamięci platformy .NET i zbieranie danych o okresie istnienia, a następnie określ szczegóły nazewnictwa dla wygenerowanego pliku danych profilowania (. vsp).|-   [Zbieranie danych alokacji pamięci .NET i okresu istnienia](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Instrukcje: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Na stronie **próbkowanie** Zmień częstotliwość próbkowania, Zmień zdarzenie próbkowania z cykli zegara procesora na inny licznik wydajności procesora lub Zmień oba te parametry.|-   [Instrukcje: Wybieranie zdarzeń próbkowania](../profiling/how-to-choose-sampling-events.md)|  
|Na stronie **Uruchamianie** Określ aplikację do uruchomienia i kolejność uruchamiania, jeśli masz wiele projektów. exe w rozwiązaniu kodu.|-   [Zbieranie danych o interakcji między warstwami](../profiling/collecting-tier-interaction-data.md)|  
|Na stronie **interakcja warstwy** Dodaj informacje o wywołaniu ADO.NET do danych zebranych w theprofiling przebiegu.|-   [Zbieranie danych o interakcji między warstwami](../profiling/collecting-tier-interaction-data.md)|  
|Na stronie **zdarzenia systemu Windows** Określ jedno lub więcej zdarzeń śledzenia zdarzeń systemu Windows (ETW), które mają być zbierane z danymi próbkowania.|-   [Instrukcje: zbieranie danych śledzenia zdarzeń dla systemu Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|Na stronie **liczniki systemu Windows** Określ co najmniej jeden licznik wydajności systemu operacyjnego, który ma zostać dodany do danych profilowania jako znaczniki.|-   [Instrukcje: zbieranie danych licznika systemu Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|Na stronie **Zaawansowane** Określ wersję środowiska uruchomieniowego .NET Framework, która ma być używana do profilowania, jeśli moduły aplikacji korzystają z wielu wersji. Domyślnie pierwsza ładowana wersja jest profilowana.|-   [Instrukcje: Określanie środowiska uruchomieniowego .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
