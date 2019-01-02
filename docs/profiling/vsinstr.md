---
title: Narzędzie VSInstr | Dokumentacja firmy Microsoft
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1e1c5d548ae8e197523fb92ed130ebeebb04af3f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53945772"
---
# <a name="vsinstr"></a>VSInstr
Narzędzie VSInstr służy do Instrumentacji danych binarnych. Jest wywoływany przy użyciu następującej składni:  
  
```cmd  
VSInstr [/U] filename [/options]  
```  
  
 W poniższej tabeli opisano opcje narzędzia VSInstr:  
  
|Opcje|Opis|  
|-------------|-----------------|  
|**Pomoc** lub **?**|Wyświetla Pomoc.|  
|**U**|Zapisuje dane wyjściowe konsoli przekierowanego jako Unicode. Musi ona być pierwszą określoną opcją.|  
|`@filename`|Określa nazwę pliku odpowiedzi, który zawiera jedną z opcji w wierszu polecenia.  Nie należy używać znaków cudzysłowu.|  
|**OutputPath** `:path`|Określa katalog docelowy dla obrazu z Instrumentacją. Jeśli nie określono ścieżki wyjściowej, oryginalny plik binarny jest nazywane przez dołączenie "Orig" do nazwy pliku, w tym samym katalogu, a został zinstrumentowany na kopię pliku binarnego.|  
|**Wyklucz** `:funcspec`|Określa Specyfikacja funkcji, które mają zostać wykluczone z Instrumentacji przez sondy. Jest to przydatne, gdy profilowanie wstawieniem sondy w funkcji powoduje, że nieprzewidywalne lub niepożądane wyniki.<br /><br /> Nie używaj **wykluczyć** i **Include** opcje, które odwołują się do funkcji w ten sam plik binarny.<br /><br /> Można określić wiele Specyfikacja funkcji z oddzielnym **wykluczyć** opcje.<br /><br /> `funcspec` jest zdefiniowany jako:<br /><br /> [przestrzeń nazw\<separator1 >] [klasy\<separator2 >] — funkcja<br /><br /> \<separator1 > jest `::` dla kodu natywnego i `.` dla kodu zarządzanego.<br /><br /> \<separator2 > jest zawsze `::`<br /><br /> **Wyklucz** jest obsługiwany z pokryciem kodu.<br /><br /> Symbol wieloznaczny \* jest obsługiwana. Na przykład, aby wykluczyć wszystkie funkcje w użyciu przestrzeni nazw:<br /><br /> MyNamespace::\*<br /><br /> Możesz użyć **VSInstr /DumpFuncs** Aby wyświetlić listę pełne nazwy funkcji w określonym pliku binarnego.|  
|**Obejmują** `:funcspec`|Określa Specyfikacja funkcji w pliku binarnym do Instrumentacji za pomocą sondy. Wszystkie funkcje w plikach binarnych nie są instrumentowane.<br /><br /> Istnieje możliwość określenia wielu specyfikacji funkcji z oddzielnych **Include** opcje.<br /><br /> Nie używaj **Include** i **wykluczyć** opcje, które odwołują się do funkcji w ten sam plik binarny.<br /><br /> **Obejmują** nie jest obsługiwany z pokryciem kodu.<br /><br /> `funcspec` jest zdefiniowany jako:<br /><br /> [przestrzeń nazw\<separator1 >] [klasy\<separator2 >] — funkcja<br /><br /> \<separator1 > jest `::` dla kodu natywnego i `.` dla kodu zarządzanego.<br /><br /> \<separator2 > jest zawsze `::`<br /><br /> Symbol wieloznaczny \* jest obsługiwana. Na przykład, aby uwzględnić wszystkie funkcje w użyciu przestrzeni nazw:<br /><br /> MyNamespace::\*<br /><br /> Możesz użyć **VSInstr /DumpFuncs** Aby wyświetlić listę pełne nazwy funkcji w określonym pliku binarnego.|  
|**DumpFuncs**|Wyświetla listę funkcji, w określonym obrazie. Jest wykonywana żadna Instrumentacja.|  
|**ExcludeSmallFuncs**|Wyklucza małych funkcji, które są krótkich funkcji, które nie należy wprowadzać wszelkie wywołania funkcji z Instrumentacji. **ExcludeSmallFuncs** opcji zapewnia mniejsze koszty Instrumentacji szybkość Instrumentacji w związku z tym ulepszone.<br /><br /> Zmniejsza to wyłączenie małych funkcji. *vsp* pliku, rozmiar i czas wymagany do analizy.|  
|**Znacznik:**{**przed**`&#124;`**po**`&#124;`**górnej**`&#124;`**dolnej**}`,funcname,markid`|Wstawia znak profilu (identyfikator używany do ograniczania danych w raportach) służące do identyfikowania początkowy lub końcowy zakresu danych w pliku Vsp raportu.<br /><br /> **Przed** — natychmiast przed wprowadzeniem funkcji docelowej.<br /><br /> **Po** — natychmiast po wyjście funkcji docelowej.<br /><br /> **TOP** — natychmiast po wejściu do funkcji docelowej.<br /><br /> **Dolny** — bezpośrednio przed każdego zwrotu w funkcji docelowej.<br /><br /> `funcname` — Nazwa docelowej funkcji<br /><br /> `Markid` -Dodatnią liczbą całkowitą (long) do wykorzystania jako identyfikator znacznika profilu.|  
|**Pokrycie**|Wykonuje Instrumentację pokrycia. Może służyć tylko z następujących opcji: **Pełne**, **OutputPath**, **wykluczyć**, i **Logfile**...|  
|**pełne**|**Pełne** opcja jest używana, aby wyświetlić szczegółowe informacje na temat procesu instrumentacji.|  
|**NoWarn** `[:[Message Number[;Message Number]]]`|Ukrywa wszystkie lub określone ostrzeżenia.<br /><br /> `Message Number` -numer ostrzeżenia. Jeśli `Message Number` jest pominięty, wszystkie ostrzeżenia są pomijane.<br /><br /> Aby uzyskać więcej informacji, zobacz [ostrzeżenia VSInstr](../profiling/vsinstr-warnings.md).|  
|**Kontrolka** `:{` **wątku** `&#124;` **procesu** `&#124;` **globalne** `}`|Określa poziom profilowania z następującą kolekcją danych VSInstr opcje sterowania:<br /><br /> **Start**<br /><br /> **StartOnly**<br /><br /> **Suspend**<br /><br /> **StopOnly**<br /><br /> **SuspendOnly**<br /><br /> **ResumeOnly**<br /><br /> **Wątek** -Określa funkcje kontroli zbierania danych na poziomie wątku. Profilowanie jest uruchomiona lub zatrzymana tylko dla bieżącego wątku. Nie dotyczy profilowania stan innych wątków. Wartość domyślna to wątku.<br /><br /> **Proces** -Określa funkcje kontroli zbierania danych poziom procesu profilowania. Profilowanie, uruchamia lub zatrzymuje działanie dla wszystkich wątków w bieżącym procesie. Nie wpływa na stan profilowania innych procesów.<br /><br /> **Globalne** -Określa funkcje kontroli danych (między procesami) poziomie globalnym w kolekcji.<br /><br /> Błąd występuje, jeśli nie określisz poziomu profilowania.|  
|**Rozpocznij** `:{` **wewnątrz** `&#124;` **poza metodą** `},funcname`|Ogranicza zbieranie danych do docelowej funkcji i funkcjach podrzędnych wywoływanych przez tę funkcję.<br /><br /> **Wewnątrz** -Wstawia funkcję StartProfile natychmiast po wejściu do funkcji docelowej. Wstawia funkcja StopProfile bezpośrednio przed każdy zwracany w docelowej funkcji.<br /><br /> **Poza metodą** -Wstawia funkcję StartProfile bezpośrednio przed każde wywołanie funkcji docelowej. Wstawia funkcję StopProfile bezpośrednio za każde wywołanie funkcji docelowej.<br /><br /> `funcname` — Nazwa docelowej funkcji.|  
|**Wstrzymywanie** `:{` **wewnątrz** `&#124;` **poza metodą** `},funcname`|Nie obejmuje zbieranie danych dla docelowej funkcji i funkcji podrzędnych wywołanych przez funkcję.<br /><br /> **Wewnątrz** -Wstawia funkcję SuspendProfile natychmiast po wejściu do funkcji docelowej. Wstawia funkcja ResumeProfile bezpośrednio przed każdy zwracany w docelowej funkcji.<br /><br /> **Poza metodą** -Wstawia funkcję SuspendProfile bezpośrednio przed wejściem do funkcji docelowej. Wstawia funkcję ResumeProfile zaraz po wyjścia z funkcji docelowej.<br /><br /> `funcname` — Nazwa docelowej funkcji.<br /><br /> Jeśli funkcja docelowa zawiera funkcję StartProfile, funkcja SuspendProfile jest wstawiany przed nią. Jeśli funkcja docelowa zawiera funkcję StopProfile, funkcja ResumeProfile jest wstawiany po nim.|  
|**StartOnly:** `{` **Przed** `&#124;` **po** `&#124;` **górnej** `&#124;` **dołu** `},funcname`|Rozpoczyna się zbieranie danych podczas uruchomienia profilowania. Funkcja StartProfile API do wstawienia w określonej lokalizacji.<br /><br /> **Przed** — natychmiast przed wprowadzeniem funkcji docelowej.<br /><br /> **Po** — natychmiast po wyjście funkcji docelowej.<br /><br /> **TOP** — natychmiast po wejściu do funkcji docelowej.<br /><br /> **Dolny** — bezpośrednio przed każdego zwrotu w funkcji docelowej.<br /><br /> `funcname` — Nazwa docelowej funkcji.|  
|**StopOnly:**{**przed**`&#124;`**po**`&#124;`**górnej**`&#124;`**dolnej**}`,funcname`|Zatrzymuje zbieranie danych podczas uruchomienia profilowania. Funkcja StopProfile do wstawienia w określonej lokalizacji.<br /><br /> **Przed** — natychmiast przed wprowadzeniem funkcji docelowej.<br /><br /> **Po** — natychmiast po wyjście funkcji docelowej.<br /><br /> **TOP** — natychmiast po wejściu do funkcji docelowej.<br /><br /> **Dolny** — bezpośrednio przed każdego zwrotu w funkcji docelowej.<br /><br /> `funcname` — Nazwa docelowej funkcji.|  
|**SuspendOnly:**{**przed**`&#124;`**po**`&#124;`**górnej**`&#124;`**dolnej**}`,funcname`|Zatrzymuje zbieranie danych podczas uruchomienia profilowania. Interfejs API SuspendProfile do wstawienia w określonej lokalizacji.<br /><br /> **Przed** — natychmiast przed wprowadzeniem funkcji docelowej.<br /><br /> **Po** — natychmiast po wyjście funkcji docelowej.<br /><br /> **TOP** — natychmiast po wejściu do funkcji docelowej.<br /><br /> **Dolny** — bezpośrednio przed każdego zwrotu w funkcji docelowej.<br /><br /> `funcname` — Nazwa docelowej funkcji.<br /><br /> Jeśli funkcja docelowa zawiera funkcję StartProfile, funkcja SuspendProfile jest wstawiany przed nią.|  
|**ResumeOnly:**{**przed**`&#124;`**po**`&#124;`**górnej**`&#124;`**dolnej**}`,funcname`|Rozpoczyna się lub wznawiania pracy zbierania danych w trakcie sesji profilowania.<br /><br /> Zwykle jest używana do uruchomienia profilowania po **SuspendOnly** opcja została zatrzymana, profilowania. Interfejs API ResumeProfile do wstawienia w określonej lokalizacji.<br /><br /> **Przed** — natychmiast przed wprowadzeniem funkcji docelowej.<br /><br /> **Po** — natychmiast po wyjście funkcji docelowej.<br /><br /> **TOP** — natychmiast po wejściu do funkcji docelowej.<br /><br /> **Dolny** — bezpośrednio przed każdego zwrotu w funkcji docelowej.<br /><br /> `funcname` — Nazwa docelowej funkcji.<br /><br /> Jeśli funkcja docelowa zawiera funkcję StopProfile, funkcja ResumeProfile jest wstawiany po nim.|  
  
## <a name="see-also"></a>Zobacz także  
 [VSPerfMon](../profiling/vsperfmon.md)   
 [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [Ostrzeżenia VSInstr](../profiling/vsinstr-warnings.md)   
 [Widoki raportu wydajności](../profiling/performance-report-views.md)