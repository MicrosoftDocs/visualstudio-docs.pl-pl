---
title: Znajdź, przecieki pamięci za pomocą biblioteki CRT | Dokumentacja firmy Microsoft
ms.date: 10/04/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- breakpoints, on memory allocation
- _CrtMemState
- _CrtMemCheckpoint
- memory leaks
- _CrtMemDifference
- memory leaks, detecting and isolating
- _CrtDumpMemoryLeaks
- _CrtSetBreakAlloc
- _crtBreakAlloc
- _CrtSetReportMode
- memory, debugging
- _CrtMemDumpStatistics
- debugging memory leaks
- _CRTDBG_MAP_ALLOC
- _CrtSetDbgFlag
ms.assetid: cf6dc7a6-cd12-4283-b1b6-ea53915f7ed1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e3045f9e420ad8d70b9f02172c18f46e4e412c37
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54946320"
---
# <a name="find-memory-leaks-with-the-crt-library"></a>Znajdowanie przecieków pamięci za pomocą biblioteki CRT

Przecieki pamięci znajdują się wśród najbardziej subtelnych i twardych wykrywania usterek w aplikacjach języka C/C++. W wyniku awarii można poprawnie cofnąć alokacji pamięci, która była przydzielona wcześniej przecieki pamięci. Niewielki przeciek pamięci, mogą nie być niezauważone na początku, ale wraz z upływem czasu, może powodować objawy, począwszy od niskiej wydajności do uległa awarii, gdy aplikacji skończy się pamięć. Przeciek aplikacji, która używa się całą dostępną pamięć może powodować awarię inne aplikacje, tworzenie nieporozumienie co do tego aplikacji, która jest odpowiedzialna. Nawet nieszkodliwe przecieki pamięci mogą wskazywać na inne problemy, które powinny zostać poprawione.  

 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Debuger i biblioteki wykonawczej języka C (CRT) mogą pomóc i wykrywanie przecieków pamięci.  

## <a name="enable-memory-leak-detection"></a>Włączanie wykrywania przecieków pamięci  

Podstawowe narzędzia do wykrywania wycieków pamięci to Debuger języka C/C++ i biblioteki wykonawcze języka C (CRT) funkcje stosu debugowania.  

Aby włączyć wszystkie funkcje stosu debugowania, Dołącz poniższe instrukcje w programach języka C++ w następującej kolejności:  

```cpp
#define _CRTDBG_MAP_ALLOC  
#include <stdlib.h>  
#include <crtdbg.h>  
```  

`#define` Instrukcji mapuje wersję podstawową stosu CRT na odpowiednią wersję debugowania. Jeśli pozostawisz `#define` instrukcji, zrzut przecieku pamięci będzie [mniej szczegółowe](#interpret-the-memory-leak-report).  

W tym *crtdbg.h* mapuje `malloc` i `free` funkcje do ich wersji debugowej [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg) i [_free_dbg —](/cpp/c-runtime-library/reference/free-dbg), którye śledzą pamięci alokacji i dezalokacji. To mapowanie występuje tylko w debugowanych kompilacjach, które mają `_DEBUG`. Kompilacje wydania używają zwykłej `malloc` i `free` funkcji.  

Po włączeniu funkcji debugowania stert za pomocą poprzednich instrukcji, Umieść wywołanie [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) przed punktem wyjścia aplikacji, aby wyświetlić raport przeciek pamięci, gdy kończy działanie aplikacji.  

```cpp
_CrtDumpMemoryLeaks();  
```  

Jeśli aplikacja ma wiele wyjść, nie trzeba ręcznie umieszczać `_CrtDumpMemoryLeaks` w każdym punkcie wyjścia. Aby spowodować, że automatyczne wywołanie `_CrtDumpMemoryLeaks` w każdym punkcie wyjścia, Umieść wywołanie `_CrtSetDbgFlag` na początku aplikacji za pomocą pola bitowe pokazane poniżej:

```cpp
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );  
```  

Domyślnie `_CrtDumpMemoryLeaks` wyświetla raport przecieku pamięci, aby **debugowania** okienku **dane wyjściowe** okna. Jeśli używasz biblioteki, biblioteka może zresetować dane wyjściowe do innej lokalizacji. 

Możesz użyć `_CrtSetReportMode` przekierować raport do innej lokalizacji lub z powrotem do **dane wyjściowe** okna, jak pokazano poniżej:  

```cpp
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );  
```  

## <a name="interpret-the-memory-leak-report"></a>Interpretowanie raport przecieku pamięci  

Jeśli w Twojej aplikacji nie zdefiniowano `_CRTDBG_MAP_ALLOC`, [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) wyświetla raport przecieku pamięci wygląda następująco:  

```cmd
Detected memory leaks!  
Dumping objects ->  
{18} normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  

Jeśli aplikacja definiuje `_CRTDBG_MAP_ALLOC`, raport przecieku pamięci wygląda następująco:  

```cmd
Detected memory leaks!  
Dumping objects ->  
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}   
normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  

Drugi raport zawiera nazwę pliku i numer wiersza, gdzie najpierw zaalokowano przecieku pamięci.  

