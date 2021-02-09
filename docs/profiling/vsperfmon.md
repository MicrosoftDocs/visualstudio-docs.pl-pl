---
title: VSPerfMon | Microsoft Docs
description: Dowiedz się, jak zbierać dane dotyczące wydajności aplikacji za pomocą narzędzia VSPerfMon. To narzędzie jest zazwyczaj uruchamiane przez VSPerfCmd.exe.
ms.date: 11/04/2016
ms.topic: reference
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
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 663bb5d1e126aa7ebc17f6720d81ac8eafd1e265
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911466"
---
# <a name="vsperfmon"></a>VSPerfMon
Za pomocą narzędzia VSPerfMon można zbierać dane dotyczące wydajności aplikacji. Zazwyczaj to narzędzie jest uruchamiane przez *VSPerfCmd.exe*. VSPerfMon wyświetla dodatkowe informacje na temat dołączania lub odłączania procesu, które nie są dostępne za pomocą narzędzia VSPerfCmd. Aby wyświetlić te informacje, uruchom VSPerfMon w osobnym oknie. Aby wywołać VSPerfMon, użyj następującej składni:

```cmd
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]
```

 W poniższej tabeli opisano opcje narzędzia VSPerfMon:

|Opcje|Opis|
|-------------|-----------------|
|**'T**|Przekierowane dane wyjściowe konsoli są zapisywane w formacie Unicode.  Ta wartość musi być pierwszą określoną opcją.|
|**Dane wyjściowe:** `<` *Nazwa pliku*`>`|Przekierowuje dane wyjściowe do określonej nazwy pliku.|
|**SZUKA**|Uruchamia Monitor wydajności dla profilowania Instrumentacji.|
|**SAMPLE**|Uruchamia Monitor wydajności dla profilowania próbkowania.|
|**POKRYCIA**|Uruchamia Monitor wydajności dla zbierania danych pokrycia kodu.|
|**WSPÓŁBIEŻNOŚCI**|Uruchamia Monitor wydajności dla profilowania rywalizacji o zasoby.|
|**Użytkownik:** `[` *domena* `\]` *Nazwa użytkownika*|Zezwala na dostęp klienta do monitora wydajności z określonego konta.|
|**CROSSSESSION**|Włącza profilowanie między sesjami.|
|**Licznik**`:cfg`|Gdy używana jest metoda profilowania Instrumentacji (TRACE), określa licznik procesora CPU do zebrania w każdym punkcie Instrumentacji. Można zbierać wiele danych liczników, określając wiele opcji licznika.<br /><br /> Aby określić dane licznika (*cfg*), użyj następującej składni:<br /><br /> **CounterName** [**, Załaduj ponownie**[,**FriendlyName**]]<br /><br /> -   **CounterName** jest nazwą licznika zwracanego przez polecenie VSPerfCmd/QueryCounters.<br />-   **Reload** jest interwałem próbkowania zdarzeń licznika. Nie należy używać *ponownego ładowania* z użyciem metody instrumentacji.<br />-W przypadku określenia parametru **FriendlyName** zastępuje **CounterName** w narzędzia profilowania nazwami kolumn raportu.|
|**WINCOUNTER**`:path`|Określa licznik wydajności systemu Windows do uwzględnienia z danymi znacznika. `path` to ciąg licznika wydajności systemu Windows w formacie ścieżki licznika PDH. Na przykład:<br /><br /> \Processor (0) \\ % czasu procesora<br /><br /> \System\Context/s|
|**Oznacz jako**`:n`|Określa przedział czasu (w milisekundach) między znacznikami automatycznymi przy użyciu używania/WINCOUNTER. ZAOKRĄGLA Zaokrąglone do najbliższej 500 ms.<br /><br /> Aby wyłączyć automatyczne znaczniki, należy użyć 0. (domyślnie = 500 MS, jeśli nie określono)|

## <a name="see-also"></a>Zobacz też
- [VSInstr](../profiling/vsinstr.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [VSPerfReport](../profiling/vsperfreport.md)
- [Widoki raportów wydajności](../profiling/performance-report-views.md)
