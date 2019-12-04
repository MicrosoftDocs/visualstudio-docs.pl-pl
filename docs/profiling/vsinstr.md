---
title: VSInstr | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, instrumentation
- instrumentation, VSInstr tool
- profiling tools,VSInstr
- command-line tools, instrumentation
- command line, tools
- VSInstr
- VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 7b1334f7-f9b0-4a82-a145-d0607bfa8467
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 386d81d14996547670944ce1b4911233eb9c8955
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74779925"
---
# <a name="vsinstr"></a>VSInstr
Narzędzie VSInstr służy do instrumentowania plików binarnych. Jest on wywoływany przy użyciu następującej składni:

```cmd
VSInstr [/U] filename [/options]
```

 W poniższej tabeli opisano opcje narzędzia VSInstr:

|Opcje|Opis|
|-------------|-----------------|
|**Pomoc** lub **?**|Wyświetla pomoc.|
|**'T**|Zapisuje przekierowane dane wyjściowe konsoli w formacie Unicode. Należy określić pierwszą opcję.|
|`@filename`|Określa nazwę pliku odpowiedzi, który zawiera jedną opcję polecenia w każdym wierszu.  Nie należy używać znaków cudzysłowu.|
|**OutputPath** `:path`|Określa katalog docelowy dla obrazu z instrumentacją. Jeśli ścieżka wyjściowa nie zostanie określona, nazwa oryginalnego pliku binarnego jest zmieniana przez dołączenie "ORIG" do nazwy plików w tym samym katalogu, a kopia pliku binarnego jest Instrumentacją.|
|**Wyklucz** `:funcspec`|Określa specyfikację funkcji, która ma zostać wykluczona z Instrumentacji przez sondy. Jest to przydatne, gdy profilowanie wstawiania sondy w funkcji powoduje nieprzewidywalne lub niepożądane wyniki.<br /><br /> Nie należy używać opcji **exclude** i **include** odwołujących się do funkcji w tym samym pliku binarnym.<br /><br /> Można określić wiele specyfikacji funkcji z oddzielnymi opcjami **wykluczenia** .<br /><br /> `funcspec` jest zdefiniowany jako:<br /><br /> [przestrzeń nazw\<separator1 >] [Klasa\<separator2 >] — funkcja<br /><br /> \<separator1 > jest `::` dla kodu natywnego i `.` dla kodu zarządzanego.<br /><br /> \<separator2 > jest zawsze `::`<br /><br /> **Wykluczanie** jest obsługiwane z pokryciem kodu.<br /><br /> Symbol wieloznaczny \* jest obsługiwany. Na przykład, aby wykluczyć wszystkie funkcje w przestrzeni nazw, użyj:<br /><br /> Przestrzeń nazw::\*<br /><br /> Aby wyświetlić pełne nazwy funkcji w określonym pliku binarnym, można użyć **VSInstr/DumpFuncs** .|
|**Uwzględnij** `:funcspec`|Określa specyfikację funkcji w pliku binarnym do Instrumentacji z sondami. Wszystkie inne funkcje w danych binarnych nie są Instrumentacją.<br /><br /> Można określić wiele specyfikacji funkcji z oddzielnymi opcjami **include** .<br /><br /> Nie należy używać opcji **dołączania** i **wykluczania** odwołujących się do funkcji w tym samym pliku binarnym.<br /><br /> **Include** nie jest obsługiwane z pokryciem kodu.<br /><br /> `funcspec` jest zdefiniowany jako:<br /><br /> [przestrzeń nazw\<separator1 >] [Klasa\<separator2 >] — funkcja<br /><br /> \<separator1 > jest `::` dla kodu natywnego i `.` dla kodu zarządzanego.<br /><br /> \<separator2 > jest zawsze `::`<br /><br /> Symbol wieloznaczny \* jest obsługiwany. Na przykład, aby uwzględnić wszystkie funkcje w przestrzeni nazw, użyj:<br /><br /> Przestrzeń nazw::\*<br /><br /> Aby wyświetlić pełne nazwy funkcji w określonym pliku binarnym, można użyć **VSInstr/DumpFuncs** .|
|**DumpFuncs**|Wyświetla listę funkcji w określonym obrazie. Instrumentacja nie jest wykonywana.|
|**ExcludeSmallFuncs**|Wyklucza małe funkcje, które są krótkimi funkcjami, które nie wykonują żadnych wywołań funkcji z Instrumentacji. Opcja **ExcludeSmallFuncs** zapewnia mniejszą obciążenie oprzyrządowania, co zwiększa szybkość Instrumentacji.<br /><br /> Wyłączenie małych funkcji powoduje także zmniejszenie. rozmiar pliku *VSP* i czas wymagany do analizy.|
|**Oznacz:** {**przed**`&#124;`**po**`&#124;`**górnym**`&#124;`**dolnym**}`,funcname,markid`|Wstawia znacznik profilu (identyfikator używany do ograniczania danych w raportach), którego można użyć do identyfikacji początku lub końca zakresu danych w pliku raportu. vsp.<br /><br /> **Przed** -bezpośrednio przed wpisem funkcji docelowej.<br /><br /> Natychmiast **po zakończeniu** funkcji docelowej.<br /><br /> Z **góry** bezpośrednio po wpisie funkcji docelowej.<br /><br /> **Dolne** — bezpośrednio przed każdym zwróceniem w funkcji docelowej.<br /><br /> `funcname` — nazwa funkcji docelowej<br /><br /> `Markid` — dodatnia liczba całkowita (Long) do użycia jako identyfikator znacznika profilu.|
|**Pokrycia**|Wykonuje instrumentację pokrycia. Może być używany tylko z następującymi opcjami: **verbose**, **OutputPath**, **exclude**i **LogFile**..|
|**Pełne**|Opcja **pełne** służy do wyświetlania szczegółowych informacji na temat procesu instrumentacji.|
|**Nowarn** `[:[Message Number[;Message Number]]]`|Pomijanie wszystkich lub określonych ostrzeżeń.<br /><br /> `Message Number` — numer ostrzegawczy. W przypadku pominięcia `Message Number` wszystkie ostrzeżenia są pomijane.<br /><br /> Aby uzyskać więcej informacji, zobacz [VSInstr](../profiling/vsinstr-warnings.md)Warnings.|
|**Sterowanie** **procesem** `:{` **wątku** `&#124;` `&#124;` **globalne** `}`|Określa poziom profilowania następujących opcji kontrolki zbierania danych VSInstr:<br /><br /> **Start**<br /><br /> **StartOnly**<br /><br /> **Suspend**<br /><br /> **StopOnly**<br /><br /> **SuspendOnly**<br /><br /> **ResumeOnly**<br /><br /> **Thread** -określa funkcje kontroli zbierania danych na poziomie wątku. Profilowanie jest uruchomione lub zatrzymane tylko dla bieżącego wątku. Nie dotyczy to stan profilowania innych wątków. Wartość domyślna to Thread.<br /><br /> **Proces** — określa funkcje kontroli zbierania danych na poziomie procesu. Profilowanie zostanie uruchomione lub zatrzymane dla wszystkich wątków w bieżącym procesie. Zmiana stanu profilowania innych procesów nie jest zależna.<br /><br /> **Global** -określa funkcje kontroli zbierania danych na poziomie globalnym (proces krzyżowy).<br /><br /> Jeśli nie określisz poziomu profilowania, wystąpi błąd.|
|**Rozpocznij** `:{` **wewnątrz** `&#124;` **poza** `},funcname`|Ogranicza zbieranie danych do funkcji docelowej i funkcji podrzędnych wywoływanych przez tę funkcję.<br /><br /> **Wewnątrz** — Wstawia funkcję StartProfile bezpośrednio po wpisie do funkcji docelowej. Wstawia funkcję StopProfile bezpośrednio przed każdym zwróceniem w funkcji docelowej.<br /><br /> **Zewnętrzny** — Wstawia funkcję StartProfile bezpośrednio przed każdym wywołaniem funkcji docelowej. Wstawia funkcję StopProfile natychmiast po każdym wywołaniu funkcji docelowej.<br /><br /> `funcname` — nazwa funkcji docelowej.|
|**Wstrzymywanie** `:{` **wewnątrz** `&#124;` **poza** `},funcname`|Wyklucza zbieranie danych dla funkcji docelowej i funkcji podrzędnych wywoływanych przez funkcję.<br /><br /> **Wewnątrz** — Wstawia funkcję SuspendProfile bezpośrednio po wpisie do funkcji docelowej. Wstawia funkcję ResumeProfile bezpośrednio przed każdym zwróceniem w funkcji docelowej.<br /><br /> **Poza** — Wstawia funkcję SuspendProfile bezpośrednio przed wpisem do funkcji docelowej. Wstawia funkcję ResumeProfile natychmiast po zakończeniu od funkcji docelowej.<br /><br /> `funcname` — nazwa funkcji docelowej.<br /><br /> Jeśli funkcja docelowa zawiera funkcję StartProfile, funkcja SuspendProfile zostanie wstawiona przed nią. Jeśli funkcja docelowa zawiera funkcję StopProfile, funkcja ResumeProfile zostanie wstawiona po niej.|
|**StartOnly:** `{` **przed** `&#124;` **po** `&#124;` **górnym** `&#124;` **dolnym** `},funcname`|Rozpoczyna zbieranie danych podczas przebiegu profilowania. Wstawia funkcję API StartProfile w określonej lokalizacji.<br /><br /> **Przed** -bezpośrednio przed wpisem funkcji docelowej.<br /><br /> Natychmiast **po zakończeniu** funkcji docelowej.<br /><br /> Z **góry** bezpośrednio po wpisie funkcji docelowej.<br /><br /> **Dolne** — bezpośrednio przed każdym zwróceniem w funkcji docelowej.<br /><br /> `funcname` — nazwa funkcji docelowej.|
|**StopOnly:** {**przed**`&#124;`**po**`&#124;`**górnym**`&#124;`**dolnym**}`,funcname`|Zatrzymuje zbieranie danych podczas przebiegu profilowania. Wstawia funkcję StopProfile w określonej lokalizacji.<br /><br /> **Przed** -bezpośrednio przed wpisem funkcji docelowej.<br /><br /> Natychmiast **po zakończeniu** funkcji docelowej.<br /><br /> Z **góry** bezpośrednio po wpisie funkcji docelowej.<br /><br /> **Dolne** — bezpośrednio przed każdym zwróceniem w funkcji docelowej.<br /><br /> `funcname` — nazwa funkcji docelowej.|
|**SuspendOnly:** {**przed**`&#124;`**po**`&#124;`**górnym**`&#124;`**dolnym**}`,funcname`|Zatrzymuje zbieranie danych podczas przebiegu profilowania. Wstawia interfejs API SuspendProfile w określonej lokalizacji.<br /><br /> **Przed** -bezpośrednio przed wpisem funkcji docelowej.<br /><br /> Natychmiast **po zakończeniu** funkcji docelowej.<br /><br /> Z **góry** bezpośrednio po wpisie funkcji docelowej.<br /><br /> **Dolne** — bezpośrednio przed każdym zwróceniem w funkcji docelowej.<br /><br /> `funcname` — nazwa funkcji docelowej.<br /><br /> Jeśli funkcja docelowa zawiera funkcję StartProfile, funkcja SuspendProfile zostanie wstawiona przed nią.|
|**ResumeOnly:** {**przed**`&#124;`**po**`&#124;`**górnym**`&#124;`**dolnym**}`,funcname`|Rozpoczyna lub wznawia zbieranie danych podczas przebiegu profilowania.<br /><br /> Jest on zwykle używany do uruchamiania profilowania po zatrzymaniu profilowania opcji **SuspendOnly** . Wstawia interfejs API ResumeProfile w określonej lokalizacji.<br /><br /> **Przed** -bezpośrednio przed wpisem funkcji docelowej.<br /><br /> Natychmiast **po zakończeniu** funkcji docelowej.<br /><br /> Z **góry** bezpośrednio po wpisie funkcji docelowej.<br /><br /> **Dolne** — bezpośrednio przed każdym zwróceniem w funkcji docelowej.<br /><br /> `funcname` — nazwa funkcji docelowej.<br /><br /> Jeśli funkcja docelowa zawiera funkcję StopProfile, funkcja ResumeProfile zostanie wstawiona po niej.|

## <a name="see-also"></a>Zobacz także
- [VSPerfMon](../profiling/vsperfmon.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [VSPerfReport](../profiling/vsperfreport.md)
- [Ostrzeżenia VSInstr](../profiling/vsinstr-warnings.md)
- [Widoki raportów wydajności](../profiling/performance-report-views.md)
