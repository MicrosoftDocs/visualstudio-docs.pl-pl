---
title: Wyszukiwanie przecieków pamięci za pomocą biblioteki CRT | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
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
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f66abbb72e707381b30c88f88e999f502e3c7da9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54800927"
---
# <a name="finding-memory-leaks-using-the-crt-library"></a>Wyszukiwanie przecieków pamięci za pomocą biblioteki CRT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przecieki pamięci, zdefiniowane jako niepowodzenie poprawnie npamięci, które zostały uprzednio alokowane, znajdują się wśród najbardziej subtelnych i twardych wykrywania usterek w aplikacjach języka C/C++. Niewielki przeciek pamięci mogą nie być niezauważone po raz pierwszy, ale wraz z upływem czasu, progresywnego przeciek pamięci może powodować objawy tego zakresu z których wydajność pogorszyła się uległa awarii, gdy aplikacja zostanie uruchomiona za mało pamięci. Co gorsza przeciek aplikacji, która zużywa się całą dostępną pamięć może spowodować awarię, innej aplikacji zamieszania, które aplikacja jest odpowiedzialna. W końcu nawet pozornie nieszkodliwe przecieki pamięci mogą być objawem innych problemów, które powinny zostać poprawione.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Debuger i biblioteki wykonawczej C (CRT) zapewniają środki do wykrywania i identyfikacji przecieków pamięci.  
  
## <a name="enabling-memory-leak-detection"></a>Włączanie wykrywania przecieków pamięci  
 Podstawowe narzędzia do wykrywania wycieków pamięci to debuger i biblioteki wykonawczej C (CRT) funkcje stosu debugowania.  
  
 Aby włączyć funkcje stosu debugowania, Dołącz poniższe instrukcje w programach:  
  
