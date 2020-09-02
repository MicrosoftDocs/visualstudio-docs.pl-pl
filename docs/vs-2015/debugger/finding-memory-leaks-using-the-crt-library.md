---
title: Znajdowanie przecieków pamięci za pomocą biblioteki CRT | Microsoft Docs
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
ms.openlocfilehash: 831cae8d83bc26e05b80d6948a3168a6e6a387c4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682423"
---
# <a name="finding-memory-leaks-using-the-crt-library"></a>Wyszukiwanie przecieków pamięci za pomocą biblioteki CRT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przecieki pamięci, zdefiniowane jako niepowodzenie poprawnego przydziału pamięci, która została wcześniej przydzielona, są między najsłabiej i trudno wykrywać błędy w aplikacjach C/C++. Niewielki przeciek pamięci może nie być zauważalny w pierwszej kolejności, ale w miarę upływu czasu przeciek pamięci może powodować występowanie objawów, które przekroczą spadek wydajności, gdy w aplikacji wystąpiła awaria pamięci. Gorsza, przeciek aplikacji wykorzystującej całą dostępną pamięć może powodować awarię innej aplikacji, a nawet w przypadku, gdy aplikacja jest odpowiedzialna. Nawet pozornie nieszkodliwe przecieki pamięci mogą być objawem z innymi problemami, które należy poprawić.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Debugery i biblioteki środowiska uruchomieniowego języka C (CRT) umożliwiają wykrywanie i identyfikowanie przecieków pamięci.  
  
## <a name="enabling-memory-leak-detection"></a>Włączanie wykrywania przecieków pamięci  
 Podstawowe narzędzia do wykrywania przecieków pamięci to debuger oraz funkcje sterty debugowania bibliotek uruchomieniowych C (CRT).  
  
 Aby włączyć funkcje sterty debugowania, należy uwzględnić następujące instrukcje w programie:  
  
