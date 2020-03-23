---
title: VSPerfMon | Dokumenty firmy Microsoft
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
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 50519554f7ec71e277dc776b05bc2967c1071f52
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779899"
---
# <a name="vsperfmon"></a>VSPerfMon
Za pomocą narzędzia VSPerfMon można zbierać dane dotyczące wydajności aplikacji; zazwyczaj to narzędzie jest uruchamiane przez *vsPerfCmd.exe*. VSPerfMon wyświetla dodatkowe informacje o procesie dołączyć lub odłączyć, który nie jest dostępny za pomocą narzędzia VSPerfCmd. Aby wyświetlić te informacje, uruchom vsPerfMon w osobnym oknie. Aby wywołać vsperfmon należy użyć następującej składni:

```cmd
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]
```

 W poniższej tabeli opisano opcje narzędzia VSPerfMon:

|Opcje|Opis|
|-------------|-----------------|
|**U**|Przekierowane wyjście konsoli jest zapisywane jako Unicode.  Musi to być pierwsza określona opcja.|
|**WYJŚCIE:** `<` *nazwa pliku*`>`|Przekierowuje dane wyjściowe do określonej nazwy pliku.|
|**Śledzenia**|Uruchamia monitor wydajności do profilowania instrumentowanego.|
|**Przykładowe**|Uruchamia monitor wydajności do profilowania próbkowania.|
|**Pokrycia**|Uruchamia monitor wydajności dla kolekcji pokrycia kodu.|
|**Współbieżności**|Uruchamia monitor wydajności do profilowania rywalizacji o zasoby.|
|**UŻYTKOWNIK:** `[` *nazwa użytkownika* *domeny* `\]`|Umożliwia klientowi dostęp do monitora wydajności z określonego konta.|
|**CROSSSESSION (KRZYŻYK)**|Umożliwia profilowanie między sesyjne.|
|**LICZNIK**`:cfg`|Gdy używana jest metoda profilowania instrumentacji (TRACE), określa licznik procesora CPU, który ma być zbierany w każdym punkcie instrumentacji. Można zebrać wiele danych licznika, określając wiele opcji licznika.<br /><br /> Aby określić dane licznika *(cfg),* należy użyć następującej składni:<br /><br /> **Nazwa przeciwmractwo** [**,Reload**[,**FriendlyName**]]<br /><br /> -   **Nazwa licznika** to nazwa licznika zwrócona przez polecenie VSPerfCmd /QueryCounters.<br />-   **Ponowne ładowanie** jest interwałem próbkowania zdarzenia licznika. Nie należy używać *funkcji Reload* z metodą oprzyrządowania.<br />- Po określeniu **FriendlyName** zastępuje **CounterName** w narzędzia profilowania nazwy kolumn raportu.|
|**OKRĘG WYBORCZY WINCOUNTER**`:path`|Określa licznik wydajności systemu Windows do uwzględnienia z danymi znaczników. `path`jest ciągiem licznika wydajności systemu Windows w formacie ścieżki licznika PDH. Przykład:<br /><br /> \Procesor(0)\\% czasu procesora<br /><br /> \Przełączniki systemowe\kontekstowe/s|
|**AUTOMARK**`:n`|Określa przedział czasu (w milisekundach) między znakami automatycznymi podczas używania /WINCOUNTER. Zaokrąglone do najbliższego 500ms.<br /><br /> Użyj 0, aby wyłączyć znaczniki automatyczne. (default=500ms jeśli nieokreślone)|

## <a name="see-also"></a>Zobacz też
- [VSInstr](../profiling/vsinstr.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [VSPerfReport](../profiling/vsperfreport.md)
- [Widoki raportu o skuteczności](../profiling/performance-report-views.md)
