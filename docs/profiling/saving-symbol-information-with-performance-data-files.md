---
title: Zapisywanie informacji o symbolach przy użyciu plików danych dotyczących wydajności | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packsymbols, in profiling tools reports
- profiling tools, packsymbols
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d4cc39f8e07ed0947bedc31ba39d74fc8cee742a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53820332"
---
# <a name="saving-symbol-information-with-performance-data-files"></a>Zapisywanie informacji o symbolach w plików danych dotyczących wydajności

Jeśli używasz środowiska IDE programu Visual Studio do analizowania plików i ma zostać przeniesiona do pliku VSP na innym komputerze, należy ustawić wydajność ustawienia projektu, aby zapisać lub *serializacji* symboli w pliku raportu. Zwiększa rozmiar pliku raportu. Serializacja symboli jest dwóch powodów:

- Aby osadzić symbole kodu do raportu dotyczącego wydajności przed zestawów docelowych zostaną utracone z lokalizacji w magazyn tymczasowy.

- Aby zachować symbole, tak aby raport wydajności jest przenośny z profilowanych komputera i wyświetla te same informacje, jeśli raport jest otwarty w celu analizy na innym komputerze, który może mieć różnych symboli.

Może wykonywać serializację symboli ze środowiska IDE programu Visual Studio lub z wiersza polecenia:

- Do zserializowania symboli w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE, wskaż **narzędzia** na pasku menu, a następnie kliknij przycisk **opcje**. W **opcje** wybierz **narzędzia do oceny wydajności**, a następnie wybierz pozycję **automatycznie serializuj informacje dotyczące symboli** pole wyboru.

- PACKSYMBOLS jest równoważna opcji wiersza polecenia, gdy zapisujesz pliki raportu. Celu zserializowania symboli, wpisz **vsperfreport której packsymbols filename.vsp**.

## <a name="troubleshooting-symbol-problems"></a>Rozwiązywanie problemów z symboli

Jeśli nie ma żadnych symboli we własnym kodzie, dostępne są niektórych typowych rozwiązań:

- Uruchom polecenia vsperfreport debugsympath w wierszu polecenia, aby wyświetlić pełną listę lokalizacji, gdzie składniki programu profilującego są ładowane informacji o symbolach i tego, czy pliki symboli, które są używane takie same jak pliki, które będzie używał Twój projekt.

- Upewnij się, że uruchomiono polecenia vsperfreport z flagą packsymbols lub, w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko projektowe, istnieje możliwość serializacja symbolu informacji wybrany w opcjach explorer ogólnej wydajności.

- Jeśli zostały zebrane dane typu, należy dodać /SUMMARY:TYPE do wiersza polecenia vsperfreport.

  Jeśli nie są widoczne symbole z Windows lub innych programów firmy Microsoft:

- Upewnij się, że zostało ustawione ścieżkę pamięci podręcznej symboli Windows. Wykonaj jedną z następujących czynności, aby ustawić ścieżkę pamięci podręcznej symboli:

  - Zestaw debuger -> symbole w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE do prawidłowej ścieżki.

  - Dodaj opcję - symbolpath do wiersza polecenia VSPerfReport obejmujący symboli.

- Jeśli nie widzisz żadnych symboli w [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], upewnij się, że serwer symboli poprawnie skonfigurowane dla serwera ASP.

## <a name="repacking-symbols"></a>Przepakowaniu symboli

Jeśli chcesz ponownie spakować symboli do raportu, możesz to zrobić za pomocą narzędzia wiersza polecenia VsPerfReport. Użyj następujących wierszy polecenia:

VsPerfReport — clearpackedsymbols filename.vsp

VsPerfReport — packsymbols-summary: all filename.vsp

## <a name="see-also"></a>Zobacz także

[Zapisywanie i eksportowanie danych dotyczących narzędzi do oceny wydajności](../profiling/saving-and-exporting-performance-tools-data.md)  
[Instrukcje: Informacje o symbolach Windows odwołania](../profiling/how-to-reference-windows-symbol-information.md)  
[VSPerfReport](../profiling/vsperfreport.md)