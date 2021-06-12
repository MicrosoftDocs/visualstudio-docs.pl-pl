---
title: Specyfikatory formatu w debugerze (C++) | Microsoft Docs
description: Użyj specyfikatora formatu, aby zmienić format, w którym wartość jest wyświetlana w oknie Czujka, Automatyczne lub Ustawienia lokalne. Ten artykuł zawiera szczegółowe informacje o użyciu.
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
ms.openlocfilehash: 868c02091814fe49ea0224190c7d205e8b67c42b
ms.sourcegitcommit: 4b2b6068846425f6964c1fd867370863fc4993ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2021
ms.locfileid: "112042980"
---
# <a name="format-specifiers-for-c-in-the-visual-studio-debugger"></a>Specyfikatory formatu dla języka C++ w Visual Studio debugerze

Format, w którym wartość jest wyświetlana w oknach  **Czujka,** **Automatyczne** i Lokalne, można zmienić przy użyciu specyfikatorów formatu.

Specyfikatorów formatu można również  używać w oknie Natychmiastowe, **oknie** Polecenia, [w](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)punktach śledzenia, a nawet w oknach źródłowych. Jeśli wstrzymasz wyrażenie w tych oknach, wynik zostanie wyświetlony w [etykietce danych](../debugger/view-data-values-in-data-tips-in-the-code-editor.md). Wyświetlanie etykietki danych odzwierciedla specyfikator formatu.

> [!NOTE]
> Gdy Visual Studio debuger natywny został zmieniony na nowy aparat debugowania, dodano nowe specyfikatory formatu i usunięto niektóre stare. Starszy debuger jest nadal używany podczas debugowania międzyplatopowego (mieszanego natywnego i zarządzanego) za pomocą języka C++/interfejsu wiersza polecenia.

## <a name="set-format-specifiers"></a>Ustawianie specyfikatorów formatu

Użyjemy następującego przykładowego kodu:

