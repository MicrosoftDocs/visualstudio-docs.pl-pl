---
title: Zbieranie statystyk wydajności za pomocą metody pobierania próbek | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439036"
---
# <a name="collecting-performance-statistics-by-using-sampling"></a>Zbieranie statystyk wydajności za pomocą metody pobierania próbek
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Domyślnie [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] metody pobierania próbek Profiling Tools są zbierane informacje profilowania co 10 000 000 cykli procesora (mniej więcej co setną chwilę na komputerze, 1 GHz). Metoda pobierania próbek jest przydatny do znajdowania problemy dotyczące użycia procesora i Sugerowane metody uruchamiania większość badania wydajności.  
  
 **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
> Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje Windows Store również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Metoda pobierania próbek można określić przy użyciu jednej z następujących procedur:  
  
- Na pierwszej stronie kreatora profilowania, kliknij przycisk **próbkowania Procesora (zalecane)**.  
  
- Na **Eksplorator wydajności** narzędzi w **metoda** kliknij **próbkowania**.  
  
- Na **ogólne** strony okna dialogowego właściwości sesji wydajności, kliknij przycisk **próbkowania**.  
  
## <a name="common-tasks"></a>Typowe zadania  
 Można określić dodatkowe opcje w _sesji wydajności_**stron właściwości** okna dialogowego sesji wydajności. Aby otworzyć to okno dialogowe:  
  
- W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij **właściwości**.  
  
  Zadania przedstawione w poniższej tabeli opisano opcje, które można określić w _sesji wydajności_**stron właściwości** okno dialogowe podczas profilowania przy użyciu metody próbkowania.  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|Na **ogólne** strony, Dodaj alokacji pamięci .NET i zbieranie danych okresu istnienia i określ szczegóły nazewnictwa wygenerowany plik danych (Vsp) profilowania.|-   [Zbieranie alokacji pamięci .NET i okres istnienia obiektu](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Jak: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Na **próbkowania** strony, zmienić częstotliwość próbkowania, zmienić zdarzenie próbkowania cykli zegara procesora na inny licznik wydajności procesora lub zmianę tych poświadczeń...|-   [Jak: Wybieranie zdarzeń próbkowania](../profiling/how-to-choose-sampling-events.md)|  
|Na **Uruchom** Określ aplikację do uruchomienia i rozpoczęcia zlecenia, jeśli masz wiele projektów .exe w rozwiązaniu kodu.|-   [Zbieranie danych o interakcji między warstwami](../profiling/collecting-tier-interaction-data.md)|  
|Na **funkcję Tier Interaction** strony, Dodaj informacje o wywołaniach ADO.NET danych zebranych podczas uruchomienia theprofiling.|-   [Zbieranie danych o interakcji między warstwami](../profiling/collecting-tier-interaction-data.md)|  
|Na **zdarzeń Windows** Określ jedno lub więcej zdarzeń śledzenie zdarzeń dla Windows (ETW) mają być zbierane dane z próbkowania.|-   [Jak: Zbieranie danych śledzenia zdarzeń systemu Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|Na **liczniki Windows** stronie Określ co najmniej jeden licznik wydajności systemu operacyjnego można dodać do danych profilowania jako znaki.|-   [Jak: Zbieranie danych liczników systemu Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|Na **zaawansowane** Określ wersję środowiska uruchomieniowego .NET Framework do profilowania, jeśli moduły aplikacji używać wielu wersji. Domyślnie jest profilowane pierwszej wersji załadowane.|-   [Jak: Określanie środowiska uruchomieniowego programu .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|
