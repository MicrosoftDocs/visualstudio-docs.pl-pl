---
title: Zapisywanie informacji o symbolach przy użyciu plików danych dotyczących wydajności | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- packsymbols, in profiling tools reports
- profiling tools, packsymbols
ms.assetid: 8b802505-e94d-4ee0-83e4-fdd790a332c1
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e9d2e8b0414746523d0f76e8266f6463d9c05574
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68160295"
---
# <a name="saving-symbol-information-with-performance-data-files"></a>Zapisywanie informacji o symbolach w plikach danych dotyczących wydajności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli używasz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE) do przeanalizowania plików i planujesz przenoszenia pliku VSP na innym komputerze, należy ustawić wydajność ustawienia projektu, aby zapisać lub *serializacji* symboli w Plik raportu. Zwiększa rozmiar pliku raportu. Serializacja symboli jest dwóch powodów:  
  
- Aby osadzić symbole kodu do raportu dotyczącego wydajności przed zestawów docelowych zostaną utracone z lokalizacji w magazyn tymczasowy.  
  
- Aby zachować symbole, tak aby raport wydajności jest przenośny z profilowanych komputera i wyświetla te same informacje, jeśli raport jest otwarty w celu analizy na innym komputerze, który może mieć różnych symboli.  
  
  **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Może wykonywać serializację symbole z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] środowiska IDE lub z wiersza polecenia:  
  
- Do zserializowania symboli w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE, wskaż **narzędzia** na pasku menu, a następnie kliknij przycisk **opcje**. W **opcje** wybierz **narzędzia do oceny wydajności**, a następnie wybierz pozycję **automatycznie serializuj informacje dotyczące symboli** pole wyboru.  
  
- PACKSYMBOLS jest równoważna opcji wiersza polecenia, gdy zapisujesz pliki raportu. Celu zserializowania symboli, wpisz **vsperfreport której packsymbols filename.vsp**.  
  
## <a name="troubleshooting-symbol-problems"></a>Rozwiązywanie problemów z symboli  
 Jeśli nie ma żadnych symboli we własnym kodzie, dostępne są niektórych typowych rozwiązań:  
  
- Uruchom polecenia vsperfreport debugsympath w wierszu polecenia, aby wyświetlić pełną listę lokalizacji, gdzie składniki programu profilującego są ładowane informacji o symbolach i tego, czy pliki symboli, które są używane takie same jak pliki, które będzie używał Twój projekt.  
  
- Upewnij się, że uruchomiono polecenia vsperfreport z flagą packsymbols lub, w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zintegrowane środowisko projektowe, istnieje możliwość serializacja symbolu informacji wybrany w opcjach explorer ogólnej wydajności.  
  
- Jeśli zostały zebrane dane typu, należy dodać /SUMMARY:TYPE do wiersza polecenia vsperfreport.  
  
  Jeśli nie są widoczne symbole z Windows lub innych programów firmy Microsoft:  
  
- Upewnij się, że zostało ustawione ścieżkę pamięci podręcznej symboli Windows. Wykonaj jedną z następujących czynności, aby ustawić ścieżkę pamięci podręcznej symboli:  
  
  - Zestaw debuger -> symbole w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE do prawidłowej ścieżki.  
  
  - Dodaj opcję - symbolpath do wiersza polecenia VSPerfReport obejmujący symboli.  
  
- Jeśli nie widzisz żadnych symboli w [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], upewnij się, że serwer symboli poprawnie skonfigurowane dla serwera ASP.  
  
## <a name="repacking-symbols"></a>Przepakowaniu symboli  
 Jeśli chcesz ponownie spakować symboli do raportu, możesz to zrobić za pomocą narzędzia wiersza polecenia VsPerfReport. Użyj następujących wierszy polecenia:  
  
 VsPerfReport — clearpackedsymbols filename.vsp  
  
 VsPerfReport — packsymbols-summary: all filename.vsp  
  
## <a name="see-also"></a>Zobacz też  
 [Zapisywanie i eksportowanie wydajności danych dotyczących narzędzi](../profiling/saving-and-exporting-performance-tools-data.md)   
 [Instrukcje: Informacje o symbolach Windows odwołania](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)
