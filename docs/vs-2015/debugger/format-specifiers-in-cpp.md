---
title: Specyfikatory w języku C++ formatu | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440073"
---
# <a name="format-specifiers-in-c"></a>Specyfikatory formatu w C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można zmienić format wyświetlania wartości w **Obejrzyj** okna przy użyciu specyfikatorów formatu.  
  
 Możesz również użyć specyfikatorów formatu w **bezpośrednie** oknie **polecenia** okna, a nawet w oknach źródłowych. Jeśli zatrzymasz się na wyrażeniu w tych oknach, wynik pojawi się w poradzie dotyczącej danych. Wyświetl etykietki danych odzwierciedla specyfikator formatu.  
  
> [!NOTE]
> Debuger macierzysty Visual Studio zmieniony na nowym aparacie debugowania. W ramach tej zmiany dodano pewnych nowych specyfikatorów formatu i niektórych starych zostały usunięte. Starszy debuger jest nadal używana podczas wykonywania interop (mieszane macierzyste i zarządzane) debugowanie za pomocą C++sposób niezamierzony. W poniższych sekcjach, w tym temacie opisano specyfikatory formatu dla każdego silnika debugowania.  
> 
> - [Specyfikatory formatu](#BKMK_Visual_Studio_2012_format_specifiers) opisuje specyfikatory formatu w nowym aparacie debugowania.  
>   - [Specyfikatory formatu dla debugowania międzyoperacyjnego przy użyciu C++sposób niezamierzony](#BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue) opisuje specyfikatory formatu w starszym silniku debugowania.  
  
## <a name="using-format-specifiers"></a>Przy użyciu specyfikatorów formatu  
 Jeśli masz następujący kod:  
  
```cpp  
int main() {  
    int my_var1 = 0x0065;  
    int my_var2 = 0x0066;  
    int my_var3 = 0x0067;  
}  
```  
  
 Dodaj `my_var1` zmienną **Obejrzyj** okna (podczas debugowania, **debugowanie / Windows / Obejrzyj / Obejrzyj 1**) i ustaw wyświetlania w postaci szesnastkowej (w **Obejrzyj** oknie Kliknij prawym przyciskiem myszy zmienną, a następnie wybierz pozycję **wyświetlanie szesnastkowe**). Teraz okno czujki pokazuje, że zawiera on wartości 0x0065. Aby zobaczyć tę wartość wyrażoną jako znak, nie liczbą całkowitą, w kolumnie Nazwa po nazwie zmiennej, Dodaj specyfikator formatu znaków **, c**. **Wartość** pojawi się kolumna z **101 "e"**.  
  
 ![WatchFormatCPlus1](../debugger/media/watchformatcplus1.png "WatchFormatCPlus1")  
  
## <a name="BKMK_Visual_Studio_2012_format_specifiers"></a> Specyfikatory formatu  
 W poniższych tabelach przedstawiono specyfikatory formatu, w której można w programie Visual Studio. Specyfikatory wytłuszczonym drukiem nie są obsługiwane w przypadku debugowania międzyoperacyjnego przy użyciu C++sposób niezamierzony.  
  
|Specyfikator|Format|Oryginalnej wartości czujki|Wartości wyświetlanej|  
|---------------|------------|--------------------------|---------------------|  
|d|Liczba całkowita dziesiętna|0x00000066|102|  
|o|Nieoznaczona ósemkowa liczba całkowita|0x00000066|000000000146|  
|x<br /><br /> **h**|Szesnastkowa liczba całkowita|102|0xcccccccc|  
|X<br /><br /> **H**|Szesnastkowa liczba całkowita|102|0xCCCCCCCC|  
|c|pojedynczy znak|0x0065, c|101 "e"|  
|s|Const char * ciągu|\<Lokalizacja > "hello world"|"hello world"|  
|**sb**|Const char * ciągu|\<Lokalizacja > "hello world"|Cześć ludzie|  
|s8|Const char * ciągu|\<Lokalizacja > "hello world"|"hello world"|  
|**s8b**|Const char * ciągu|\<Lokalizacja > "hello world"|"hello world"|  
|su|Const wchar_t * const<br /><br /> char16_t\* ciągu|\<Lokalizacja > L "hello world"|L "hello world"<br /><br /> u "hello world"|  
|Sub|Const wchar_t * const<br /><br /> char16_t\* ciągu|\<Lokalizacja > L "hello world"|Cześć ludzie|  
|bstr|Ciąg BSTR|\<Lokalizacja > L "hello world"|L "hello world"|  
|**s32**|Ciąg UTF-32|\<Lokalizacja > U "hello world"|U "hello world"|  
|**s32b**|Ciąg UTF-32 (bez cudzysłowu)|\<Lokalizacja > U "hello world"|Cześć ludzie|  
|**en**|enum|SATURDAY(6)|Sobota|  
|**hv**|Typ wskaźnika — wskazuje, że wartość wskaźnika, poddawanego inspekcji jest wynikiem alokacji sterty w tablicy, na przykład `new int[3]`.|\<Lokalizacja > {\<pierwszy element członkowski >}|\<Lokalizacja > {\<pierwszy element członkowski >, \<drugi element członkowski >,...}|  
|**Nazwa**|Pomija adres pamięci wskaźnika do obiektu.|\<Lokalizacja >, {elementu członkowskiego = wartość...}|{elementu członkowskiego = wartość...}|  
|**ND**|Wyświetla tylko klasy bazowej informacje, ignorując klasy pochodne|`(Shape*) square` zawiera klasy podstawowej i pochodnej informacji o klasie|Wyświetla tylko podstawowy informacji o klasie|  
|godz.|Kod błędu HRESULT lub Win32. (Narzędzie debugger teraz dekoduje HRESULTs automatycznie, więc specyfikator ten nie jest wymagane w tych przypadkach.|S_OK|S_OK|  
|wc|Flaga klasy okna|0x0010|WC_DEFAULTCHAR|  
|wm|Numery komunikatu Windows|16|WM_CLOSE|  
|!|format RAW, ignorowanie wszelkich dostosowań widoków typu danych|\<dostosowane reprezentacji >|4|  
  
> [!NOTE]
> Gdy **hv** specyfikatora formatu, debuger próbuje określić długość buforu i wyświetlić odpowiednią liczbę elementów. Ponieważ nie zawsze jest możliwe dla debugera znaleźć rozmiar buforu dokładnie tablicy, należy użyć Określ rozmiar specyfikatorów `(pBuffer,[bufferSize])` zawsze, gdy jest to możliwe. **Hv** specyfikator formatu jest przeznaczone dla scenariuszy, których rozmiar buforu nie jest jeszcze dostępna  
  
### <a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> Określ rozmiar specyfikatorów dla wskaźników jako tablice  
 Jeśli masz wskaźnik do obiektu, który chcesz wyświetlić jako tablicę, można użyć liczbą całkowitą lub wyrażenie, aby określić liczbę elementów tablicy:  
  
|Specyfikator|Format|Oryginalny wartośćN wyrażenie kontrolne|Wartości wyświetlanej|  
|---------------|------------|---------------------------|---------------------|  
|n|Dziesiętna lub **szesnastkowe** liczba całkowita|pBuffer, [32]<br /><br /> pBuffer,**[0x20]**|Wyświetla `pBuffer` jako tablica 32 elementów.|  
|**[exp]**|Prawidłowe wyrażenie C++, którego wynikiem jest liczbą całkowitą.|pBuffer,[bufferSize]|Wyświetla pBuffer jako tablicę `bufferSize` elementów.|  
|**expand(n)**|Prawidłowe wyrażenie C++, którego wynikiem jest liczbą całkowitą|pBuffer, expand(2)|Wyświetla trzeci element  `pBuffer`|  
  
## <a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> Specyfikatory formatu dla debugowania międzyoperacyjnego przy użyciu C++sposób niezamierzony  
 Specyfikatory **bold** są obsługiwane tylko w przypadku debugowania natywnego i C++sposób niezamierzony kodu.  
  
|Specyfikator|Format|Oryginalnej wartości czujki|Wartości wyświetlanej|  
|---------------|------------|--------------------------|---------------------|  
|**d, i**|oznaczona dziesiętna liczba całkowita|0xF000F065|-268373915|  
|**u**|Nieoznaczona dziesiętna liczba całkowita|0x0065|101|  
|o|Nieoznaczona ósemkowa liczba całkowita|0xF065|0170145|  
|x,X|Szesnastkowa liczba całkowita|61541|0x0000f065|  
|**g, h**|długi lub krótki prefiks dla: d, i, u, o, x X|00406042|0x0c22|  
|**f**|oznaczona liczba zmiennoprzecinkowa|(3./2.), f|1.500000|  
|**e**|podpisana Notacja naukowa|(3.0/2.0)|1.500000e + 000|  
|**g**|podpisana, liczba zmiennoprzecinkowa lub oznaczona Notacja naukowa, nich okaże się krótsza|(3.0/2.0)|1,5|  
|c|pojedynczy znak|\<Lokalizacja >|101 "e"|  
|s|Const char *|\<Lokalizacja >|"hello world"|  
|su|Const wchar_t *<br /><br /> Const char16_t\*|\<Lokalizacja >|L "hello world"|  
|Sub|Const wchar_t *<br /><br /> Const char16_t\*|\<Lokalizacja >|Cześć ludzie|  
|s8|Const char *|\<Lokalizacja >|"hello world"|  
|godz.|Kod błędu HRESULT lub Win32. (Narzędzie debugger teraz dekoduje HRESULTs automatycznie, więc specyfikator ten nie jest wymagane w tych przypadkach.|S_OK|S_OK|  
|wc|Flaga klasy okna.|0x00000040,|WC_DEFAULTCHAR|  
|wm|Numery komunikatu Windows|0x0010|WM_CLOSE|  
|!|format RAW, ignorowanie wszelkich dostosowań widoków typu danych|\<dostosowane reprezentacji >|4|  
  
### <a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> Specyfikatory lokalizacjami pamięci debugowania międzyoperacyjnego przy użyciu formatu C++sposób niezamierzony  
 Poniższa tabela zawiera symbole formatowania używane dla lokalizacji pamięci. Można użyć specyfikatora lokalizacji pamięci z dowolną wartością lub wyrażeniem, które ewoluuje do lokalizacji.  
  
|Symbol|Format|Oryginalnej wartości czujki|Wartości wyświetlanej|  
|------------|------------|--------------------------|---------------------|  
|**ma**|64 znaki ASCII|0x0012ffac|0x0012ffac .4...0...".0W&.......1W&.0.:W..1...."..1.JO&.1.2.."..1...0y....1|  
|**m**|16 bajtów w formacie szesnastkowym, a następnie 16 znaków ASCII|0x0012ffac|0X0012FFAC B3 34 FF CB 00 84 30 94 80 22 8A 30 57 26 00 00. 4... 0... ". 0W &...|  
|**mb**|16 bajtów w formacie szesnastkowym, a następnie 16 znaków ASCII|0x0012ffac|0X0012FFAC B3 34 FF CB 00 84 30 94 80 22 8A 30 57 26 00 00. 4... 0... ". 0W &...|  
|**mw**|8 słów|0x0012ffac|0x0012ffac 34B3 00CB 3084 8094 22FF 308A 2657 0000|  
|**md**|4 wyrazy w liczbie mnogiej|0x0012ffac|0x0012ffac 00CB34B3 80943084 308A22FF 00002657|  
|**mq**|2 wyrazy w liczbie mnogiej|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|  
|**mu**|znaki 2-bajtowe (Unicode)|0x0012ffac|0x0012ffac 8478 77f4 ffff ffff 0000 0000 0000 0000|  
  
### <a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> Określ rozmiar specyfikatorów dla wskaźników jako tablice w debugowaniu międzyoperacyjnym z C++/CLIt  
 Jeśli masz wskaźnik do obiektu, który chcesz wyświetlić jako tablicę, można użyć liczby całkowitej, aby określić liczbę elementów tablicy:  
  
|Specyfikator|Format|Wyrażenie|Wartości wyświetlanej|  
|---------------|------------|----------------|---------------------|  
|n|Liczba całkowita dziesiętna|pBuffer [32]|Wyświetla `pBuffer` jako tablica 32 elementów.|
