---
title: Specyfikatory formatu w debugerze (C++) | Microsoft Docs
description: Użyj specyfikatora formatu, aby zmienić format, w którym wartość jest wyświetlana w oknie Czujka, autostarty lub lokalne. Ten artykuł zawiera szczegółowe informacje dotyczące użycia.
ms.custom: SEO-VS-2020
ms.date: 3/11/2019
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
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
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 2a3fa99594f42e7e9c3739a8a8d57abf226bc04c
ms.sourcegitcommit: 66951f064d601b1d7a2253cb9b250380807e12db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2021
ms.locfileid: "103483196"
---
# <a name="format-specifiers-for-c-in-the-visual-studio-debugger"></a>Specyfikatory formatu dla języka C++ w debugerze programu Visual Studio

Można zmienić format, w którym wartość jest wyświetlana w oknach **czujka**, **autostarty** i **lokalne** przy użyciu specyfikatorów formatu.

Można również użyć specyfikatorów formatu w oknie **bezpośrednim** , oknie **polecenia** , w [punkty śledzenia](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints), a nawet w oknach źródłowych. Jeśli wstrzymasz w wyrażeniu w tych oknach, wynik zostanie wyświetlony w [etykietki danych](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Etykietki danych wyświetla specyfikator formatu.

> [!NOTE]
> Gdy debuger natywny programu Visual Studio został zmieniony na nowy aparat debugowania, dodano kilka nowych specyfikatorów formatu, a niektóre stare zostały usunięte. Starszy debuger jest nadal używany w przypadku debugowania międzyoperacyjności (natywne i zarządzane) przy użyciu języka C++/CLI.

## <a name="set-format-specifiers"></a>Ustaw specyfikatory formatu

Użyjemy następującego przykładowego kodu:

```C++
int main() {
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

Dodaj `my_var1` zmienną do okna **czujki** podczas debugowania, **Debuguj**  >    >  czujkę **czujki** w systemie Windows  >  **1**. Następnie kliknij prawym przyciskiem myszy zmienną i wybierz pozycję **Wyświetlanie w formacie szesnastkowym**. Teraz okno **czujki** pokazuje wartość 0x0065. Aby wyświetlić tę wartość wyrażoną jako znak, a nie liczbę całkowitą, najpierw kliknij prawym przyciskiem myszy i usuń zaznaczenie w **formacie szesnastkowym**. Następnie Dodaj specyfikator formatu znaku **, c** w kolumnie **Nazwa** po nazwie zmiennej. Kolumna **wartość** zawiera teraz **101 ' e '**.

![Zrzut ekranu programu Visual Studio okno wyrażeń kontrolnych z jednym zaznaczonym wierszem, który pokazuje my_var1. c z wartością 101 "e" i typem int.](../debugger/media/watchformatcplus1.png)

::: moniker range=">= vs-2019" 
Można wyświetlić i wybrać listę dostępnych specyfikatorów formatu, dołączając przecinek (,) do wartości w oknie **czujki** . 

![WatchFormatSpecDropdown](../debugger/media/vs-2019/format-specs-cpp.png "FormatSpecCpp")

::: moniker-end

## <a name="format-specifiers"></a><a name="BKMK_Visual_Studio_2012_format_specifiers"></a> Specyfikatory formatu

W poniższych tabelach opisano specyfikatory formatu, których można użyć w programie Visual Studio. Specyfikatory pogrubione są obsługiwane tylko dla nowych debugerów, a nie do debugowania międzyoperacyjności przy użyciu języka C++/CLI.

::: moniker range=">= vs-2019" 

|Specyfikator|Format|Oryginalna wartość czujki|Wyświetlana wartość|
|---------------|------------|--------------------------|---------------------|
|d|Liczba całkowita dziesiętna|0x00000066|102|
|o|Liczba całkowita bez znaku|0x00000066|000000000146|
|x<br /><br /> **h**|Szesnastkowa liczba całkowita|102|0xcccccccc|
|X<br /><br /> **C**|Szesnastkowa liczba całkowita|102|0xCCCCCCCC|
|XB<br /><br /> **HB**|Szesnastkowa liczba całkowita (bez wiodącego 0x)|102|cccccccc|
|XB<br /><br /> **HB**|Szesnastkowa liczba całkowita (bez wiodącego 0x)|102|CCCCCCCC|
|b|Liczba całkowita bez znaku|25|0b00000000000000000000000000011001|
|bb|Liczba całkowita binarna bez znaku (bez wiodących 0b)|25|00000000000000000000000000011001|
|e|zapis naukowy|25000000|2.500000 e + 07|
|g|krótsze lub zmiennoprzecinkowe|25000000|2.5 e + 07|
|c|pojedynczy znak|0x0065|101 ' e '|
|s|ciąg const char * (ze znakami cudzysłowu)|\<location> "Hello World"|"Hello World"|
|**SB**|ciąg const char * (bez cudzysłowów)|\<location> "Hello World"|Cześć ludzie|
|s8|Ciąg UTF-8|\<location> "To jest ̃ kawy w formacie UTF-8"|"To jest ☕ kawy w formacie UTF-8"|
|**s8b**|Ciąg UTF-8 (bez cudzysłowów)|\<location> "Hello World"|Cześć ludzie|
|Su|Ciąg Unicode (kodowanie UTF-16) (ze znakami cudzysłowu)|\<location> L "Hello World"|L "Hello World"<br /><br /> u "Hello World"|
|Sub|Ciąg Unicode (kodowanie UTF-16) (bez cudzysłowów)|\<location> L "Hello World"|Cześć ludzie|
|bstr|Ciąg binarny BSTR (ze znakami cudzysłowu)|\<location> L "Hello World"|L "Hello World"|
|kopert|Blok środowiska (ciąg zakończenia o wartości null)|\<location>L "=:: =:: \\ \\ "|L "=:: =:: \\ \\ \\ 0 = c: = c: \\ \\ Windows \\ \\ system32 \\ 0ALLUSERSPROFILE =...|
|**s32**|Ciąg UTF-32 (ze znakami cudzysłowu)|\<location> U "Hello World"|U "Hello World"|
|**s32b**|Ciąg UTF-32 (bez cudzysłowów)|\<location> U "Hello World"|Cześć ludzie|
|**en**|enum|Sobota (6)|Sobota|
|**HV**|Typ wskaźnika — wskazuje, że testowana wartość wskaźnika jest wynikiem alokacji sterty tablicy, na przykład `new int[3]` .|\<location>{\<first member>}|\<location>{\<first member>, \<second member>, ...}|
|**potrącon**|Pomija adres pamięci wskaźnika do obiektu.|\<location>, {member = Value...}|{member = wartość...}|
|**ND**|Wyświetla tylko informacje o klasie bazowej, ignorując klasy pochodne|`(Shape*) square` zawiera klasę bazową i informacje o klasie pochodnej|Wyświetla tylko informacje o klasie bazowej|
|godz.|Kod błędu HRESULT lub Win32. Ten specyfikator nie jest już wymagany dla HRESULT, ponieważ debuger dekoduje je automatycznie.|S_OK|S_OK|
|w górę|Flaga klasy okna|0x0010|WC_DEFAULTCHAR|
|Media|Numery komunikatów systemu Windows|16|WM_CLOSE|
|Nr|Pomijanie elementu "widok nieprzetworzony"|
|nvo|Pokaż element "RAW View" tylko dla wartości numerycznych|
|!|Format nieprzetworzony, ignorowanie dostosowanych widoków typów danych|\<customized representation>|4|

::: moniker-end

::: moniker range="vs-2017" 

|Specyfikator|Format|Oryginalna wartość czujki|Wyświetlana wartość|
|---------------|------------|--------------------------|---------------------|
|d|Liczba całkowita dziesiętna|0x00000066|102|
|o|Liczba całkowita bez znaku|0x00000066|000000000146|
|x<br /><br /> **h**|Szesnastkowa liczba całkowita|102|0xcccccccc|
|X<br /><br /> **C**|Szesnastkowa liczba całkowita|102|0xCCCCCCCC|
|c|pojedynczy znak|0x0065, c|101 ' e '|
|s|ciąg const char * (ze znakami cudzysłowu)|\<location> "Hello World"|"Hello World"|
|**SB**|ciąg const char * (bez cudzysłowów)|\<location> "Hello World"|Cześć ludzie|
|s8|Ciąg UTF-8|\<location> "To jest ̃ kawy w formacie UTF-8"|"To jest ☕ kawy w formacie UTF-8"|
|**s8b**|Ciąg UTF-8 (bez cudzysłowów)|\<location> "Hello World"|Cześć ludzie|
|Su|Ciąg Unicode (kodowanie UTF-16) (ze znakami cudzysłowu)|\<location> L "Hello World"|L "Hello World"<br /><br /> u "Hello World"|
|Sub|Ciąg Unicode (kodowanie UTF-16) (bez cudzysłowów)|\<location> L "Hello World"|Cześć ludzie|
|bstr|Ciąg binarny BSTR (ze znakami cudzysłowu)|\<location> L "Hello World"|L "Hello World"|
|kopert|Blok środowiska (ciąg zakończenia o wartości null)|\<location>L "=:: =:: \\ \\ "|L "=:: =:: \\ \\ \\ 0 = c: = c: \\ \\ Windows \\ \\ system32 \\ 0ALLUSERSPROFILE =...|
|**s32**|Ciąg UTF-32 (ze znakami cudzysłowu)|\<location> U "Hello World"|U "Hello World"|
|**s32b**|Ciąg UTF-32 (bez cudzysłowów)|\<location> U "Hello World"|Cześć ludzie|
|**en**|enum|Sobota (6)|Sobota|
|**HV**|Typ wskaźnika — wskazuje, że testowana wartość wskaźnika jest wynikiem alokacji sterty tablicy, na przykład `new int[3]` .|\<location>{\<first member>}|\<location>{\<first member>, \<second member>, ...}|
|**potrącon**|Pomija adres pamięci wskaźnika do obiektu.|\<location>, {member = Value...}|{member = wartość...}|
|**ND**|Wyświetla tylko informacje o klasie bazowej, ignorując klasy pochodne|`(Shape*) square` zawiera klasę bazową i informacje o klasie pochodnej|Wyświetla tylko informacje o klasie bazowej|
|godz.|Kod błędu HRESULT lub Win32. Ten specyfikator nie jest już wymagany dla HRESULT, ponieważ debuger dekoduje je automatycznie.|S_OK|S_OK|
|w górę|Flaga klasy okna|0x0010|WC_DEFAULTCHAR|
|Media|Numery komunikatów systemu Windows|16|WM_CLOSE|
|!|Format nieprzetworzony, ignorowanie dostosowanych widoków typów danych|\<customized representation>|4|

::: moniker-end

> [!NOTE]
> Gdy jest obecny Specyfikator formatu **HV** , debuger próbuje określić długość buforu i wyświetlić tę liczbę elementów. Ponieważ nie zawsze jest możliwe, aby debuger znalazł dokładny rozmiar buforu tablicy, należy użyć specyfikatora rozmiaru `(pBuffer,[bufferSize])` wszędzie tam, gdzie to możliwe. Specyfikator formatu **HV** jest przydatny, gdy rozmiar buforu nie jest łatwo dostępny.

### <a name="size-specifiers-for-pointers-as-arrays"></a><a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> Specyfikatory rozmiaru dla wskaźników jako tablic

Jeśli masz wskaźnik do obiektu, który chcesz wyświetlić jako tablicę, możesz użyć liczby całkowitej lub wyrażenia, aby określić liczbę elementów tablicy.

|Specyfikator|Format|Oryginalna wartość czujki|Wyświetlana wartość|
|---------------|------------|---------------------------|---------------------|
|n|Dziesiętna lub **szesnastkowa** liczba całkowita|pBuffer, [32]<br /><br /> pBuffer,**[0x20]**|Wyświetla `pBuffer` jako tablicę elementów 32.|
|**EXP**|Prawidłowe wyrażenie języka C++, które daje w wyniku liczbę całkowitą.|pBuffer, [bufferSize]|Wyświetla pBuffer jako tablicę `bufferSize` elementów.|
|**Rozwiń (n)**|Prawidłowe wyrażenie języka C++, które daje w wyniku liczbę całkowitą|pBuffer, rozwiń (2)|Wyświetla trzeci element  `pBuffer`|

## <a name="format-specifiers-for-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> Specyfikatory formatu na potrzeby debugowania międzyoperacyjnego przy użyciu języka C++/CLI

Specyfikatory **pogrubione** są obsługiwane tylko na potrzeby debugowania kodu natywnego i C++/CLI. Wymaga to starszego debugera, określonego przy użyciu [zarządzanego trybu zgodności](../debugger/general-debugging-options-dialog-box.md).

|Specyfikator|Format|Oryginalna wartość czujki|Wyświetlana wartość|
|---------------|------------|--------------------------|---------------------|
|**d**<br /><br />**i**|cyfra dziesiętna ze znakiem|0xF000F065|-268373915|
|**'t**|Liczba całkowita dziesiętna bez znaku|0x0065|101|
|o|Liczba całkowita bez znaku|0xF065|0170145|
|x<br /><br />X|Szesnastkowa liczba całkowita|61541|0x0000f065|
|**&**<br /><br />**h**|długi lub krótki prefiks dla: d, i, u, o, x, X|00406042|0x0c22|
|**n**|podpisany zmiennoprzecinkowy|(3./2.), f|1,500000|
|**adres**|Notacja naukowa ze znakiem|(3.0/2.0)|1.500000 e + 000|
|**g**|podpisany element zmiennoprzecinkowy lub podpisany Zapis naukowy,<br/> w zależności od tego co jest krótsze|(3.0/2.0)|1.5|
|c|pojedynczy znak|\<location>|101 ' e '|
|s|const char * (ze znakami cudzysłowu)|\<location>|"Hello World"|
|Su|const wchar_t *<br /><br /> const char16_t \* (ze znakami cudzysłowu)|\<location>|L "Hello World"|
|Sub|const wchar_t *<br /><br /> stała char16_t\*|\<location>|Cześć ludzie|
|s8|const char * (ze znakami cudzysłowu)|\<location>|"Hello World"|
|godz.|Kod błędu HRESULT lub Win32.<br/>Ten specyfikator nie jest już wymagany dla HRESULT, ponieważ debuger dekoduje je automatycznie.|S_OK|S_OK|
|w górę|Flaga klasy okna|0x00000040|WC_DEFAULTCHAR|
|Media|Numery komunikatów systemu Windows|0x0010|WM_CLOSE|
|!|Format nieprzetworzony, ignorowanie wszelkich dostosowań widoku typu danych|\<customized representation>|4|

### <a name="format-specifiers-for-memory-locations-in-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> Specyfikatory formatu dla lokalizacji pamięci podczas debugowania międzyoperacyjności przy użyciu języka C++/CLI

W poniższej tabeli opisano symbole formatowania używane dla lokalizacji pamięci. Można użyć specyfikatora lokalizacji pamięci z dowolną wartością lub wyrażeniem, które jest oceniane do lokalizacji.

Specyfikatory **pogrubione** są obsługiwane tylko na potrzeby debugowania kodu natywnego i C++/CLI. Wymaga to starszego debugera, określonego przy użyciu [zarządzanego trybu zgodności](../debugger/general-debugging-options-dialog-box.md).

|Symbol|Format|Oryginalna wartość czujki|Wyświetlana wartość|
|------------|------------|--------------------------|---------------------|
|**ruchom**|64 znaków ASCII|0x0012ffac|0x0012ffac. 4... 0... ". 0W&...... 1W&.0.: W... 1.... ".. 1.JO&.1,2... 1... 0y... jedno|
|**m**|16 bajtów w formacie szesnastkowym, po których następuje 16 znaków ASCII|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00.4... 0.... 0W&..|
|**megabit**|16 bajtów w formacie szesnastkowym, po których następuje 16 znaków ASCII|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00.4... 0.... 0W&..|
|**MW**|8 słów|0x0012ffac|0x0012ffac 34B3 00CB 3084 8094 22FF 308A 2657 0000|
|**algorytmu**|4 doublewords|0x0012ffac|0x0012ffac 00CB34B3 80943084 308A22FF 00002657|
|**MQ**|2 quadwords|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|
|**mu**|znaki dwubajtowe (Unicode)|0x0012ffac|0x0012ffac 8478 77f4 FFFF FFFF 0000 0000 0000 0000|

### <a name="size-specifier-for-pointers-as-arrays-in-interop-debugging-with-ccli"></a><a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> Specyfikator rozmiaru dla wskaźników jako tablice w debugowaniu międzyoperacyjnym z C++/CLI

Jeśli masz wskaźnik do obiektu, który chcesz wyświetlić jako tablicę, możesz użyć liczby całkowitej, aby określić liczbę elementów tablicy.

|Specyfikator|Format|Wyrażenie|Wyświetlana wartość|
|---------------|------------|----------------|---------------------|
|n|Liczba całkowita dziesiętna|pBuffer [32]|`pBuffer`Jest wyświetlana jako tablica elementów 32.|