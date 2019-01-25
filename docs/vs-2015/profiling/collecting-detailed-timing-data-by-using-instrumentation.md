---
title: Zbieranie danych o chronometrażu przy użyciu Instrumentacji | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,instrumentation method
- instrumentation profiling method
ms.assetid: e9deb370-c459-45ac-84d3-14d646590d05
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 595c5f326ba7af25f3b6517f9955db18056e38f9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54794329"
---
# <a name="collecting-detailed-timing-data-by-using-instrumentation"></a>Zbieranie szczegółowych danych o chronometrażu przy użyciu instrumentacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Profiling Tools metoda Instrumentacja wprowadza profilowania kodu do kopii modułu. Ten kod rejestruje każdego wpisu, zakończenia i wywołanie funkcji funkcji w module podczas uruchomienia profilowania. Metoda Instrumentacja jest przydatne do zbierania informacji chronometrażu o sekcji kodu i zrozumienie wpływu na operacje wejścia i wyjścia na wydajność aplikacji.  
  
 Należy określić metody instrumentacji, przy użyciu jednej z następujących procedur:  
  
-   Na pierwszej stronie kreatora profilowania, wybierz **Instrumentacji**.  
  
-   Na **Eksplorator wydajności** narzędzi w **metoda** kliknij **Instrumentacji**.  
  
-   Na **ogólne** strony okna dialogowego właściwości sesji wydajności, wybierz opcję **Instrumentacji**.  
  
## <a name="common-tasks"></a>Typowe zadania  
 Można określić dodatkowe opcje w _sesji wydajności_**stron właściwości** okna dialogowego sesji wydajności. Aby otworzyć to okno dialogowe:  
  
- W **Eksplorator wydajności**, kliknij prawym przyciskiem myszy nazwę sesji wydajności, a następnie kliknij **właściwości**.  
  
  Zadania przedstawione w poniższej tabeli opisano opcje, które można określić w _sesji wydajności_**stron właściwości** okno dialogowe podczas profilowania przy użyciu metody instrumentacji.  
  
|Zadanie|Powiązana zawartość|  
|----------|---------------------|  
|Na **ogólne** strony, Dodaj alokacji pamięci .NET i danych o okresie istnienia, a następnie określ szczegóły nazewnictwa wygenerowany plik danych (Vsp) profilowania.|-   [Zbieranie alokacji pamięci .NET i okres istnienia obiektu](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md)<br />-   [Jak: Ustawianie opcji nazwy pliku danych wydajności](../profiling/how-to-set-performance-data-file-name-options.md)|  
|Na **Uruchom** strony, jeśli masz wiele projektów .exe w solution.specify Twojej aplikacji, aby uruchomić i ich kolejność uruchamiania.|-   [Jak: Określanie plików binarnych do uruchomienia](../profiling/how-to-specify-the-binary-to-start.md)|  
|Na **pliki binarne** Określ lokalizację instrumentowanych kopie modułów. Domyślnie oryginalnych danych binarnych są przenoszone do folderu kopii zapasowej.|-   [Jak: Zmienianie lokalizacji instrumentowanych danych binarnych](../profiling/how-to-relocate-instrumented-binaries.md)|  
|Na **funkcję Tier Interaction** strony, należy dodać danych połączeń ADO.NET do uruchomienia profilowania.|-   [Zbieranie danych o interakcji między warstwami](../profiling/collecting-tier-interaction-data.md)|  
|Na **Instrumentacji** strony, Wyklucz małe funkcje z profilowania, aby zmniejszyć profilowania obciążenie, Profiluj kod JavaScript na stronach sieci Web platformy ASP.NET, a także określić polecenie do uruchomienia w wierszu polecenia przed i po proces instrumentacji.|-   [Jak: Wykluczanie lub uwzględnianie krótkich funkcji z instrumentacji](../profiling/how-to-exclude-or-include-short-functions-from-instrumentation.md)<br />-   [Jak: Profilowanie kodu JavaScript na stronach internetowych](../profiling/how-to-profile-javascript-code-in-web-pages.md)<br />-   [Jak: Określanie poleceń przed i po instrumentacji](../profiling/how-to-specify-pre-and-post-instrument-commands.md)|  
|Na **liczniki CPU** stronie Określ co najmniej jeden licznik wydajności procesora do dodania do danych profilowania.|-   [Jak: Zbieranie danych licznika procesora CPU](../profiling/how-to-collect-cpu-counter-data.md)|  
|Na **zdarzeń Windows** wybierz jedno lub więcej zdarzeń śledzenie zdarzeń dla Windows (ETW) mają być zbierane dane z próbkowania.|-   [Jak: Zbieranie danych śledzenia zdarzeń systemu Windows (ETW)](../profiling/how-to-collect-event-tracing-for-windows-etw-data.md)|  
|Na **liczniki Windows** stronie Określ co najmniej jeden licznik wydajności systemu operacyjnego można dodać do danych profilowania jako znaki.|-   [Jak: Zbieranie danych liczników systemu Windows](../profiling/how-to-collect-windows-counter-data.md)|  
|Na **zaawansowane** Określ dodatkowe opcje, które mają być przekazane do programu Instrumentacji VSInstr, takich jak opcje do dołączania lub wykluczania określonych funkcji.|-   [Jak: Określanie dodatkowych opcji instrumentacji](../profiling/how-to-specify-additional-instrumentation-options.md)<br />-   [Jak: Ograniczanie instrumentacji do określonych funkcji](../profiling/how-to-limit-instrumentation-to-specific-functions.md)<br />-   [Narzędzie VSInstr](../profiling/vsinstr.md)|
