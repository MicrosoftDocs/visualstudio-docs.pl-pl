---
title: Zapisywanie informacji o symbolach za pomocą plików danych wydajności | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 74137752900d082c545dd5e5271b7700ec81fa01
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778300"
---
# <a name="saving-symbol-information-with-performance-data-files"></a>Zapisywanie informacji o symbolach w plikach danych dotyczących wydajności

Jeśli używasz ide programu Visual Studio do analizowania plików i planujesz przenieść plik VSP na inny komputer, należy ustawić ustawienia projektu wydajności, aby zapisać lub *serializować* symbole w pliku raportu. Zwiększa to rozmiar pliku raportu. Serializacja symboli jest konieczna z dwóch powodów:

- Aby osadzać symbole kodu w raporcie wydajności, zanim zestawy docelowe zostaną utracone z ich lokalizacji w magazynie tymczasowym.

- Aby zachować symbole, tak aby raport wydajności jest przenośny z profilowanego komputera i wyprowadza te same informacje, jeśli raport jest otwarty do analizy na innym komputerze, który może mieć różne symbole.

Symbole można serializować z ide programu Visual Studio lub z wiersza polecenia:

- Aby serializować symbole w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDEI, wskaż polecenie **Narzędzia** na pasku menu, a następnie kliknij przycisk **Opcje**. W oknie **Opcje** wybierz pozycję **Narzędzia wydajności**, a następnie zaznacz pole wyboru **Automatycznie serializować informacje o symbolu.**

- PACKSYMBOLS jest równoważną opcją wiersza polecenia podczas zapisywania plików raportu. Aby serializować symbole, wpisz **vsperfreport /summary:all /packsymbols filename.vsp**.

## <a name="troubleshooting-symbol-problems"></a>Rozwiązywanie problemów z symbolami

Jeśli nie widzisz żadnych symboli we własnym kodzie, dostępne są niektóre typowe rozwiązania:

- Uruchom vsperfreport /debugsympath w wierszu polecenia, aby wyświetlić pełną listę lokalizacji, w których składniki profilera ładują informacje o symbolach i czy używane pliki symboli są zgodne z plikami używanymi w projekcie.

- Upewnij się, że uruchomisz vsperfreport z flagą /PACKSYMBOLS lub w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE, że masz opcję informacji o symbolu serializacji wybraną w opcjach eksploratora wydajności ogólnej.

- Jeśli zebrano dane tekstowe, dodaj /SUMMARY:TYPE do wiersza polecenia vsperfreport.

  Jeśli nie widzisz symboli z systemu Windows lub innych programów firmy Microsoft:

- Upewnij się, że ustawiono ścieżkę pamięci podręcznej symboli systemu Windows. Wykonaj jedną z następujących czynności, aby ustawić ścieżkę pamięci podręcznej symboli:

  - Ustaw debuger->symbole w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE do poprawnej ścieżki.

  - Dodaj opcję -symbolpath do wiersza polecenia VSPerfReport, aby uwzględnić symbole.

- Jeśli nie widzisz żadnych symboli w [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], upewnij się, że serwer symboli został poprawnie skonfigurowany dla serwera ASP.

## <a name="repacking-symbols"></a>Przepakowywanie symboli

Jeśli chcesz przepakować symbole do raportu, możesz to zrobić za pomocą narzędzia wiersza polecenia VsPerfReport. Użyj następujących wierszy polecenia:

VsPerfReport -clearpackedsymbols nazwa pliku.vsp

VsPerfReport -packsymbols -summary:all filename.vsp

## <a name="see-also"></a>Zobacz też

[Zapisywanie i eksportowanie danych](../profiling/saving-and-exporting-performance-tools-data.md)
narzędzi wydajności[Jak: Odwołanie do informacji o](../profiling/how-to-reference-windows-symbol-information.md)
symbolu systemu Windows[VSPerfReport](../profiling/vsperfreport.md)
