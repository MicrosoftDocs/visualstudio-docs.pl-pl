---
title: Zbieranie alokacji pamięci .NET i danych o okresie istnienia | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- .NET memory profiling method
- Profiling Tools,.NET memory method
ms.assetid: 62a6dd5f-db66-4456-9d57-f8913dbfe4d5
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 232707cd8fa51b8b69c67e1e66cb0790f4938031
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54794218"
---
# <a name="collecting-net-memory-allocation-and-lifetime-data"></a>Zbieranie alokacji pamięci .NET i okres istnienia obiektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Narzędzia profilowania obsługują zbieranie alokacji pamięci .NET i danych o okresie istnienia obiektu, który ułatwia wykrywanie problemów z wydajnością związane z pamięcią w aplikacji.  
  
- Dane o alokacji pamięci .NET zawiera, rozmiar i liczba przydzielonych obiektów pamięci .NET Framework.  
  
- Danych o okresie istnienia obiektu zawiera, rozmiar i liczba obiektów pamięci .NET Framework, które zostały odzyskane w trzy generacje wyrzucania elementów w kolekcji.  
  
  **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
> [!NOTE]
>  Ulepszone funkcje zabezpieczeń w systemie Windows 8 i Windows Server 2012 wymagają znaczących zmian w taki sposób, programu Visual Studio profiler zbiera dane na tych platformach. Aplikacje Windows Store również wymagają nowych technik zbierania. Zobacz [narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
  
 Za pomocą pobierania próbek lub metoda profilowania Instrumentacja może zbierać dane.  
  
-   Przy użyciu metody próbkowania profilera śledzi wszystkie alokacje pamięci .NET i obiekty, które są generowane przez proces, który został uruchomiony lub dołączone do.  
  
-   Przy użyciu metody Instrumentacji profilera umożliwia śledzenie tylko alokacji pamięci .NET i obiekty, które są generowane przez moduły instrumentowanych.  
  
> [!IMPORTANT]
>  Zbierając dane pamięci platformy .NET (alokacji, czasów istnienia obiektów lub obie) przy użyciu metody próbkowania, wszystkie zdarzenia próbkowania określone przez użytkownika są ignorowane, a zdarzenia alokacji odpowiedniej ilości pamięci są używane do zbierania danych.  
  
 Włączenie profilowania alokacji pamięci of.NET, możesz również włączyć widok alokacji. Włączenie profilowania danych o okresie istnienia .NET, możesz również włączyć widok okresu istnienia obiektów. Aby uzyskać więcej informacji, zobacz [Widok alokacji](../profiling/dotnet-memory-allocations-view.md) i [widok okresu istnienia obiektu](../profiling/object-lifetime-view.md).  
  
 Aby dowiedzieć się, jak zbierać dane pamięci platformy .NET przy użyciu narzędzi wiersza poleceń Profiling Tools, zobacz przy użyciu metod pamięci .NET w celu zbierania alokacji pamięci i danych o okresie istnienia obiektu w [przy użyciu profilowania metody z wiersza polecenia](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).  
  
### <a name="to-collect-net-memory-data"></a>Do zbierania danych pamięci .NET  
  
1.  W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy sesję wydajności, a następnie kliknij **właściwości**.  
  
2.  Na _sesji wydajności_**stron właściwości** okno dialogowe, kliknij przycisk **ogólne** , a następnie wybierz pozycję **.NET zbierać informacje dotyczące alokacji obiektów** pole wyboru.  
  
3.  Do zbierania danych o okresie istnienia obiektu platformy .NET, wybierz **również zbierać informacje dotyczące okresu istnienia obiektu platformy .NET** pole wyboru.  
  
## <a name="common-tasks"></a>Typowe zadania  
 Można określić dodatkowe opcje w _sesji wydajności_**stron właściwości** okna dialogowego sesji wydajności. Aby otworzyć to okno dialogowe:  
  
- W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij **właściwości**.  
  
  Zadania przedstawione w poniższej tabeli opisano opcje, które można określić w _sesji wydajności_**stron właściwości** okno dialogowe podczas zbierania danych pamięci .NET.  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|Na **ogólne** Określ szczegóły nazewnictwa dla wygenerowanego pliku danych (Vsp) profilowania.|-   [Zbieranie alokacji pamięci .NET i okres istnienia obiektu](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Jak: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Na **Uruchom** wybierz aplikację do uruchomienia, jeśli masz wiele projektów .exe w rozwiązaniu kodu.|-   [Zbieranie danych o interakcji między warstwami](../profiling/collecting-tier-interaction-data.md)|  
|Na **funkcję Tier Interaction** strony, należy dodać danych połączeń ADO.NET do uruchomienia profilowania.|-   [Zbieranie danych o interakcji między warstwami](../profiling/collecting-tier-interaction-data.md)|  
|Na **zdarzeń Windows** Określ jedno lub więcej zdarzeń śledzenie zdarzeń dla Windows (ETW) mają być zbierane dane z próbkowania.|-   [Jak: Zbieranie danych śledzenia zdarzeń systemu Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|Na **liczniki Windows** stronie Określ co najmniej jeden licznik wydajności systemu operacyjnego można dodać do danych profilowania jako znaki.|-   [Jak: Zbieranie danych liczników systemu Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|Na **zaawansowane** Określ wersję środowiska uruchomieniowego .NET Framework do profilowania, jeśli moduły aplikacji używać wielu wersji. Domyślnie jest profilowane pierwszej wersji załadowane.|-   [Jak: Określanie środowiska uruchomieniowego programu .NET Framework](../profiling/how-to-specify-the-dotnet-framework-runtime.md)|  
  
## <a name="instrumentation-tasks"></a>Zadania Instrumentacji  
 Zadania przedstawione w poniższej tabeli są opcje w **stron właściwości** okno dialogowe, które są specyficzne dla profilowania przy użyciu metody instrumentacji.  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|Na **pliki binarne** Określ lokalizację instrumentowanych kopie modułów. Domyślnie oryginalnych danych binarnych są przenoszone do folderu kopii zapasowej.|-   [Jak: Zmienianie lokalizacji instrumentowanych danych binarnych](../profiling/how-to-relocate-instrumented-binaries.md)|  
|Na **Instrumentacji** strony, Wyklucz małe funkcje z profilowania, aby zmniejszyć profilowania obciążenie, Profiluj kod JavaScript na stronach sieci Web platformy ASP.NET, a także określić polecenie do uruchomienia w wierszu polecenia przed i po proces instrumentacji.|-   [Jak: Wykluczanie lub uwzględnianie krótkich funkcji z instrumentacji](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Jak: Profilowanie kodu JavaScript na stronach internetowych](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Jak: Określanie poleceń przed i po instrumentacji](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|  
|Na **liczniki CPU** stronie Określ co najmniej jeden licznik wydajności procesora do dodania do danych profilowania.|-   [Jak: Zbieranie danych licznika procesora CPU](../profiling/how-to-collect-cpu-counter-data.md)|  
|Na **zaawansowane** określ wszelkie dodatkowe VSInstr.exe żądane opcje, takie jak opcje do dołączania lub wykluczania określonych funkcji. Aby uzyskać więcej informacji na temat opcji VSInstr zobacz [VSInstr](../profiling/vsinstr.md)|-   [Jak: Określanie dodatkowych opcji instrumentacji](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Jak: Ograniczanie instrumentacji do określonych funkcji](../profiling/how-to-limit-instrumentation-to-specific-functions.md)|  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie sesji wydajności](../profiling/configuring-performance-sessions.md)   
 [Instrukcje: Wybieranie metod kolekcji](../profiling/how-to-choose-collection-methods.md)   
 [Właściwości sesji wydajności](../profiling/performance-session-properties.md)