Określa, czy należy zdefiniować `_CRTDBG_MAP_ALLOC`, wyświetla raport przecieku pamięci:  

- Numer alokacji pamięci, która jest `18` w przykładzie  
- Typ bloku `normal` w przykładzie.  
- Lokalizacja pamięci szesnastkowej `0x00780E80` w przykładzie.  
- Rozmiar bloku, `64 bytes` w przykładzie.  
- Pierwsze 16 bajtów danych w bloku, w postaci szesnastkowej.  

Typów bloków pamięci są *normalne*, *klienta*, lub *CRT*. A *Blok normalny* to zwykła pamięć przydzielana przez Twój program. A *blok klienta* to specjalny rodzaj bloku pamięci używany przez programy MFC dla obiektów, które wymagają destruktora. MFC `new` operator tworzy Blok normalny lub blok klienta, odpowiednio do tworzonego obiektu. 

A *blok CRT* jest przydzielany przez bibliotekę CRT na własny użytek. Biblioteka CRT obsługuje dezalokację dla tych bloków, dzięki czemu bloki CRT nie będzie wyświetlane w raporcie o przecieku pamięci, chyba że występują poważne problemy za pomocą biblioteki CRT.  

Istnieją dwa typy bloków pamięci, które nigdy nie są wyświetlane w raportach o przeciekach pamięci. A *wolny blok* pamięci, która została zwolniona, więc nie jest przeciek zgodnie z definicją. *Ignoruj blok* pamięci, które zostały jawnie oznaczone do wykluczenia z raport przecieku pamięci.  

Powyższych technik identyfikacji przecieków pamięci do pamięci przydzielonej za pomocą standardowych CRT `malloc` funkcji. Jeśli Twój program przydziela pamięć przy użyciu języka C++ `new` operatora, jednak użytkownik może być widoczna tylko nazwę pliku i numer wiersza gdzie `operator new` wywołania `_malloc_dbg` w raporcie o przecieku pamięci. Aby utworzyć bardziej przydatny raport przeciek pamięci, można napisać makro podobne do następującego raportu wiersza, który zgłosił przydział: 

```cpp  
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```  

Teraz możesz zastąpić `new` operator przy użyciu `DBG_NEW` makra w kodzie. W kompilacjach do debugowania `DBG_NEW` używane jest przeciążenie globalnych `operator new` , wymaga dodatkowych parametrów, aby uzyskać typ bloku, pliku i numer wiersza. Przeciążenia `new` wywołania `_malloc_dbg` do rejestrowania dodatkowych informacji. Raporty przeciek pamięci pokazują nazwę pliku i numer wiersza, w którym ujawnione obiektów została przydzielona. Wersji kompilacji Użyj nadal domyślnie `new`. Oto przykład techniki:  

```cpp  
// debug_new.cpp
// compile by using: cl /EHsc /W4 /D_DEBUG /MDd debug_new.cpp
#define _CRTDBG_MAP_ALLOC
#include <cstdlib>
#include <crtdbg.h>

#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif

struct Pod {
    int x;
};

void main() {
    Pod* pPod = DBG_NEW Pod;
    pPod = DBG_NEW Pod; // Oops, leaked the original pPod!
    delete pPod;

    _CrtDumpMemoryLeaks();
}
```  

Po uruchomieniu tego kodu w programie Visual Studio debugera, wywołanie `_CrtDumpMemoryLeaks` generuje raport w **dane wyjściowe** okna, która wygląda podobnie do:  

```Output  
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD 
Object dump complete.
```  

To danych wyjściowych raportów, że ujawnione przydział był przeznaczony w wierszu 20 *debug_new.cpp*.  

>[!NOTE]
>Nie zaleca się tworzenie makro preprocesora, o nazwie `new`, i wszelkich innych słów kluczowych języka. 

## <a name="set-breakpoints-on-a-memory-allocation-number"></a>Ustawianie punktów przerwania na liczbę alokacji pamięci  

Numer alokacji pamięci informuje, kiedy przydzielono blok pamięci z przeciekiem. Blok z liczbą alokacji pamięci 18, jest na przykład 18 blokiem pamięci przydzielonej podczas uruchomienia aplikacji. Raport CRT zlicza wszystkie alokacje bloków pamięci podczas uruchamiania, w tym alokacje przez bibliotekę CRT i inne biblioteki, takie jak MFC. W związku z tym pamięć alokacji numeru bloku 18 prawdopodobnie nie jest 18 blok pamięci alokowanym przez kod. 

Liczba alokacji umożliwia ustawianie punktu przerwania alokacji pamięci.  

**Aby ustawić punkt przerwania alokacji pamięci za pomocą okna czujki:**  

1. Ustaw punkt przerwania w pobliżu początku aplikacji, a następnie rozpocząć debugowanie.  
   
1. Gdy aplikacja jest wstrzymana w punkcie przerwania, otwórz **Obejrzyj** okna, wybierając **debugowania** > **Windows** > **Czujka 1** (lub **Obejrzyj 2**, **Obejrzyj 3**, lub **Obejrzyj 4**).  
   