```  
#define _CRTDBG_MAP_ALLOC  
#include <stdlib.h>  
#include <crtdbg.h>  
```  
  
 Aby funkcje CRT działały prawidłowo, `#include` instrukcje muszą być zgodne z kolejnością pokazaną w tym miejscu.  
  
 W tym CRTDBG. h mapuje `malloc` i [bezpłatne](https://msdn.microsoft.com/library/74ded9cf-1863-432e-9306-327a42080bb8) funkcje do wersji debugowania, [_malloc_dbg](https://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb) i `free` , które śledzą alokację pamięci i cofa alokację. To mapowanie odbywa się tylko w kompilacjach debugowania, które mają `_DEBUG` . Kompilacje wydań używają zwykłych `malloc` i standardowych `free` funkcji.  
  
 `#define`Instrukcja mapuje podstawową wersję funkcji sterty CRT do odpowiedniej wersji debugowania. Jeśli pominięto `#define` instrukcję, zrzut przecieku pamięci będzie mniej szczegółowy.  
  
 Po włączeniu funkcji sterty debugowania za pomocą tych instrukcji można umieścić wywołanie `_CrtDumpMemoryLeaks` przed punktem wyjścia aplikacji, aby wyświetlić raport przecieku pamięci po zakończeniu działania aplikacji:  
  
```  
_CrtDumpMemoryLeaks();  
```  
  
 Jeśli aplikacja ma wiele wyjść, nie trzeba ręcznie umieszczać wywołania [_CrtDumpMemoryLeaks](https://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c) w każdym punkcie wyjścia. Wywołanie na `_CrtSetDbgFlag` początku aplikacji spowoduje automatyczne wywołanie do `_CrtDumpMemoryLeaks` każdego punktu wyjścia. Należy ustawić dwa pola bitowe wyświetlane poniżej:  
  
```  
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );  
```  
  
 Domyślnie program `_CrtDumpMemoryLeaks` wyprowadza raport o przecieku pamięci do okienka **debugowanie** w oknie **danych wyjściowych** . Możesz użyć, `_CrtSetReportMode` Aby przekierować raport do innej lokalizacji.  
  
 Jeśli używasz biblioteki, biblioteka może zresetować dane wyjściowe do innej lokalizacji. W takim przypadku można ustawić lokalizację wyjściową z powrotem do okna **danych wyjściowych** , jak pokazano poniżej:  
  
```  
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );  
```  
  
## <a name="interpreting-the-memory-leak-report"></a>Interpretowanie raportu przecieku pamięci  
 Jeśli aplikacja nie jest zdefiniowana `_CRTDBG_MAP_ALLOC` , [_CrtDumpMemoryLeaks](https://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c) wyświetla raport przecieku pamięci, który wygląda następująco:  
  
```  
Detected memory leaks!  
Dumping objects ->  
{18} normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 Jeśli aplikacja definiuje `_CRTDBG_MAP_ALLOC` , raport o przecieku pamięci wygląda następująco:  
  
```  
Detected memory leaks!  
Dumping objects ->  
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}   
 normal block at 0x00780E80, 64 bytes long.  
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD  
Object dump complete.  
```  
  
 Różnica polega na tym, że drugi raport przedstawia nazwę pliku i numer wiersza, w którym jest najpierw przydzielono przeciek pamięci.  
  
 Niezależnie `_CRTDBG_MAP_ALLOC` od tego, czy definiujesz, czy nie, raport przecieku pamięci będzie wyświetlał następujące informacje:  
  
- Numer alokacji pamięci, który jest `18` w tym przykładzie  
  
- [Typ bloku](https://msdn.microsoft.com/e2f42faf-0687-49e7-aa1f-916038354f97), który jest `normal` w tym przykładzie.  
  
- Lokalizacja pamięci szesnastkowej, która jest `0x00780E80` w tym przykładzie.  
  
- Rozmiar bloku, `64 bytes` w tym przykładzie.  
  
- Pierwsze 16 bajtów danych w bloku w postaci szesnastkowej.  
  
  Raport przecieku pamięci identyfikuje blok pamięci jako normalny, klient lub CRT. *Zwykły blok* to zwykłe pamięci przydzielone przez program. *Blok klienta* jest specjalnym typem bloku pamięci używanym przez programy MFC dla obiektów, które wymagają destruktora. Operator MFC `new` tworzy blok normalny lub blok klienta, zgodnie z potrzebami dla tworzonego obiektu. *Blok CRT* jest przypisywany przez bibliotekę CRT do własnego użytku. Biblioteka CRT obsługuje cofanie alokacji dla tych bloków. W związku z tym jest mało prawdopodobne, że są one widoczne w raporcie przecieków pamięci, chyba że wystąpi istotny problem, na przykład Biblioteka CRT jest uszkodzona.  
  
  Istnieją dwa inne typy bloków pamięci, które nigdy nie pojawiają się w raportach przecieków pamięci. *Bezpłatny blok* to pamięć, która została wydana. Oznacza to, że nie jest wycieka z definicji. *Blok ignorowany* jest pamięcią, która została jawnie oznaczona, aby wykluczyć ją z raportu przecieków pamięci.  
  
  Techniki te działają w przypadku pamięci przystosowanej przy użyciu standardowej `malloc` funkcji CRT. Jeśli program przydziela pamięć przy użyciu operatora języka C++ `new` , może być jednak widoczny tylko plik i numer wiersza, w którym implementacja `operator new` wywołań globalnych `_malloc_dbg` w raporcie przecieku pamięci. Ponieważ takie zachowanie nie jest bardzo przydatne, można je zmienić w celu zgłoszenia wiersza, który dokonał alokacji, przy użyciu makra, które wygląda następująco: 
 
```cpp  
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```  
  
Teraz można zastąpić operator przy `new` użyciu `DBG_NEW` makra w kodzie. W kompilacjach debugowania wykorzystuje Przeciążenie globalne `operator new` , które pobiera dodatkowe parametry dla typu bloku, pliku i numeru wiersza. To Przeciążenie `new` wywołań `_malloc_dbg` do rejestrowania dodatkowych informacji. W przypadku korzystania `DBG_NEW` z programu, w raportach o przeciekach pamięci jest wyświetlana nazwa pliku i numer wiersza, w którym zostały przydzieloną wycieki obiekty. W kompilacjach detalicznych używa domyślnego `new` . (Nie zalecamy tworzenia makra preprocesora o nazwie `new` lub dowolnego innego słowa kluczowego języka). Oto przykład techniki:  
  
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
  
Po uruchomieniu tego kodu w debugerze w programie Visual Studio, wywołanie w celu `_CrtDumpMemoryLeaks` wygenerowania raportu w oknie **danych wyjściowych** wygląda podobnie do przedstawionego poniżej:  
  
```Output  
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD 
Object dump complete.
```  
  
Oznacza to, że nadmierna alokacja była w wierszu 20 debug_new. cpp.  
  
## <a name="setting-breakpoints-on-a-memory-allocation-number"></a>Ustawianie punktów przerwania na numer przydziału pamięci  
 Numer alokacji pamięci informuje o przydzieleniu przecieku pamięci. Blok z liczbą alokacji pamięci 18, na przykład, to 18-blok pamięci przydzielonej podczas uruchamiania aplikacji. Raport CRT zlicza wszystkie alokacje bloków pamięci podczas przebiegu. Obejmuje to alokacje przez bibliotekę CRT i inne biblioteki, takie jak MFC. W związku z tym blok o numerze alokacji pamięci 18 nie może być 18-tym blok pamięci przydzielonego przez kod. Zwykle nie będzie to możliwe.  
  
 Możesz użyć numeru alokacji, aby ustawić punkt przerwania dla alokacji pamięci.  
  
#### <a name="to-set-a-memory-allocation-breakpoint-using-the-watch-window"></a>Aby ustawić punkt przerwania alokacji pamięci przy użyciu okno wyrażeń kontrolnych  
  
1. Ustaw punkt przerwania w bliskiej części początku aplikacji, a następnie uruchom aplikację.  
  
2. Gdy aplikacja zostanie przerwana w punkcie przerwania, okno **czujka** .  
  
3. W oknie **czujki** wpisz `_crtBreakAlloc` w kolumnie **Nazwa** .  
  
    W przypadku używania wielowątkowej biblioteki DLL z biblioteką CRT (opcja/MD) należy uwzględnić Operator kontekstu: `{,,ucrtbased.dll}_crtBreakAlloc`  
  
4. Naciśnij klawisz **Return**.  
  
    Debuger oblicza wywołanie i umieszcza wynik w kolumnie **wartość** . Ta wartość będzie równa-1, jeśli nie ustawisz żadnych punktów przerwania dla alokacji pamięci.  
  
5. W kolumnie **wartość** Zastąp wartość wyświetlaną z numerem alokacji alokacji pamięci, w której chcesz przerwać.  
  
   Po ustawieniu punktu przerwania w numerze alokacji pamięci można kontynuować debugowanie. Należy zachować ostrożność, aby uruchomić program w taki sam sposób, jak w poprzednim przebiegu, aby kolejność alokacji pamięci nie zmieniła się. Gdy program jest podzielony na określony przydział pamięci, można użyć okna **stosu wywołań** i innych okien debugera, aby określić warunki, w których przydzielono pamięć. Następnie można kontynuować wykonywanie, aby zobaczyć, co się dzieje z obiektem i określić przyczynę nieprawidłowego cofnięcia przydziału.  
  
   Ustawienie punktu przerwania danych na obiekcie może być również pomocne. Aby uzyskać więcej informacji, zobacz [Używanie punktów przerwania](../debugger/using-breakpoints.md).  
  
   Można również ustawić punkty przerwania alokacji pamięci w kodzie. Istnieją dwa sposoby wykonania tej czynności:  
  
```  
_crtBreakAlloc = 18;  
```  
  
 lub:  
  
```  
_CrtSetBreakAlloc(18);  
```  
  
## <a name="comparing-memory-states"></a>Porównywanie Stanów pamięci  
 Inna technika lokalizowania przecieków pamięci polega na tworzeniu migawek stanu pamięci aplikacji w kluczowych punktach. Aby wykonać migawkę stanu pamięci w danym punkcie w aplikacji, Utwórz strukturę **_CrtMemState** i przekaż ją do `_CrtMemCheckpoint` funkcji. Ta funkcja wypełnia strukturę migawką bieżącego stanu pamięci:  
  
```  
_CrtMemState s1;  
_CrtMemCheckpoint( &s1 );  
  
```  
  
 `_CrtMemCheckpoint` wypełnia strukturę migawką bieżącego stanu pamięci.  
  
 Aby wyprowadzić zawartość struktury **_CrtMemState** , Przekaż strukturę do `_ CrtMemDumpStatistics` funkcji:  
  
```  
_CrtMemDumpStatistics( &s1 );  
  
```  
  
 `_ CrtMemDumpStatistics` wyprowadza zrzut stanu pamięci, który wygląda następująco:  
  
```  
0 bytes in 0 Free Blocks.  
0 bytes in 0 Normal Blocks.  
3071 bytes in 16 CRT Blocks.  
0 bytes in 0 Ignore Blocks.  
0 bytes in 0 Client Blocks.  
Largest number used: 3071 bytes.  
Total allocations: 3764 bytes.  
  
```  
  
 Aby określić, czy przeciek pamięci wystąpił w sekcji kodu, można wykonać migawki stanu pamięci przed i po sekcji, a następnie użyć `_ CrtMemDifference` do porównania dwóch stanów:  
  
```  
_CrtMemCheckpoint( &s1 );  
// memory allocations take place here  
_CrtMemCheckpoint( &s2 );  
  
if ( _CrtMemDifference( &s3, &s1, &s2) )  
   _CrtMemDumpStatistics( &s3 );  
```  
  
 `_CrtMemDifference` porównuje Stany pamięci `s1` i `s2` zwraca wynik w ( `s3` ), który jest różnicą `s1` i `s2` .  
  
 Jedna z technik znajdowania przecieków pamięci rozpoczyna się od umieszczenia `_CrtMemCheckpoint` wywołań na początku i na końcu aplikacji, a następnie za pomocą `_CrtMemDifference` programu, aby porównać wyniki. W przypadku `_CrtMemDifference` wyświetlenia przecieku pamięci można dodać więcej `_CrtMemCheckpoint` wywołań, aby podzielić program za pomocą wyszukiwania binarnego do momentu wyizolowania źródła wycieku.  
  
## <a name="false-positives"></a>Fałszywie dodatnie  
 W niektórych przypadkach `_CrtDumpMemoryLeaks` może dawać fałszywych wskazań przecieków pamięci. Taka sytuacja może wystąpić, jeśli używasz biblioteki, która oznacza wewnętrzne alokacje jako _NORMAL_BLOCKs zamiast `_CRT_BLOCK` s lub `_CLIENT_BLOCK` s. W takim przypadku `_CrtDumpMemoryLeaks` nie jest możliwe poinformowanie różnic między przydziałami użytkowników i wewnętrznymi przydziałami bibliotek. Jeśli globalne destruktory alokacji biblioteki są uruchamiane po punkcie, w którym jest wywoływana `_CrtDumpMemoryLeaks` , każda alokacja biblioteki wewnętrznej jest raportowana jako przeciek pamięci. Starsze wersje biblioteki standardowych szablonów (starszej niż Visual Studio .NET) powodowały `_CrtDumpMemoryLeaks` zgłaszanie fałszywych wyników fałszywie, ale zostały one rozwiązane w ostatnich wersjach.  
  
## <a name="see-also"></a>Zobacz też  
 [Szczegóły sterty debugowania CRT](../debugger/crt-debug-heap-details.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
