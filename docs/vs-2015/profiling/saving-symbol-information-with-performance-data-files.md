---
title: Zapisywanie informacji o symbolach przy użyciu plików danych o wydajności | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160295"
---
# <a name="saving-symbol-information-with-performance-data-files"></a>Zapisywanie informacji o symbolach w plikach danych dotyczących wydajności
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli używasz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE) do analizowania plików i planujesz przenieść plik VSP do innego komputera, musisz ustawić ustawienia projektu wydajności, aby zapisać lub *serializować* symbole w pliku raportu. Zwiększa to rozmiar pliku raportu. Serializacja symboli jest konieczna z dwóch powodów:  
  
- Aby osadzić symbole kodu w raporcie wydajności przed utratą zestawów docelowych z ich lokalizacji w magazynie tymczasowym.  
  
- Aby zachować symbole, dzięki czemu raport wydajności jest przenośny z PROFILOWANEGO komputera i wyświetla te same informacje, jeśli raport zostanie otwarty do analizy na innym komputerze, który może mieć różne symbole.  
  
  **Wymagania**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  Można serializować symbole z [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE lub z wiersza polecenia:  
  
- Aby serializować symbole w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE, wskaż **Narzędzia** na pasku menu, a następnie kliknij przycisk **Opcje**. W oknie **Opcje** wybierz pozycję **Narzędzia wydajności**, a następnie zaznacz pole wyboru **automatycznie serializować informacje o symbolach** .  
  
- PACKSYMBOLS jest równoważną opcją wiersza polecenia podczas zapisywania plików raportów. Aby serializować symbole, wpisz **VSPerfReport/Summary: ALL/PACKSYMBOLS filename. vsp**.  
  
## <a name="troubleshooting-symbol-problems"></a>Rozwiązywanie problemów z symbolami  
 Jeśli nie widzisz żadnych symboli w własnym kodzie, dostępne są niektóre popularne rozwiązania:  
  
- Uruchom VSPerfReport/debugsympath wyświetla w wierszu polecenia, aby wyświetlić pełną listę lokalizacji, w których składniki profilera ładują informacje o symbolach i czy pliki symboli, które są używane, są zgodne z plikami używanymi przez ten projekt.  
  
- Upewnij się, że uruchamiasz VSPerfReport z flagą/PACKSYMBOLS lub, w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE, że wybrano opcję Informacje o symbolach serializacji w ogólnych opcjach Eksploratora wydajności.  
  
- Jeśli zebrano dane typu, Dodaj/SUMMARY: TYPE do VSPerfReport wiersza polecenia.  
  
  Jeśli nie widzisz symboli z okna lub innych programów firmy Microsoft:  
  
- Upewnij się, że ustawiono ścieżkę pamięci podręcznej symboli systemu Windows. Wykonaj jedną z następujących czynności, aby ustawić ścieżkę pamięci podręcznej symboli:  
  
  - Ustaw opcję symboli >debugera w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE na poprawną ścieżkę.  
  
  - Dodaj opcję-SymbolPath — do wiersza polecenia VSPerfReport, aby uwzględnić symbole.  
  
- Jeśli nie widzisz żadnych symboli w programie, upewnij się, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] że serwer symboli jest prawidłowo skonfigurowany dla serwera ASP.  
  
## <a name="repacking-symbols"></a>Przepakowywanie symboli  
 Jeśli chcesz ponownie spakować symbole do raportu, możesz to zrobić za pomocą narzędzia wiersza polecenia VsPerfReport. Użyj następujących wierszy poleceń:  
  
 VsPerfReport-clearpackedsymbols filename. vsp  
  
 VsPerfReport-PACKSYMBOLS-Summary: ALL filename. vsp  
  
## <a name="see-also"></a>Zobacz też  
 [Zapisywanie i eksportowanie danych narzędzi wydajności](../profiling/saving-and-exporting-performance-tools-data.md)   
 [Instrukcje: odwołania do informacji o symbolach systemu Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [VSPerfReport](../profiling/vsperfreport.md)