```C++
int main() {
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

Dodaj `my_var1` zmienną do okna **Czujka** podczas debugowania, Debug Windows Watch Watch 1 ( **Debugowanie**  >  **w systemie Windows**  >  **Watch**  >  **1).** Następnie kliknij prawym przyciskiem myszy zmienną i wybierz pozycję **Wyświetl szesnastkową**. Teraz **w oknie Czujka** zostanie pokazana wartość 0x0065. Aby wyświetlić tę wartość wyrażoną jako znak, a nie jako liczba całkowita, najpierw kliknij prawym przyciskiem myszy i usuń zaznaczenie opcji **Wyświetl szesnastkowo.** Następnie dodaj specyfikator formatu znaków **, c** w **kolumnie Nazwa** po nazwie zmiennej. Kolumna **Wartość** zawiera teraz **wartość 101 "e".**

![Zrzut ekranu przedstawiający Visual Studio okno wyrażeń kontrolnych z jednym wybranym wierszem, który my_var1.c z wartością 101 "e" i typem int.](../debugger/media/watchformatcplus1.png)

::: moniker range=">= vs-2019" 
Możesz wyświetlić i wybrać z listy dostępnych specyfikatorów formatu, dołączając przecinek (,) do wartości w oknie **Czujka.** 

![WatchFormatSpecDropdown](../debugger/media/vs-2019/format-specs-cpp.png "FormatSpecCpp")

::: moniker-end

## <a name="format-specifiers"></a><a name="BKMK_Visual_Studio_2012_format_specifiers"></a> Specyfikatory formatu

W poniższych tabelach opisano specyfikatory formatu, których można używać w Visual Studio. Specyfikatory pogrubione są obsługiwane tylko w nowym debugerze, a nie w przypadku debugowania międzyopcyjnie w języku C++/interfejsie wiersza polecenia.

::: moniker range=">= vs-2019" 

|Specyfikator|Format|Oryginalna wartość zegarka|Wyświetlana wartość|
|---------------|------------|--------------------------|---------------------|
|d|liczba całkowita dziesiętna|0x00000066|102|
|o|niepodpisane ósemkowe liczby całkowite|0x00000066|000000000146|
|x<br /><br /> **h**|szesnastkową liczbę całkowitą|102|0xcccccccc|
|X<br /><br /> **H**|szesnastkową liczbę całkowitą|102|0xCCCCCCCC|
|Xb<br /><br /> **Hb**|szesnastkowa liczba całkowita (bez wiodącej 0x)|102|przejściacccc|
|Xb<br /><br /> **Hb**|szesnastkowa liczba całkowita (bez wiodącej 0x)|102|PRZEJŚCIACCCCC|
|b|niepodpisane binarne liczby całkowite|25|0b000000000000000000000000000011001|
|bb|niepodpisane binarne liczby całkowite (bez wiodącej liczby 0b)|25|00000000000000000000000000011001|
|e|zapis naukowy|25000000|2,500000e+07|
|g|krótszy punkt naukowy lub zmiennoprzecinkowy|25000000|2,5e+07|
|c|pojedynczy znak|0x0065|101 "e"|
|s|const char* ciąg (ze znakami cudzysłowu)|\<location> "hello world"|"hello world"|
|**Sb**|const char* ciąg (bez cudzysłowów)|\<location> "hello world"|Cześć ludzie|
|s8|Ciąg UTF-8|\<location> "To jest kubek do kawy UTF-8 â ̃•"|"To jest ekspres do kawy UTF-8 ☕"|
|**s8b**|Ciąg UTF-8 (bez cudzysłowów)|\<location> "hello world"|Cześć ludzie|
|Su|Ciąg Unicode (kodowanie UTF-16) (ze znakami cudzysłowu)|\<location> L"hello world"|L"hello world"<br /><br /> u"hello world"|
|Sub|Ciąg Unicode (kodowanie UTF-16) (bez cudzysłowów)|\<location> L"hello world"|Cześć ludzie|
|bstr|Ciąg binarny BSTR (ze znakami cudzysłowu)|\<location> L"hello world"|L"hello world"|
|Env|Blok środowiska (ciąg zakończony z podwójną wartością null)|\<location>L"=::=:: \\ \\ "|L"=::=:: \\ \\ \\ 0=C:=C: \\ \\ windows \\ \\ system32 \\ 0ALLUSERSPROFILE=...|
|**s32**|Ciąg UTF-32 (ze znakami cudzysłowu)|\<location> U"hello world"|U"hello world"|
|**s32b**|Ciąg UTF-32 (bez cudzysłowów)|\<location> U"hello world"|Cześć ludzie|
|**en**|enum|Saturday(6)|Sobota|
|**Hv**|Typ wskaźnika — wskazuje, że sprawdzana wartość wskaźnika jest wynikiem alokacji sterty tablicy, na przykład `new int[3]` .|\<location>{\<first member>}|\<location>{\<first member>, \<second member>, ...}|
|**Na**|Pomija adres pamięci wskaźnika do obiektu.|\<location>, {member=value...}|{member=value...}|
|**Nd**|Wyświetla tylko informacje o klasie bazowej, ignorując klasy pochodne|`(Shape*) square` zawiera informacje o klasie bazowej i klasie pochodnej|Wyświetla tylko informacje o klasie bazowej|
|godz.|Kod błędu HRESULT lub Win32. Ten specyfikator nie jest już potrzebny w przypadku hresultów HRESULTs, ponieważ debuger dekoduje je automatycznie.|S_OK|S_OK|
|wc|Flaga klasy okna|0x0010|WC_DEFAULTCHAR|
|Wm|Numery komunikatów systemu Windows|16|WM_CLOSE|
|nr|Pomijanie elementu "Nieprzetworzone widoki"|
|nvo|Pokaż element "Nieprzetworzone widoki" tylko dla wartości liczbowych|
|!|format pierwotny, ignorując wszelkie dostosowania widoków typów danych|\<customized representation>|4|
|Obsługi|Wyświetla informacje o dojściu win32|0x000000000000009c| Wyświetla przydatne informacje o dojściu, takie jak identyfikator wątku itp. |

::: moniker-end

::: moniker range="vs-2017" 

|Specyfikator|Format|Oryginalna wartość zegarka|Wyświetlana wartość|
|---------------|------------|--------------------------|---------------------|
|d|liczba całkowita dziesiętna|0x00000066|102|
|o|niepodpisane ósemkowe liczby całkowite|0x00000066|000000000146|
|x<br /><br /> **h**|szesnastkową liczbę całkowitą|102|0xcccccccc|
|X<br /><br /> **H**|szesnastkową liczbę całkowitą|102|0xCCCCCCCC|
|c|pojedynczy znak|0x0065, c|101 "e"|
|s|const char* ciąg (ze znakami cudzysłowu)|\<location> "hello world"|"hello world"|
|**Sb**|const char* ciąg (bez cudzysłowów)|\<location> "hello world"|Cześć ludzie|
|s8|Ciąg UTF-8|\<location> "To jest kubek do kawy UTF-8 â ̃•"|"To jest ekspres do kawy UTF-8 ☕"|
|**s8b**|Ciąg UTF-8 (bez cudzysłowów)|\<location> "hello world"|Cześć ludzie|
|Su|Ciąg Unicode (kodowanie UTF-16) (ze znakami cudzysłowu)|\<location> L"hello world"|L"hello world"<br /><br /> u"hello world"|
|Sub|Ciąg Unicode (kodowanie UTF-16) (bez cudzysłowu)|\<location> L"hello world"|Cześć ludzie|
|bstr|Ciąg binarny BSTR (ze znakami cudzysłowu)|\<location> L"hello world"|L"hello world"|
|Env|Blok środowiska (ciąg zakończony z podwójną wartością null)|\<location>L"=::=:: \\ \\ "|L"=::=:: \\ \\ \\ 0=C:=C: \\ \\ windows \\ \\ system32 \\ 0ALLUSERSPROFILE=...|
|**s32**|Ciąg UTF-32 (ze znakami cudzysłowu)|\<location> U"hello world"|U"hello world"|
|**s32b**|Ciąg UTF-32 (bez cudzysłowów)|\<location> U"hello world"|Cześć ludzie|
|**en**|enum|Saturday(6)|Sobota|
|**Hv**|Typ wskaźnika — wskazuje, że sprawdzana wartość wskaźnika jest wynikiem alokacji sterty tablicy, na przykład `new int[3]` .|\<location>{\<first member>}|\<location>{\<first member>, \<second member>, ...}|
|**Na**|Pomija adres pamięci wskaźnika do obiektu.|\<location>, {member=value...}|{member=value...}|
|**Nd**|Wyświetla tylko informacje o klasie bazowej, ignorując klasy pochodne|`(Shape*) square` zawiera informacje o klasie bazowej i klasie pochodnej|Wyświetla tylko informacje o klasie bazowej|
|godz.|Kod błędu HRESULT lub Win32. Ten specyfikator nie jest już potrzebny w przypadku hresultów HRESULTs, ponieważ debuger dekoduje je automatycznie.|S_OK|S_OK|
|wc|Flaga klasy okna|0x0010|WC_DEFAULTCHAR|
|Wm|Numery komunikatów systemu Windows|16|WM_CLOSE|
|!|format pierwotny, ignorując wszelkie dostosowania widoków typów danych|\<customized representation>|4|

::: moniker-end

> [!NOTE]
> Gdy **specyfikator** formatu hv jest obecny, debuger próbuje określić długość buforu i wyświetlić liczbę elementów. Ponieważ nie zawsze jest możliwe, aby debuger znalazł dokładny rozmiar buforu tablicy, należy używać specyfikatora rozmiaru zawsze, gdy `(pBuffer,[bufferSize])` jest to możliwe. Specyfikator **formatu hv** jest przydatny, gdy rozmiar buforu nie jest łatwo dostępny.

### <a name="size-specifiers-for-pointers-as-arrays"></a><a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> Specyfikatory rozmiaru dla wskaźników jako tablic

Jeśli masz wskaźnik do obiektu, który chcesz wyświetlić jako tablicę, możesz użyć liczby całkowitej lub wyrażenia, aby określić liczbę elementów tablicy.

|Specyfikator|Format|Oryginalna wartość zegarka|Wyświetlana wartość|
|---------------|------------|---------------------------|---------------------|
|n|Liczba **dziesiętna lub szesnastkowa liczba całkowita**|pBuffer,[32]<br /><br /> pBuffer,**[0x20]**|Wyświetla `pBuffer` jako tablicę 32-elementową.|
|**[exp]**|Prawidłowe wyrażenie języka C++, które jest obliczane jako liczba całkowita.|pBuffer,[bufferSize]|Wyświetla element pBuffer jako tablicę `bufferSize` elementów.|
|**expand(n)**|Prawidłowe wyrażenie języka C++, które jest obliczane jako liczba całkowita|pBuffer, expand(2)|Wyświetla trzeci element elementu  `pBuffer`|

## <a name="format-specifiers-for-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> Specyfikatory formatu na potrzeby debugowania międzyoptyków w języku C++/interfejsie wiersza polecenia

Specyfikatory pogrubione **są** obsługiwane tylko w przypadku debugowania kodu natywnego i C++/CLI. Wymaga to starszego debugera określonego przy użyciu trybu [zgodności zarządzanej.](../debugger/general-debugging-options-dialog-box.md)

|Specyfikator|Format|Oryginalna wartość zegarka|Wyświetlana wartość|
|---------------|------------|--------------------------|---------------------|
|**d**<br /><br />**i**|liczba całkowita ze znakami dziesiętnych|0xF000F065|-268373915|
|**U**|liczba całkowita dziesiętna bez znaku|0x0065|101|
|o|niepodpisane ósemkowe liczby całkowite|0xF065|0170145|
|x<br /><br />X|Szesnastkowa liczba całkowita|61541|0x0000f065|
|**L**<br /><br />**h**|długi lub krótki prefiks dla: d, i, u, o, x, X|00406042|0x0c22|
|**F**|zmiennoprzecinkowy ze podpisem|(3./2.), f|1.500000|
|**E**|podpisana notacja naukowa|(3.0/2.0)|1,500000e+000|
|**G**|podpisana zmiennoprzecinkowa lub podpisana notacja naukowa,<br/> w zależności od tego, która wartość jest krótsza|(3.0/2.0)|1.5|
|c|pojedynczy znak|\<location>|101 "e"|
|s|const char* (ze znakami cudzysłowu)|\<location>|"hello world"|
|Su|const wchar_t*<br /><br /> const char16_t \* (ze znakami cudzysłowu)|\<location>|L"hello world"|
|Sub|const wchar_t*<br /><br /> const char16_t\*|\<location>|Cześć ludzie|
|s8|const char* (ze znakami cudzysłowu)|\<location>|"hello world"|
|godz.|Kod błędu HRESULT lub Win32.<br/>Ten specyfikator nie jest już potrzebny w przypadku hresultów HRESULTs, ponieważ debuger dekoduje je automatycznie.|S_OK|S_OK|
|wc|Flaga klasy okna|0x00000040,|WC_DEFAULTCHAR|
|Wm|Numery komunikatów systemu Windows|0x0010|WM_CLOSE|
|!|format pierwotny, ignorując wszelkie dostosowania widoku typu danych|\<customized representation>|4|

### <a name="format-specifiers-for-memory-locations-in-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> Specyfikatory formatu dla lokalizacji pamięci w debugowaniu międzyoptyków przy użyciu języka C++/interfejsu wiersza polecenia

W poniższej tabeli opisano symbole formatowania używane dla lokalizacji pamięci. Można użyć specyfikatora lokalizacji pamięci z dowolną wartością lub wyrażeniem, które oblicza lokalizację.

Specyfikatory pogrubione **są** obsługiwane tylko w przypadku debugowania kodu natywnego i C++/CLI. Wymaga to starszego debugera określonego przy użyciu trybu [zgodności zarządzanej.](../debugger/general-debugging-options-dialog-box.md)

|Symbol|Format|Oryginalna wartość zegarka|Wyświetlana wartość|
|------------|------------|--------------------------|---------------------|
|**ma**|64 znaki ASCII|0x0012ffac|0x0012ffac .4...0...". 0W&. 1W&.0.:W.. 1....".. 1.JO&.1.2."... 1...0y...... 1|
|**m**|16 bajtów w postaci szesnastkowej, po których następuje 16 znaków ASCII|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...". 0W&..|
|**Mb**|16 bajtów w postaci szesnastkowej, po których następuje 16 znaków ASCII|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...". 0W&..|
|**Mw**|8 wyrazów|0x0012ffac|0x0012ffac 34B3 00CB 3084 8094 22FF 308A 2657 0000|
|**Md**|4 podwójne słowa|0x0012ffac|0x0012ffac 00CB34B3 80943084 308A22FF 00002657|
|**Mq**|2 czworokątne hasła|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|
|**mu**|Znaki 2-bajtowe (Unicode)|0x0012ffac|0x0012ffac 8478 77f4 ffff ffff 0000 0000 0000 0000|

### <a name="size-specifier-for-pointers-as-arrays-in-interop-debugging-with-ccli"></a><a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> Specyfikator rozmiaru wskaźników jako tablic w debugowaniu międzyoptyków za pomocą języka C++/interfejsu wiersza polecenia

Jeśli masz wskaźnik do obiektu, który chcesz wyświetlić jako tablicę, możesz użyć liczby całkowitej, aby określić liczbę elementów tablicy.

|Specyfikator|Format|Wyrażenie|Wyświetlana wartość|
|---------------|------------|----------------|---------------------|
|n|Liczba całkowita dziesiętna|pBuffer[32]|Wyświetla `pBuffer` jako tablicę 32-elementową.|