```  
#define _CRTDBG_MAP_ALLOC  
#include <stdlib.h>  
#include <crtdbg.h>  
```  
  
 Aby funkcje CRT działały prawidłowo `#include` instrukcji należy wykonać pokazaną tu kolejność.  
  
 Łącznie z mapy crtdbg.h `malloc` i [bezpłatne](http://msdn.microsoft.com/library/74ded9cf-1863-432e-9306-327a42080bb8) funkcje do ich wersji debugowej [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb) i `free`, którye śledzą alokację i dezalokację pamięci. To mapowanie występuje tylko w debugowanych kompilacjach, które mają `_DEBUG`. Kompilacje wydania używają zwykłej `malloc` i `free` funkcji.  
  
 `#define` Instrukcji mapuje wersję podstawową stosu CRT na odpowiednią wersję debugowania. Jeżeli pominięto `#define` instrukcji, zrzut przecieku pamięci będzie mniej dokładny.  
  
 Po włączeniu funkcji debugowania stert za pomocą tych instrukcji, można umieścić wywołanie `_CrtDumpMemoryLeaks` przed punktem wyjścia aplikacji, aby wyświetlić raport przeciek pamięci, gdy aplikacja zakończy działanie:  
  
```  
_CrtDumpMemoryLeaks();  
```  
  
 Jeśli aplikacja ma wiele wyjść, nie trzeba ręcznie umieszczać wywołania do [_CrtDumpMemoryLeaks](http://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c) w każdym punkcie wyjścia. Wywołanie `_CrtSetDbgFlag` na początku aplikacji spowoduje automatyczne wywołanie `_CrtDumpMemoryLeaks` na każdym punkcie wyjścia. Należy ustawić dwa pola bitowe pokazane tutaj:  
  
```  
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );  
```  
  
 Domyślnie `_CrtDumpMemoryLeaks` wyświetla raport przecieku pamięci, aby **debugowania** okienku **dane wyjściowe** okna. Możesz użyć `_CrtSetReportMode` Aby przekierować raport do innej lokalizacji.  
  
 Jeśli używasz biblioteki, biblioteka może zresetować dane wyjściowe do innej lokalizacji. W takiej sytuacji można ustawić położenie wyjściowe powrót do **dane wyjściowe** okna, jak pokazano poniżej:  
  
```  
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );  
```  
  
## <a name="interpreting-the-memory-leak-report"></a>Interpretowanie raport przecieku pamięci  
 Jeśli aplikacja nie definiuje `_CRTDBG_MAP_ALLOC`, [_CrtDumpMemoryLeaks](http://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c) wyświetla raport przecieku pamięci, który wygląda podobnie do tego:  
  
```  
Detected memory leaks!  
Dumping objects ->  
{18} normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 Jeśli aplikacja definiuje `_CRTDBG_MAP_ALLOC`, raport przecieku pamięci wygląda następująco:  
  
```  
Detected memory leaks!  
Dumping objects ->  
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}   
 normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 Różnica polega na tym, że drugi raport zawiera nazwę pliku i numer wiersza, gdzie najpierw zaalokowano przecieku pamięci.  
  
 Czy można zdefiniować `_CRTDBG_MAP_ALLOC` lub nie będą raport przecieku pamięci wyświetlić następujące informacje:  
  
- Numer alokacji pamięci, która jest `18` w tym przykładzie  
  
- [Typ bloku](http://msdn.microsoft.com/e2f42faf-0687-49e7-aa1f-916038354f97), czyli `normal` w tym przykładzie.  
  
- Lokalizacja pamięci szesnastkowej, czyli `0x00780E80` w tym przykładzie.  
  
- Rozmiar bloku, `64 bytes` w tym przykładzie.  
  
- Pierwsze 16 bajtów danych w bloku, w postaci szesnastkowej.  
  
  Raport przecieku pamięci określa blok pamięci jako normalny, klienta lub CRT. A *Blok normalny* to zwykła pamięć przydzielana przez Twój program. A *blok klienta* to specjalny rodzaj bloku pamięci używany przez programy MFC dla obiektów, które wymagają destruktora. MFC `new` operator tworzy Blok normalny lub blok klienta, odpowiednio do tworzonego obiektu. A *blok CRT* jest przydzielany przez bibliotekę CRT na własny użytek. Biblioteka CRT obsługuje dezalokację dla tych bloków. Dlatego jest mało prawdopodobne, zobaczysz je w raporcie o przeciekach pamięci, chyba że występuje jakiś poważny problem, na przykład biblioteka CRT jest uszkodzona.  
  
  Istnieją dwa typy bloków pamięci, które nigdy nie są wyświetlane w raportach o przeciekach pamięci. A *wolny blok* pamięci, która została zwolniona. Oznacza to, że nie jest to przeciek, zgodnie z definicją. *Ignoruj blok* jest pamięcią, która jawnie oznaczone jako celu wykluczenia go ze raport przecieku pamięci.  
  
  Techniki te działają w przypadku pamięci przydzielonej przy użyciu standardowych CRT `malloc` funkcji. Jeśli Twój program przydziela pamięć przy użyciu języka C++ `new` operatora, jednak użytkownik może być widoczna tylko plik i numer wiersza gdzie wdrożenia globalnego `operator new` wywołania `_malloc_dbg` w raporcie o przecieku pamięci. To zachowanie nie jest bardzo przydatny, można zmienić go zgłosić wiersz, który wprowadzone alokacji za pomocą makra, który wygląda w następujący sposób: 
 
```cpp  
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```  
  
Teraz możesz zastąpić `new` operator przy użyciu `DBG_NEW` makra w kodzie. W kompilacjach do debugowania, to używane jest przeciążenie globalnego `operator new` , wymaga dodatkowych parametrów, aby uzyskać typ bloku, pliku i numer wiersza. To przeciążenie `new` wywołania `_malloc_dbg` do rejestrowania dodatkowych informacji. Kiedy używasz `DBG_NEW`, przeciek pamięci, raporty, Pokaż nazwę pliku i numer wiersza, gdzie zostały przydzielone obiekty ujawnione. W kompilacjach do sprzedaży detalicznej używa domyślnie `new`. (Nie zaleca się tworzenie makro preprocesora, o nazwie `new`, i wszelkich innych słów kluczowych języka.) Oto przykład techniki:  
  
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
  
Po uruchomieniu tego kodu w debugerze programu Visual Studio, wywołanie `_CrtDumpMemoryLeaks` generuje raport w **dane wyjściowe** okno, które wygląda podobnie do następującej:  
  
```Output  
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD 
Object dump complete.
```  
  
Oznacza to, że ujawnione przydział był przeznaczony w wierszu 20 debug_new.cpp.  
  
## <a name="setting-breakpoints-on-a-memory-allocation-number"></a>Ustawianie punktów przerwania dla numeru alokacji pamięci  
 Numer alokacji pamięci informuje, kiedy przydzielono blok pamięci z przeciekiem. Blok z liczbą alokacji pamięci 18, jest na przykład 18 blokiem pamięci przydzielonej podczas uruchomienia aplikacji. Raport CRT zlicza wszystkie alokacje bloków pamięci podczas uruchamiania. Obejmuje to alokacje przez bibliotekę CRT i inne biblioteki, takie jak MFC. Dlatego blok o numerze alokacji pamięci 18 może nie być 18 blok pamięci alokowanym przez kod. Zazwyczaj nie będzie.  
  
 Liczba alokacji umożliwia ustawianie punktu przerwania alokacji pamięci.  
  
#### <a name="to-set-a-memory-allocation-breakpoint-using-the-watch-window"></a>Aby ustawić punkt przerwania alokacji pamięci za pomocą okna czujki  
  
1. Ustaw punkt przerwania w pobliżu początku aplikacji, a następnie uruchom aplikację.  
  
2. Gdy aplikacja przerywa w punkcie przerwania, **Obejrzyj** okna.  
  
3. W **Obejrzyj** okna, typ `_crtBreakAlloc` w **nazwa** kolumny.  
  
    Jeśli używasz wielowątkowej wersji DLL biblioteki CRT (opcja/MD), Dodaj operator kontekstu: `{,,ucrtbased.dll}_crtBreakAlloc`  
  
4. Naciśnij klawisz **zwracają**.  
  
    Debuger ocenia wywołanie i umieszcza wynik w **wartość** kolumny. Ta wartość będzie równa – 1, jeśli nie ustawiono żadnych punktów przerwania w alokacjach pamięci.  
  
5. W **wartość** kolumny, Zamień wartość widoczną z liczbą alokacji alokacji pamięci, w którym chcesz przerwać.  
  
   Po ustawieniu punktu przerwania na liczbę alokacji pamięci można kontynuować debugowanie. Uważaj uruchomić program w tych samych warunkach jako poprzedniego uruchomienia, tak, aby nie zmienia kolejność alokacji pamięci. Kiedy program przerywa w określonej alokacji pamięci, możesz użyć **stos wywołań** okna i innych oknach debugera, aby określić warunki, w jakich pamięć została alokowana. Następnie można kontynuować wykonywanie, aby obserwować, co się dzieje z obiektem i ustalić, dlaczego go jest nie jest poprawnie dezalokowany.  
  
   Ustawianie punktu przerwania danych obiektu może być również przydatne. Aby uzyskać więcej informacji, zobacz [przy użyciu punktów przerwania](../debugger/using-breakpoints.md).  
  
   Można również ustawić punkty przerwania alokacji pamięci, w kodzie. Istnieją dwa sposoby wykonania tej czynności:  
  
```  
_crtBreakAlloc = 18;  
```  
  
 lub:  
  
```  
_CrtSetBreakAlloc(18);  
```  
  
## <a name="comparing-memory-states"></a>Porówywanie stanów pamięci  
 Inna technika lokalizowania przecieków pamięci zakłada robienie migawek stanu pamięci aplikacji w najważniejszych punktach. Aby zrobić migawkę stanu pamięci w danym punkcie w aplikacji, należy utworzyć **_CrtMemState** struktury i przekazać ją do `_CrtMemCheckpoint` funkcji. Ta funkcja wypełnia strukturę migawką bieżącego stanu pamięci:  
  
```  
_CrtMemState s1;  
_CrtMemCheckpoint( &s1 );  
  
```  
  
 `_CrtMemCheckpoint` wypełnia strukturę migawką bieżącego stanu pamięci.  
  
 Aby wyprowadzić zawartość **_CrtMemState** struktury, należy przekazać strukturę do `_ CrtMemDumpStatistics` funkcji:  
  
```  
_CrtMemDumpStatistics( &s1 );  
  
```  
  
 `_ CrtMemDumpStatistics` Wyświetla zrzut stanu pamięci, który wygląda w następujący sposób:  
  
```  
0 bytes in 0 Free Blocks.  
0 bytes in 0 Normal Blocks.  
3071 bytes in 16 CRT Blocks.  
0 bytes in 0 Ignore Blocks.  
0 bytes in 0 Client Blocks.  
Largest number used: 3071 bytes.  
Total allocations: 3764 bytes.  
  
```  
  
 Aby ustalić, czy wystąpił przeciek pamięci, w sekcji kodu, należy można wykonać migawki stanu pamięci przed i po sekcji, a następnie użyć `_ CrtMemDifference` do porównywania dwóch stanów:  
  
```  
_CrtMemCheckpoint( &s1 );  
// memory allocations take place here  
_CrtMemCheckpoint( &s2 );  
  
if ( _CrtMemDifference( &s3, &s1, &s2) )  
   _CrtMemDumpStatistics( &s3 );  
```  
  
 `_CrtMemDifference` porównuje stany pamięci `s1` i `s2` i zwraca wynik w (`s3`) czyli różnicę `s1` i `s2`.  
  
 Jedna z technik do znajdowania przecieki pamięci rozpoczyna się od wprowadzania `_CrtMemCheckpoint` wywołania na początku i na końcu aplikacji, a następnie użyć `_CrtMemDifference` porównanie wyników. Jeśli `_CrtMemDifference` pokazuje przeciek pamięci, można dodać więcej `_CrtMemCheckpoint` wywołań, aby dzielić program za pomocą wyszukiwania binarnego do momentu wykrycia źródła przecieku.  
  
## <a name="false-positives"></a>Wyniki fałszywie dodatnie  
 W niektórych przypadkach `_CrtDumpMemoryLeaks` może dać fałszywe wskazania przecieków pamięci. Taka sytuacja może wystąpić, jeśli używasz biblioteki, która oznacza wewnętrzne alokacje jako bloki _normal_block zamiast `_CRT_BLOCK`s lub `_CLIENT_BLOCK`s. W takim przypadku `_CrtDumpMemoryLeaks` jest w stanie odróżnić alokacje użytkownika i alokacje biblioteki wewnętrznej. Jeśli globalne destruktory dla alokacji biblioteki działają po punkcie, w gdzie jest wywoływana `_CrtDumpMemoryLeaks`, każda wewnętrzna alokacja biblioteki jest raportowana jako przeciek pamięci. Starsze wersje biblioteki STL, starszych niż program Visual Studio .NET, spowodowały `_CrtDumpMemoryLeaks` do zgłaszania takich fałszywych alarmów, ale został rozwiązany w ostatnich wersjach.  
  
## <a name="see-also"></a>Zobacz też  
 [Szczegóły dotyczące sterty debugowania CRT](../debugger/crt-debug-heap-details.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
