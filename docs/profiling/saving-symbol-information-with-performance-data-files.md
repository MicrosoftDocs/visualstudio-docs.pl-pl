---
title: Zapisywanie informacji o symbolach przy użyciu plików danych o wydajności | Microsoft Docs
description: Dowiedz się, jak można ustawić ustawienia projektu wydajności, aby zapisać lub serializować symbole w pliku raportu.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- packsymbols, in profiling tools reports
- profiling tools, packsymbols
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 142e73a65fa9ffd2210719d84f18a25068762acb
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720218"
---
# <a name="saving-symbol-information-with-performance-data-files"></a>Zapisywanie informacji o symbolach w plikach danych dotyczących wydajności

Jeśli używasz środowiska IDE programu Visual Studio do analizowania plików i planujesz przenieść plik VSP do innego komputera, musisz ustawić ustawienia projektu wydajności, aby zapisać lub *serializować* symbole w pliku raportu. Zwiększa to rozmiar pliku raportu. Serializacja symboli jest konieczna z dwóch powodów:

- Aby osadzić symbole kodu w raporcie wydajności przed utratą zestawów docelowych z ich lokalizacji w magazynie tymczasowym.

- Aby zachować symbole, dzięki czemu raport wydajności jest przenośny z PROFILOWANEGO komputera i wyświetla te same informacje, jeśli raport zostanie otwarty do analizy na innym komputerze, który może mieć różne symbole.

Można serializować symbole z poziomu środowiska IDE programu Visual Studio lub z wiersza polecenia:

- Aby serializować symbole w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE, wskaż **Narzędzia** na pasku menu, a następnie kliknij przycisk **Opcje**. W oknie **Opcje** wybierz pozycję **Narzędzia wydajności**, a następnie zaznacz pole wyboru **automatycznie serializować informacje o symbolach** .

- PACKSYMBOLS jest równoważną opcją wiersza polecenia podczas zapisywania plików raportów. Aby serializować symbole, wpisz **VSPerfReport/Summary: ALL/PACKSYMBOLS filename. vsp**.

## <a name="troubleshooting-symbol-problems"></a>Rozwiązywanie problemów z symbolami

Jeśli nie widzisz żadnych symboli w własnym kodzie, dostępne są niektóre popularne rozwiązania:

- Uruchom VSPerfReport/debugsympath wyświetla w wierszu polecenia, aby wyświetlić pełną listę lokalizacji, w których składniki profilera ładują informacje o symbolach i czy pliki symboli, które są używane, są zgodne z plikami używanymi przez ten projekt.

- Upewnij się, że uruchamiasz VSPerfReport z flagą/PACKSYMBOLS lub, w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE, że wybrano opcję Informacje o symbolach serializacji w ogólnych opcjach Eksploratora wydajności.

- Jeśli zebrano dane typu, Dodaj/SUMMARY: TYPE do VSPerfReport wiersza polecenia.

  Jeśli nie widzisz symboli z okna lub innych programów firmy Microsoft:

- Upewnij się, że ustawiono ścieżkę pamięci podręcznej symboli systemu Windows. Wykonaj jedną z następujących czynności, aby ustawić ścieżkę pamięci podręcznej symboli:

  - Ustaw opcję symboli >debugera w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE na poprawną ścieżkę.

  - Dodaj opcję-SymbolPath — do wiersza polecenia VSPerfReport, aby uwzględnić symbole.

- Jeśli nie widzisz żadnych symboli w programie, upewnij się, [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] że serwer symboli jest prawidłowo skonfigurowany dla serwera ASP.

## <a name="repacking-symbols"></a>Przepakowywanie symboli

Jeśli chcesz ponownie spakować symbole do raportu, możesz to zrobić za pomocą narzędzia wiersza polecenia VsPerfReport. Użyj następujących wierszy poleceń:

VsPerfReport-clearpackedsymbols filename. vsp

VsPerfReport-PACKSYMBOLS-Summary: ALL filename. vsp

## <a name="see-also"></a>Zobacz także

[Zapisywanie i eksportowanie danych](../profiling/saving-and-exporting-performance-tools-data.md) 
 narzędzi wydajności [Instrukcje: odwołania do informacji o](../profiling/how-to-reference-windows-symbol-information.md) 
 symbolach systemu Windows [VSPerfReport](../profiling/vsperfreport.md)
