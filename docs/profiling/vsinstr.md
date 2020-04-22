---
title: VsInstr | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 87e51a8bd82a4bd79309dfe2a055c44d986e94c4
ms.sourcegitcommit: a7f781d5a089e6aab6b073a07f3d4d2967af8aa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81760146"
---
# <a name="vsinstr"></a>VSInstr
Narzędzie VSInstr służy do instrumencie plików binarnych. Jest wywoływana przy użyciu następującej składni:

```cmd
VSInstr [/U] filename [/options]
```

 W poniższej tabeli opisano opcje narzędzia VSInstr:

|Opcje|Opis|
|-------------|-----------------|
|**Pomoc** lub **?**|Wyświetla Pomoc.|
|**U**|Zapisuje przekierowane dane wyjściowe konsoli jako Unicode. Musi być najpierw określona opcja.|
|`@filename`|Określa nazwę pliku odpowiedzi zawierającego jedną opcję polecenia w wierszu.  Nie należy używać cudzysłowów.|
|**Ścieżka wyjściowa**`:path`|Określa katalog docelowy dla obrazu instrumentowanego. Jeśli ścieżka wyjściowa nie jest określona, oryginalny plik binarny zostanie zmieniony przez dołączenie "Orig" do nazwy pliku w tym samym katalogu, a kopia pliku binarnego jest instrumentowana.|
|**Wyklucz:**`funcspec`|Określa specyfikację funkcji, która ma być wyłączona z oprzyrządowania przez sondy. Jest to przydatne, gdy profilowanie sondy wstawiania w funkcji powoduje nieprzewidywalne lub niepożądane wyniki.<br /><br /> Nie należy używać opcji **Wyklucz** i **Uwzględnij,** które odwołują się do funkcji w tym samym pliku binarnym.<br /><br /> Można określić specyfikację wielu funkcji z oddzielnymi opcjami **wykluczeń.**<br /><br /> `funcspec`jest zdefiniowany jako:<br /><br /> [separator\<przestrzeni nazw1>] [separator klasy2\<>]funkcja<br /><br /> \<separator1> jest `::` dla kodu macierzystego i `.` kodu zarządzanego.<br /><br /> \<separator2> jest zawsze`::`<br /><br /> **Wyklucz** jest obsługiwany z pokryciem kodu.<br /><br /> Obsługiwany jest \* symbol wieloznaczny. Na przykład, aby wykluczyć wszystkie funkcje w obszarze nazw, użyj:<br /><br /> Mynamespace::\*<br /><br /> Za pomocą **programu VSInstr /DumpFuncs** można wyświetlić pełną liczbę nazw funkcji w określonym pliku binarnym.|
|**Obejmują:**`funcspec`|Określa specyfikację funkcji w pliku binarnym do przyrządu z sondami. Wszystkie inne funkcje w plikach binarnych nie są instrumentowane.<br /><br /> Można określić wiele specyfikacji funkcji z oddzielnymi opcjami **Dołączania.**<br /><br /> Nie należy używać opcji **Uwzględnij** i **Wyklucz,** które odwołują się do funkcji w tym samym pliku binarnym.<br /><br /> **Uwzględnij** nie jest obsługiwany z pokryciem kodu.<br /><br /> `funcspec`jest zdefiniowany jako:<br /><br /> [separator\<przestrzeni nazw1>] [separator klasy2\<>]funkcja<br /><br /> \<separator1> jest `::` dla kodu macierzystego i `.` kodu zarządzanego.<br /><br /> \<separator2> jest zawsze`::`<br /><br /> Obsługiwany jest \* symbol wieloznaczny. Na przykład, aby uwzględnić wszystkie funkcje w obszarze nazw, użyj:<br /><br /> Mynamespace::\*<br /><br /> Za pomocą **programu VSInstr /DumpFuncs** można wyświetlić pełną liczbę nazw funkcji w określonym pliku binarnym.|
|**DumpFuncs (WywrotkaFuncs**|Wyświetla listę funkcji w obrębie określonego obrazu. Oprzyrządowanie nie jest wykonywane.|
|**WykluczSmallFuncs**|Wyklucza małe funkcje, które są krótkimi funkcjami, które nie wykonują żadnych wywołań funkcji, z instrumentacji. Opcja **ExcludeSmallFuncs** zapewnia mniejszą oprzyrządowanie napowietrznych, a tym samym zwiększoną szybkość oprzyrządowania.<br /><br /> Wyłączenie małych funkcji zmniejsza również . *vsp* rozmiar pliku i czas wymagany do analizy.|
|**Oznacz:**{**przed**\|**za górną**\|**dolną**\|**dnem**}`,funcname,markid`|Wstawia znacznik profilu (identyfikator używany do rozdzielania danych w raportach), którego można użyć do zidentyfikowania początku lub końca zakresu danych w pliku raportu vsp.<br /><br /> **Przed** - Bezpośrednio przed wpisem funkcji docelowej.<br /><br /> **Po** - Natychmiast po zamknięciu funkcji docelowej.<br /><br /> **Góra** — natychmiast po wpisie funkcji docelowej.<br /><br /> **Dół** — bezpośrednio przed każdym powrotem w funkcji docelowej.<br /><br /> `funcname`- Nazwa funkcji docelowej<br /><br /> `Markid`- Dodatnia liczba całkowita (długa) do użycia jako identyfikator znaku profilu.|
|**Pokrycie**|Wykonuje instrumentację pokrycia. Może być używany tylko z **następującymi opcjami: Verbose**, **OutputPath**, **Exclude**i **Logfile**..|
|**Pełne**|Opcja Pełne służy do **wyświetlania** szczegółowych informacji o procesie instrumentacji.|
|**NoWarn (Niewarn)**`[:[Message Number[;Message Number]]]`|Pomiń wszystkie lub określone ostrzeżenia.<br /><br /> `Message Number`- numer ostrzegawczy. Jeśli `Message Number` zostanie pominięty, wszystkie ostrzeżenia są pomijane.<br /><br /> Aby uzyskać więcej informacji, zobacz [ostrzeżenia VSInstr](../profiling/vsinstr-warnings.md).|
|**Kontrola:** `{` **Globalny proces** \| **Global** **wątku** \|`}`|Określa poziom profilowania następujących opcji kontroli zbierania danych VSInstr:<br /><br /> **Początek**<br /><br /> **StartOnly (Tylko)**<br /><br /> **Suspend**<br /><br /> **StopOnly (Nie tylko)**<br /><br /> **SuspendOnly**<br /><br /> **ResumeOnly**<br /><br /> **Wątek** - określa funkcje kontroli zbierania danych na poziomie wątku. Profilowanie jest uruchamiane lub zatrzymywane tylko dla bieżącego wątku. Nie ma to wpływu na stan profilowania innych wątków. Wartość domyślna to wątek.<br /><br /> **Proces** — określa funkcje kontroli zbierania danych na poziomie procesu. Profilowanie rozpoczyna się lub zatrzymuje dla wszystkich wątków w bieżącym procesie. Nie ma to wpływu na stan profilowania innych procesów.<br /><br /> **Global** - określa funkcje kontroli zbierania danych na poziomie globalnym (między procesem).<br /><br /> Błąd występuje, jeśli nie określisz poziomu profilowania.|
|**Start:** `{` **Wewnątrz na** \| **zewnątrz**`},funcname`|Ogranicza zbieranie danych do funkcji docelowej i funkcji podrzędnych wywoływanych przez tę funkcję.<br /><br /> **Wewnątrz** — wstawia StartProfile funkcji natychmiast po wejściu do funkcji docelowej. Wstawia StopProfile funkcji bezpośrednio przed każdym powrotem w funkcji docelowej.<br /><br /> **Na zewnątrz** — wstawia StartProfile funkcji bezpośrednio przed każdym wywołaniu funkcji docelowej. Wstawia StopProfile funkcji natychmiast po każdym wywołaniu funkcji docelowej.<br /><br /> `funcname`- nazwa funkcji docelowej.|
|**Wstrzymaj:** `{` **Wewnątrz na** \| **zewnątrz**`},funcname`|Wyklucza zbieranie danych dla funkcji docelowej i funkcji podrzędnych wywoływanych przez funkcję.<br /><br /> **Wewnątrz** — wstawia SuspendProfile funkcji natychmiast po wprowadzeniu do funkcji docelowej. Wstawia ResumeProfile funkcji bezpośrednio przed każdym powrotem w funkcji docelowej.<br /><br /> **Na zewnątrz** — wstawia SuspendProfile funkcji bezpośrednio przed wpisem do funkcji docelowej. Wstawia ResumeProfile funkcji natychmiast po wyjściu z funkcji docelowej.<br /><br /> `funcname`- nazwa funkcji docelowej.<br /><br /> Jeśli funkcja docelowa zawiera funkcję StartProfile, przed nią wstawiana jest funkcja SuspendProfile. Jeśli funkcja docelowa zawiera funkcję StopProfile, po niej wstawiana jest funkcja ResumeProfile.|
|**StartOnly:** `{` **Przed** \| **po** \| górnej **dolnej** \| **Bottom**`},funcname`|Rozpoczyna zbieranie danych podczas przebiegu profilowania. Wstawia Funkcję interfejsu API StartProfile w określonej lokalizacji.<br /><br /> **Przed** - bezpośrednio przed wpisem funkcji docelowej.<br /><br /> **Po** - natychmiast po wyjściu funkcji docelowej.<br /><br /> **Top** - natychmiast po wpisie funkcji docelowej.<br /><br /> **Bottom** - bezpośrednio przed każdym powrotem w funkcji docelowej.<br /><br /> `funcname`- nazwa funkcji docelowej.|
|**StopOnly:**{**Przed**\|**po**\|**dolnej dolnej**\|**}**`,funcname`|Zatrzymuje zbieranie danych podczas przebiegu profilowania. Wstawia StopProfile funkcji w określonej lokalizacji.<br /><br /> **Przed** - bezpośrednio przed wpisem funkcji docelowej.<br /><br /> **Po** - natychmiast po wyjściu funkcji docelowej.<br /><br /> **Top** - natychmiast po wpisie funkcji docelowej.<br /><br /> **Bottom** - bezpośrednio przed każdym powrotem w funkcji docelowej.<br /><br /> `funcname`- nazwa funkcji docelowej.|
|**SuspendOnly:**{**Przed**\|**po dolnej**\|**dolnej**\|**}**`,funcname`|Zatrzymuje zbieranie danych podczas przebiegu profilowania. Wstawia SuspendProfile interfejsu API w określonej lokalizacji.<br /><br /> **Przed** - bezpośrednio przed wpisem funkcji docelowej.<br /><br /> **Po** - natychmiast po wyjściu funkcji docelowej.<br /><br /> **Top** - natychmiast po wpisie funkcji docelowej.<br /><br /> **Bottom** - bezpośrednio przed każdym powrotem w funkcji docelowej.<br /><br /> `funcname`- nazwa funkcji docelowej.<br /><br /> Jeśli funkcja docelowa zawiera funkcję StartProfile, przed nią wstawiana jest funkcja SuspendProfile.|
|**ResumeOnly:**{**Przed**\|**po dolnej**\|**dolnej**\|**}**`,funcname`|Rozpoczyna lub wznawia zbieranie danych podczas przebiegu profilowania.<br /><br /> Jest on zwykle używany do rozpoczęcia profilowania po **SuspendOnly** opcja została zatrzymana profilowania. Wstawia resumeProfile interfejsu API w określonej lokalizacji.<br /><br /> **Przed** - bezpośrednio przed wpisem funkcji docelowej.<br /><br /> **Po** - natychmiast po wyjściu funkcji docelowej.<br /><br /> **Top** - natychmiast po wpisie funkcji docelowej.<br /><br /> **Bottom** - bezpośrednio przed każdym powrotem w funkcji docelowej.<br /><br /> `funcname`- nazwa funkcji docelowej.<br /><br /> Jeśli funkcja docelowa zawiera funkcję StopProfile, po niej wstawiana jest funkcja ResumeProfile.|

## <a name="see-also"></a>Zobacz też
- [VSPerfMon](../profiling/vsperfmon.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [VSPerfReport](../profiling/vsperfreport.md)
- [Ostrzeżenia VSInstr](../profiling/vsinstr-warnings.md)
- [Widoki raportu o skuteczności](../profiling/performance-report-views.md)