1. W **Obejrzyj** okna, typ `_crtBreakAlloc` w **nazwa** kolumny.  
   
   Jeśli używasz wielowątkowej wersji DLL biblioteki CRT (opcja/MD), Dodaj operator kontekstu: `{,,ucrtbased.dll}_crtBreakAlloc`  
   
1. Naciśnij klawisz **wprowadź**.  
   
   Debuger ocenia wywołanie i umieszcza wynik w **wartość** kolumny. Ta wartość będzie **-1** Jeśli nie ustawiono żadnych punktów przerwania w alokacjach pamięci.  
   
1. W **wartość** kolumny, zastąp wartość symbolu z liczbą alokacji alokacji pamięci, której chcesz debuger przerywa.  

Po ustawieniu punktu przerwania na liczbę alokacji pamięci można kontynuować debugowanie. Upewnij się, że są uruchamiane w tych samych warunkach, więc nie zmienia numer alokacji pamięci. Kiedy program przerywa w określonej alokacji pamięci, należy użyć **stos wywołań** okna i innych oknach debugera, aby określić warunki, w jakich pamięć została alokowana. Następnie można kontynuować wykonywanie, aby obserwować, co się dzieje z obiektem i ustalić, dlaczego nie jest poprawnie dezalokowany.  

Ustawianie punktu przerwania danych obiektu może być również przydatne. Aby uzyskać więcej informacji, zobacz [używanie punktów przerwania](../debugger/using-breakpoints.md).  

Można również ustawić punkty przerwania alokacji pamięci, w kodzie. Możesz ustawić:  

```cpp
_crtBreakAlloc = 18;  
```  

 lub:  

```cpp
_CrtSetBreakAlloc(18);  
```  

## <a name="compare-memory-states"></a>Porównaj stany pamięci  
 Inna technika lokalizowania przecieków pamięci zakłada robienie migawek stanu pamięci aplikacji w najważniejszych punktach. Aby zrobić migawkę stanu pamięci w danym punkcie w aplikacji, należy utworzyć `_CrtMemState` struktury i przekazać ją do `_CrtMemCheckpoint` funkcji. 

```cpp
_CrtMemState s1;  
_CrtMemCheckpoint( &s1 );  
```  

`_CrtMemCheckpoint` Funkcja wypełnia strukturę migawką bieżącego stanu pamięci.  

Aby wyprowadzić zawartość `_CrtMemState` struktury, należy przekazać strukturę do `_ CrtMemDumpStatistics` funkcji:  

```cpp
_CrtMemDumpStatistics( &s1 );  
```  

`_ CrtMemDumpStatistics` Wyświetla zrzut stanu pamięci, który wygląda następująco:  

```cmd
0 bytes in 0 Free Blocks.  
0 bytes in 0 Normal Blocks.  
3071 bytes in 16 CRT Blocks.  
0 bytes in 0 Ignore Blocks.  
0 bytes in 0 Client Blocks.  
Largest number used: 3071 bytes.  
Total allocations: 3764 bytes.  
```  

Aby ustalić, czy wystąpił przeciek pamięci, w sekcji kodu, należy można wykonać migawki stanu pamięci przed i po sekcji, a następnie użyć `_ CrtMemDifference` do porównywania dwóch stanów:  

```cpp
_CrtMemCheckpoint( &s1 );  
// memory allocations take place here  
_CrtMemCheckpoint( &s2 );  

if ( _CrtMemDifference( &s3, &s1, &s2) )  
   _CrtMemDumpStatistics( &s3 );  
```  

`_CrtMemDifference` porównuje stany pamięci `s1` i `s2` i zwraca wynik w (`s3`) oznacza to różnica między `s1` i `s2`.  

Jedna z technik do znajdowania przecieki pamięci rozpoczyna się od wprowadzania `_CrtMemCheckpoint` wywołania na początku i na końcu aplikacji, a następnie użyć `_CrtMemDifference` porównanie wyników. Jeśli `_CrtMemDifference` pokazuje przeciek pamięci, można dodać więcej `_CrtMemCheckpoint` wywołań, aby dzielić program za pomocą wyszukiwania binarnego do momentu zostało izolowany źródła przecieku.  

## <a name="false-positives"></a>Wyniki fałszywie dodatnie  
 `_CrtDumpMemoryLeaks` może dać fałszywe wskazania przecieków pamięci, jeśli biblioteka oznacza wewnętrzne alokacje jako bloki normalne zamiast bloki CRT lub bloki klienta. W takim przypadku `_CrtDumpMemoryLeaks` jest w stanie odróżnić alokacje użytkownika i alokacje biblioteki wewnętrznej. Jeśli globalne destruktory dla alokacji biblioteki działają po punkcie, w gdzie jest wywoływana `_CrtDumpMemoryLeaks`, każda wewnętrzna alokacja biblioteki jest raportowana jako przeciek pamięci. Wersje starsze niż program Visual Studio .NET może spowodować, że standardowej biblioteki szablonów `_CrtDumpMemoryLeaks` do zgłaszania takich fałszywych alarmów.  

## <a name="see-also"></a>Zobacz także  
 [Szczegóły dotyczące sterty debugowania CRT](../debugger/crt-debug-heap-details.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
