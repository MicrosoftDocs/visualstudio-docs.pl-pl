---
title: VSPerfMon | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPerfMon tool
- command line, tools
- command-line tools, VSPerfMon tool
- data [Visual Studio ALM], VSPerfMon tool
- performance data, VSPerfMon tool
- performance tools, VSPerfMon tool
- profilng tools,VSPerfCmd
ms.assetid: 37052afb-7a58-441f-bb17-f1587cc57068
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f43a01902801e6d3af9b6611ac2181acbcf398f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070490"
---
# <a name="vsperfmon"></a>VSPerfMon
Vsperfmon — narzędzie służy do zbierania danych dotyczących wydajności aplikacji; zwykle to narzędzie jest uruchamiane przez *VSPerfCmd.exe*. Vsperfmon — Wyświetla dodatkowe informacje na temat procesu dołączania lub odłączania, który nie jest dostępny za pomocą narzędzia VSPerfCmd. Aby wyświetlić te informacje, należy uruchomić VSPerfMon w osobnym oknie. Aby wywołać VSPerfMon, użyj następującej składni:  
  
```cmd  
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]  
```  
  
 W poniższej tabeli opisano opcje narzędzia VSPerfMon:  
  
|Opcje|Opis|  
|-------------|-----------------|  
|**U**|Dane wyjściowe przekierowanego konsoli są zapisywane jako Unicode.  Musi to być pierwszą określoną opcją.|  
|**Dane wyjściowe:** `<` *nazwy pliku* `>`|Przekierowuje dane wyjściowe do określonej nazwy pliku.|  
|**ŚLEDZENIA**|Uruchamia monitor wydajności dla instrumentowane profilowanie.|  
|**PRÓBKI**|Uruchamia monitor wydajności dla pobierania próbek profilowania.|  
|**POKRYCIE**|Uruchamia monitor wydajności na potrzeby zbierania pokrycie kodu.|  
|**WSPÓŁBIEŻNOŚĆ**|Uruchamia monitor wydajności na potrzeby profilowania rywalizacji zasobów.|  
|**Użytkownik:** `[` *domeny* `\]` *nazwy użytkownika*|Zezwala na dostęp klienta do monitora wydajności z określonego konta.|  
|**CROSSSESSION**|Włącza profilowanie między sesjami.|  
|**LICZNIK** `:cfg`|Gdy jest używana metoda profilowania Instrumentacji (ŚLEDŹ), określa on Licznik użycia Procesora, mają być zbierane w każdym punkcie instrumentacji. Może zbierać wiele dane liczników, przez określenie opcji obsługi wielu liczników.<br /><br /> Użyj następującej składni, aby określić licznika (*cfg*) danych:<br /><br /> **CounterName** [**, Załaduj ponownie**[,**FriendlyName**]]<br /><br /> -   **CounterName** to nazwa licznika zwróconemu przez polecenie/querycounters narzędzia VSPerfCmd.<br />-   **Załaduj ponownie** jest interwału próbkowania licznika zdarzeń. Nie używaj *Załaduj ponownie* przy użyciu metody instrumentacji.<br />— Jeśli zostanie określony, **FriendlyName** zastępuje **CounterName** w narzędziach profilowania raportu nazw kolumn.|  
|**WINCOUNTER** `:path`|Określa licznik wydajności Windows dołączany z danymi znacznika. `path` jest to ciąg licznika wydajności Windows w formacie ścieżki licznika PDH. Na przykład:<br /><br /> \Processor(0)\\czas procesora (%)<br /><br /> \System\Context przełączniki/s|  
|**AUTOMARK** `:n`|Określa przedział czasu (w milisekundach) między automatycznymi oznaczeniami w przypadku użycia /WINCOUNTER. Zaokrąglone do najbliższych 500 MS. wartość.<br /><br /> Użycie wartości 0, aby wyłączyć automatyczne znaczniki. (domyślny = 500 MS, jeśli nie określono tego parametru)|  
  
## <a name="see-also"></a>Zobacz także  
 [Narzędzie VSInstr](../profiling/vsinstr.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [Widoki raportu wydajności](../profiling/performance-report-views.md)