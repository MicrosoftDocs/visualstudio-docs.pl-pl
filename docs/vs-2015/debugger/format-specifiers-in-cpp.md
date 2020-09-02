---
title: Specyfikatory formatu w języku C++ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- QuickWatch dialog box, format specifiers in C++
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- expressions [C++], format specifiers
- specifiers, watch variable format
- specifiers
- Watch window, format specifiers in C++
- watch variable symbols
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 0f6f3b7c-ce2c-4b4d-b14f-7589dbed5444
caps.latest.revision: 45
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9f620cbf5d522b99965268f35c00ff8e874f1542
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64834162"
---
# <a name="format-specifiers-in-c"></a>Specyfikatory formatu w C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zmienić format, w którym wartość jest wyświetlana w oknie **czujki** przy użyciu specyfikatorów formatu.  
  
 Można również użyć specyfikatorów formatu w oknie **bezpośrednim** , oknie **polecenia** , a nawet w oknach źródłowych. W przypadku wstrzymania na wyrażeniu w tych oknach wynik zostanie wyświetlony w etykietki danych. Etykietki danych wyświetla specyfikator formatu.  
  
> [!NOTE]
> Debuger natywny programu Visual Studio został zmieniony na nowy aparat debugowania. W ramach tej zmiany dodano kilka nowych specyfikatorów formatu, a niektóre stare zostały usunięte. Starszy debuger jest nadal używany w przypadku debugowania międzyoperacyjności (natywne i zarządzane) przy użyciu języka C++/CLI. W poniższych sekcjach tego tematu przedstawiono specyfikatory formatu dla każdego aparatu debugowania.  
> 
> - [Specyfikatory formatu](#BKMK_Visual_Studio_2012_format_specifiers) opisują specyfikatory formatu w nowym aparacie debugowania.  
>   - [Specyfikatory formatu dla debugowania międzyoperacyjnego przy użyciu języka C++/CLI](#BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue) opisują specyfikatory formatu w starszym aparacie debugowania.  
  
## <a name="using-format-specifiers"></a>Używanie specyfikatorów formatu  
 Jeśli masz następujący kod:  
  
```cpp  
int main() {  
    int my_var1 = 0x0065;  
    int my_var2 = 0x0066;  
    int my_var3 = 0x0067;  
}  
```  
  
 Dodaj `my_var1` zmienną do okna **czujki** (podczas debugowania, **Debuguj/Windows/Watch/Watch 1**) i ustaw wartość wyświetlaną na szesnastkową (w oknie **czujka** kliknij zmienną prawym przyciskiem myszy i wybierz pozycję **wyświetlacz szesnastkowy**). Teraz okno wyrażeń kontrolnych pokazuje, że zawiera wartość 0x0065. Aby wyświetlić tę wartość wyrażoną jako znak zamiast liczby całkowitej, w kolumnie Nazwa po nazwie zmiennej Dodaj specyfikator formatu znaku **, c**. Kolumna **wartość** będzie teraz wyświetlana z **101 ' e '**.  
  
 ![WatchFormatCPlus1](../debugger/media/watchformatcplus1.png "WatchFormatCPlus1")  
  
## <a name="format-specifiers"></a><a name="BKMK_Visual_Studio_2012_format_specifiers"></a> Specyfikatory formatu  
 W poniższych tabelach przedstawiono specyfikatory formatu, których można użyć w programie Visual Studio. Specyfikatory pogrubione nie są obsługiwane w przypadku debugowania międzyoperacyjnego w języku C++/CLI.  
  
|Specyfikator|Format|Oryginalna wartość czujki|Wyświetlana wartość|  
|---------------|------------|--------------------------|---------------------|  
|d|Liczba całkowita dziesiętna|0x00000066|102|  
|o|Liczba całkowita bez znaku|0x00000066|000000000146|  
|x<br /><br /> **c**|Szesnastkowa liczba całkowita|102|0xcccccccc|  
|X<br /><br /> **H**|Szesnastkowa liczba całkowita|102|0xCCCCCCCC|  
|c|pojedynczy znak|0x0065, c|101 ' e '|  
|s|ciąg const char *|\<location> "Hello World"|"Hello World"|  
|**SB**|ciąg const char *|\<location> "Hello World"|Cześć ludzie|  
|s8|ciąg const char *|\<location> "Hello World"|"Hello World"|  
|**s8b**|ciąg const char *|\<location> "Hello World"|"Hello World"|  
|Su|const wchar_t * const<br /><br /> \*ciąg char16_t|\<location> L "Hello World"|L "Hello World"<br /><br /> u "Hello World"|  
|Sub|const wchar_t * const<br /><br /> \*ciąg char16_t|\<location> L "Hello World"|Cześć ludzie|  
|bstr|Ciąg BSTR|\<location> L "Hello World"|L "Hello World"|  
|**s32**|Ciąg UTF-32|\<location> U "Hello World"|U "Hello World"|  
|**s32b**|Ciąg UTF-32 (bez cudzysłowów)|\<location> U "Hello World"|Cześć ludzie|  
|**półpauzy**|enum|Sobota (6)|Sobota|  
|**HV**|Typ wskaźnika — wskazuje, że testowana wartość wskaźnika jest wynikiem alokacji sterty tablicy, na przykład `new int[3]` .|\<location>{\<first member>}|\<location>{\<first member>, \<second member>, …}|  
|**potrącon**|Pomija adres pamięci wskaźnika do obiektu.|\<location>, {member = Value...}|{member = wartość...}|  
|**ND**|Wyświetla tylko informacje o klasie bazowej, ignorując klasy pochodne|`(Shape*) square` zawiera klasę bazową i informacje o klasie pochodnej|Wyświetla tylko informacje o klasie bazowej|  
|godz.|Kod błędu HRESULT lub Win32. (Debuger teraz dekoduje HRESULTs automatycznie, dlatego ten specyfikator nie jest wymagany w takich przypadkach.|S_OK|S_OK|  
|w górę|Flaga klasy okna|0x0010|WC_DEFAULTCHAR|  
|Media|Numery komunikatów systemu Windows|16|WM_CLOSE|  
|!|Format nieprzetworzony, ignorowanie dostosowanych widoków typów danych|\<customized representation>|4|  
  
> [!NOTE]
> Gdy jest obecny Specyfikator formatu **HV** , debuger próbuje określić długość buforu i wyświetlić odpowiednią liczbę elementów. Ponieważ nie zawsze jest możliwe, aby debuger znalazł dokładny rozmiar buforu tablicy, należy użyć specyfikatora rozmiaru `(pBuffer,[bufferSize])` wszędzie tam, gdzie to możliwe. Specyfikator formatu **HV** jest przeznaczony dla scenariuszy, w których rozmiar buforu nie jest łatwo dostępny  
  
### <a name="size-specifiers-for-pointers-as-arrays"></a><a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> Specyfikatory rozmiaru dla wskaźników jako tablic  
 Jeśli masz wskaźnik do obiektu, który chcesz wyświetlić jako tablicę, możesz użyć liczby całkowitej lub wyrażenia, aby określić liczbę elementów tablicy:  
  
|Specyfikator|Format|Oryginalny Valuen czujki|Wyświetlana wartość|  
|---------------|------------|---------------------------|---------------------|  
|n|Dziesiętna lub **szesnastkowa** liczba całkowita|pBuffer, [32]<br /><br /> pBuffer,**[0x20]**|Wyświetla `pBuffer` jako tablicę elementów 32.|  
|**EXP**|Prawidłowe wyrażenie języka C++, które daje w wyniku liczbę całkowitą.|pBuffer, [bufferSize]|Wyświetla pBuffer jako tablicę `bufferSize` elementów.|  
|**Rozwiń (n)**|Prawidłowe wyrażenie języka C++, które daje w wyniku liczbę całkowitą|pBuffer, rozwiń (2)|Wyświetla trzeci element  `pBuffer`|  
  
## <a name="format-specifiers-for-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> Specyfikatory formatu na potrzeby debugowania międzyoperacyjnego przy użyciu języka C++/CLI  
 Specyfikatory **pogrubione** są obsługiwane tylko na potrzeby debugowania kodu natywnego i C++/CLI.  
  
|Specyfikator|Format|Oryginalna wartość czujki|Wyświetlana wartość|  
|---------------|------------|--------------------------|---------------------|  
|**d, i**|cyfra dziesiętna ze znakiem|0xF000F065|-268373915|  
|**'t**|Liczba całkowita dziesiętna bez znaku|0x0065|101|  
|o|Liczba całkowita bez znaku|0xF065|0170145|  
|x, X|Szesnastkowa liczba całkowita|61541|0x0000f065|  
|**l, h**|długi lub krótki prefiks dla: d, i, u, o, x, X|00406042|0x0c22|  
|**n**|podpisany zmiennoprzecinkowy|(3./2.), f|1,500000|  
|**adres**|Notacja naukowa ze znakiem|(3.0/2.0)|1.500000 e + 000|  
|**g**|podpisana liczba zmiennoprzecinkowa lub cyfra, w zależności od tego, co jest krótsza|(3.0/2.0)|1.5|  
|c|pojedynczy znak|\<location>|101 ' e '|  
|s|const char *|\<location>|"Hello World"|  
|Su|const wchar_t *<br /><br /> stała char16_t\*|\<location>|L "Hello World"|  
|Sub|const wchar_t *<br /><br /> stała char16_t\*|\<location>|Cześć ludzie|  
|s8|const char *|\<location>|"Hello World"|  
|godz.|Kod błędu HRESULT lub Win32. (Debuger teraz dekoduje HRESULTs automatycznie, dlatego ten specyfikator nie jest wymagany w takich przypadkach.|S_OK|S_OK|  
|w górę|Flaga klasy okna.|0x00000040|WC_DEFAULTCHAR|  
|Media|Numery komunikatów systemu Windows|0x0010|WM_CLOSE|  
|!|Format nieprzetworzony, ignorowanie dostosowanych widoków typów danych|\<customized representation>|4|  
  
### <a name="format-specifiers-memory-locations-in-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> Lokalizacje pamięci specyfikatorów formatu podczas debugowania międzyoperacyjności przy użyciu języka C++/CLI  
 Poniższa tabela zawiera symbole formatowania używane dla lokalizacji pamięci. Można użyć specyfikatora lokalizacji pamięci z dowolną wartością lub wyrażeniem, które jest oceniane do lokalizacji.  
  
|Symbol|Format|Oryginalna wartość czujki|Wyświetlana wartość|  
|------------|------------|--------------------------|---------------------|  
|**ruchom**|64 znaków ASCII|0x0012ffac|0x0012ffac. 4... 0... ". 0W&...... 1W&.0.: W... 1.... ".. 1.JO&.1,2... 1... 0y... jedno|  
|**mol**|16 bajtów w formacie szesnastkowym, po których następuje 16 znaków ASCII|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00.4... 0.... 0W&..|  
|**megabit**|16 bajtów w formacie szesnastkowym, po których następuje 16 znaków ASCII|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00.4... 0.... 0W&..|  
|**MW**|8 słów|0x0012ffac|0x0012ffac 34B3 00CB 3084 8094 22FF 308A 2657 0000|  
|**algorytmu**|4 doublewords|0x0012ffac|0x0012ffac 00CB34B3 80943084 308A22FF 00002657|  
|**MQ**|2 quadwords|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|  
|**mu**|znaki dwubajtowe (Unicode)|0x0012ffac|0x0012ffac 8478 77f4 FFFF FFFF 0000 0000 0000 0000|  
  
### <a name="size-specifier-for-pointers-as-arrays-in-interop-debugging-with-cclit"></a><a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> Specyfikator rozmiaru dla wskaźników jako tablice w debugowaniu międzyoperacyjnym z C++/CLIt  
 Jeśli masz wskaźnik do obiektu, który chcesz wyświetlić jako tablicę, możesz użyć liczby całkowitej, aby określić liczbę elementów tablicy:  
  
|Specyfikator|Format|Wyrażenie|Wyświetlana wartość|  
|---------------|------------|----------------|---------------------|  
|n|Liczba całkowita dziesiętna|pBuffer [32]|Wyświetla `pBuffer` jako tablicę elementów 32.|
