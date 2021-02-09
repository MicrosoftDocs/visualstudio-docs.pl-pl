---
title: VSInstr | Microsoft Docs
description: Dowiedz się, w jaki sposób narzędzie VSInstr służy do instrumentowania plików binarnych i innych różnych opcji narzędzi VSInstr.
ms.date: 11/04/2016
ms.topic: reference
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
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 476822abe665bee18d082b7187bfa657cc360d3e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99911650"
---
# <a name="vsinstr"></a>VSInstr
Narzędzie VSInstr służy do instrumentowania plików binarnych. Jest on wywoływany przy użyciu następującej składni:

```cmd
VSInstr [/U] filename [/options]
```

 W poniższej tabeli opisano opcje narzędzia VSInstr:

|Opcje|Opis|
|-------------|-----------------|
|**Pomoc** lub **?**|Wyświetla Pomoc.|
|**'T**|Zapisuje przekierowane dane wyjściowe konsoli w formacie Unicode. Należy określić pierwszą opcję.|
|`@filename`|Określa nazwę pliku odpowiedzi, który zawiera jedną opcję polecenia w każdym wierszu.  Nie należy używać znaków cudzysłowu.|
|**OutputPath**`:path`|Określa katalog docelowy dla obrazu z instrumentacją. Jeśli ścieżka wyjściowa nie zostanie określona, nazwa oryginalnego pliku binarnego jest zmieniana przez dołączenie "ORIG" do nazwy plików w tym samym katalogu, a kopia pliku binarnego jest Instrumentacją.|
|**Wyklucz:**`funcspec`|Określa specyfikację funkcji, która ma zostać wykluczona z Instrumentacji przez sondy. Jest to przydatne, gdy profilowanie wstawiania sondy w funkcji powoduje nieprzewidywalne lub niepożądane wyniki.<br /><br /> Nie należy używać opcji **exclude** i **include** odwołujących się do funkcji w tym samym pliku binarnym.<br /><br /> Można określić wiele specyfikacji funkcji z oddzielnymi opcjami **wykluczenia** .<br /><br /> `funcspec` jest zdefiniowany jako:<br /><br /> [przestrzeń nazw \<separator1> ] [Klasa \<separator2> ] funkcyjn<br /><br /> \<separator1> jest `::` przeznaczony dla kodu natywnego i `.` dla kodu zarządzanego.<br /><br /> Wartość \<separator2> to zawsze `::`<br /><br /> **Wykluczanie** jest obsługiwane z pokryciem kodu.<br /><br /> Symbol wieloznaczny \* jest obsługiwany. Na przykład, aby wykluczyć wszystkie funkcje w przestrzeni nazw, użyj:<br /><br /> Przestrzeń nazw::\*<br /><br /> Aby wyświetlić pełne nazwy funkcji w określonym pliku binarnym, można użyć **VSInstr/DumpFuncs** .|
|**Uwzględnij:**`funcspec`|Określa specyfikację funkcji w pliku binarnym do Instrumentacji z sondami. Wszystkie inne funkcje w danych binarnych nie są Instrumentacją.<br /><br /> Można określić wiele specyfikacji funkcji z oddzielnymi opcjami **include** .<br /><br /> Nie należy używać opcji **dołączania** i **wykluczania** odwołujących się do funkcji w tym samym pliku binarnym.<br /><br /> **Include** nie jest obsługiwane z pokryciem kodu.<br /><br /> `funcspec` jest zdefiniowany jako:<br /><br /> [przestrzeń nazw \<separator1> ] [Klasa \<separator2> ] funkcyjn<br /><br /> \<separator1> jest `::` przeznaczony dla kodu natywnego i `.` dla kodu zarządzanego.<br /><br /> Wartość \<separator2> to zawsze `::`<br /><br /> Symbol wieloznaczny \* jest obsługiwany. Na przykład, aby uwzględnić wszystkie funkcje w przestrzeni nazw, użyj:<br /><br /> Przestrzeń nazw::\*<br /><br /> Aby wyświetlić pełne nazwy funkcji w określonym pliku binarnym, można użyć **VSInstr/DumpFuncs** .|
|**DumpFuncs**|Wyświetla listę funkcji w określonym obrazie. Instrumentacja nie jest wykonywana.|
|**ExcludeSmallFuncs**|Wyklucza małe funkcje, które są krótkimi funkcjami, które nie wykonują żadnych wywołań funkcji z Instrumentacji. Opcja **ExcludeSmallFuncs** zapewnia mniejszą obciążenie oprzyrządowania, co zwiększa szybkość Instrumentacji.<br /><br /> Wyłączenie małych funkcji powoduje także zmniejszenie. rozmiar pliku *VSP* i czas wymagany do analizy.|
|**Oznacz:**{**przed** \|  \| **górnym** \| **dnem**}`,funcname,markid`|Wstawia znacznik profilu (identyfikator używany do ograniczania danych w raportach), którego można użyć do identyfikacji początku lub końca zakresu danych w pliku raportu. vsp.<br /><br /> **Przed** -bezpośrednio przed wpisem funkcji docelowej.<br /><br /> Natychmiast **po zakończeniu** funkcji docelowej.<br /><br /> Z **góry** bezpośrednio po wpisie funkcji docelowej.<br /><br /> **Dolne** — bezpośrednio przed każdym zwróceniem w funkcji docelowej.<br /><br /> `funcname` -Nazwa funkcji docelowej<br /><br /> `Markid` -Dodatnia liczba całkowita (Long) do użycia jako identyfikator znacznika profilu.|
|**Pokrycie**|Wykonuje instrumentację pokrycia. Może być używany tylko z następującymi opcjami: **verbose**, **OutputPath**, **exclude** i **LogFile**..|
|**Pełne**|Opcja **pełne** służy do wyświetlania szczegółowych informacji na temat procesu instrumentacji.|
|**Nowarn**`[:[Message Number[;Message Number]]]`|Pomijanie wszystkich lub określonych ostrzeżeń.<br /><br /> `Message Number` -Numer ostrzegawczy. `Message Number`W przypadku pominięcia wszystkie ostrzeżenia są pomijane.<br /><br /> Aby uzyskać więcej informacji, zobacz [VSInstr](../profiling/vsinstr-warnings.md)Warnings.|
|**Kontrolka:** `{` **Wątek** \| **Proces** \| **Globalne**`}`|Określa poziom profilowania następujących opcji kontrolki zbierania danych VSInstr:<br /><br /> **Początek**<br /><br /> **StartOnly**<br /><br /> **Wstrzymanie**<br /><br /> **StopOnly**<br /><br /> **SuspendOnly**<br /><br /> **ResumeOnly**<br /><br /> **Thread** -określa funkcje kontroli zbierania danych na poziomie wątku. Profilowanie jest uruchomione lub zatrzymane tylko dla bieżącego wątku. Nie dotyczy to stan profilowania innych wątków. Wartość domyślna to Thread.<br /><br /> **Proces** — określa funkcje kontroli zbierania danych na poziomie procesu. Profilowanie zostanie uruchomione lub zatrzymane dla wszystkich wątków w bieżącym procesie. Zmiana stanu profilowania innych procesów nie jest zależna.<br /><br /> **Global** -określa funkcje kontroli zbierania danych na poziomie globalnym (proces krzyżowy).<br /><br /> Jeśli nie określisz poziomu profilowania, wystąpi błąd.|
|**Rozpocznij:** `{` **Wewnątrz** \| **Poza**`},funcname`|Ogranicza zbieranie danych do funkcji docelowej i funkcji podrzędnych wywoływanych przez tę funkcję.<br /><br /> **Wewnątrz** — Wstawia funkcję StartProfile bezpośrednio po wpisie do funkcji docelowej. Wstawia funkcję StopProfile bezpośrednio przed każdym zwróceniem w funkcji docelowej.<br /><br /> **Zewnętrzny** — Wstawia funkcję StartProfile bezpośrednio przed każdym wywołaniem funkcji docelowej. Wstawia funkcję StopProfile natychmiast po każdym wywołaniu funkcji docelowej.<br /><br /> `funcname` -Nazwa funkcji docelowej.|
|**Wstrzymywanie:** `{` **Wewnątrz** \| **Poza**`},funcname`|Wyklucza zbieranie danych dla funkcji docelowej i funkcji podrzędnych wywoływanych przez funkcję.<br /><br /> **Wewnątrz** — Wstawia funkcję SuspendProfile bezpośrednio po wpisie do funkcji docelowej. Wstawia funkcję ResumeProfile bezpośrednio przed każdym zwróceniem w funkcji docelowej.<br /><br /> **Poza** — Wstawia funkcję SuspendProfile bezpośrednio przed wpisem do funkcji docelowej. Wstawia funkcję ResumeProfile natychmiast po zakończeniu od funkcji docelowej.<br /><br /> `funcname` -Nazwa funkcji docelowej.<br /><br /> Jeśli funkcja docelowa zawiera funkcję StartProfile, funkcja SuspendProfile zostanie wstawiona przed nią. Jeśli funkcja docelowa zawiera funkcję StopProfile, funkcja ResumeProfile zostanie wstawiona po niej.|
|**StartOnly:** `{` **Przed** \| **Po** \| **Góra** \| **U dołu**`},funcname`|Rozpoczyna zbieranie danych podczas przebiegu profilowania. Wstawia funkcję API StartProfile w określonej lokalizacji.<br /><br /> **Przed** -bezpośrednio przed wpisem funkcji docelowej.<br /><br /> Natychmiast **po zakończeniu** funkcji docelowej.<br /><br /> Z **góry** bezpośrednio po wpisie funkcji docelowej.<br /><br /> **Dolne** — bezpośrednio przed każdym zwróceniem w funkcji docelowej.<br /><br /> `funcname` -Nazwa funkcji docelowej.|
|**StopOnly:**{**przed** \|  \| **górnym** \| **dnem**}`,funcname`|Zatrzymuje zbieranie danych podczas przebiegu profilowania. Wstawia funkcję StopProfile w określonej lokalizacji.<br /><br /> **Przed** -bezpośrednio przed wpisem funkcji docelowej.<br /><br /> Natychmiast **po zakończeniu** funkcji docelowej.<br /><br /> Z **góry** bezpośrednio po wpisie funkcji docelowej.<br /><br /> **Dolne** — bezpośrednio przed każdym zwróceniem w funkcji docelowej.<br /><br /> `funcname` -Nazwa funkcji docelowej.|
|**SuspendOnly:**{**przed** \|  \| **górnym** \| **dnem**}`,funcname`|Zatrzymuje zbieranie danych podczas przebiegu profilowania. Wstawia interfejs API SuspendProfile w określonej lokalizacji.<br /><br /> **Przed** -bezpośrednio przed wpisem funkcji docelowej.<br /><br /> Natychmiast **po zakończeniu** funkcji docelowej.<br /><br /> Z **góry** bezpośrednio po wpisie funkcji docelowej.<br /><br /> **Dolne** — bezpośrednio przed każdym zwróceniem w funkcji docelowej.<br /><br /> `funcname` -Nazwa funkcji docelowej.<br /><br /> Jeśli funkcja docelowa zawiera funkcję StartProfile, funkcja SuspendProfile zostanie wstawiona przed nią.|
|**ResumeOnly:**{**przed** \|  \| **górnym** \| **dnem**}`,funcname`|Rozpoczyna lub wznawia zbieranie danych podczas przebiegu profilowania.<br /><br /> Jest on zwykle używany do uruchamiania profilowania po zatrzymaniu profilowania opcji **SuspendOnly** . Wstawia interfejs API ResumeProfile w określonej lokalizacji.<br /><br /> **Przed** -bezpośrednio przed wpisem funkcji docelowej.<br /><br /> Natychmiast **po zakończeniu** funkcji docelowej.<br /><br /> Z **góry** bezpośrednio po wpisie funkcji docelowej.<br /><br /> **Dolne** — bezpośrednio przed każdym zwróceniem w funkcji docelowej.<br /><br /> `funcname` -Nazwa funkcji docelowej.<br /><br /> Jeśli funkcja docelowa zawiera funkcję StopProfile, funkcja ResumeProfile zostanie wstawiona po niej.|

## <a name="see-also"></a>Zobacz też
- [VSPerfMon](../profiling/vsperfmon.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [VSPerfReport](../profiling/vsperfreport.md)
- [Ostrzeżenia VSInstr](../profiling/vsinstr-warnings.md)
- [Widoki raportów wydajności](../profiling/performance-report-views.md)
