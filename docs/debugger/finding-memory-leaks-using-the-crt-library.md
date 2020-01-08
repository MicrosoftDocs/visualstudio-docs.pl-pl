---
title: Znajdowanie przecieków pamięci za pomocą biblioteki CRT | Microsoft Docs
ms.date: 10/04/2018
ms.topic: conceptual
dev_langs:
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
ms.openlocfilehash: 13a346aa0212f4830c2c88ed866b674fc19d30bd
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75404980"
---
# <a name="find-memory-leaks-with-the-crt-library"></a>Znajdowanie przecieków pamięci za pomocą biblioteki CRT

Przecieki pamięci są między najbardziej subtelnymi i trudno wykrywanymi usterkami w języku C/C++ Apps. Przecieki pamięci z powodu błędu nie można poprawnie cofnąć przydziału pamięci, która została wcześniej przyznana. Niewielki przeciek pamięci może nie być zauważalny w pierwszej kolejności, ale w miarę upływu czasu może powodować występowanie problemów z niską wydajnością w przypadku braku pamięci w aplikacji. Przeciek aplikacji wykorzystującej całą dostępną pamięć może powodować awarię innych aplikacji, a także tworzenie pomyłek w przypadku, gdy aplikacja jest odpowiedzialna. Nawet nieszkodliwe przecieki pamięci mogą wskazywać na inne problemy, które należy poprawić.

Debuger [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i biblioteka uruchomieniowa C (CRT) mogą pomóc w wykrywaniu i identyfikowaniu przecieków pamięci.

## <a name="enable-memory-leak-detection"></a>Włącz wykrywanie przecieków pamięci

Podstawowe narzędzia do wykrywania przecieków pamięci to debuger C/C++ Debugger oraz funkcja sterty debugowania biblioteki wykonawczej c (CRT).

Aby włączyć wszystkie funkcje sterty debugowania, w C++ programie należy uwzględnić następujące instrukcje:

```cpp
#define _CRTDBG_MAP_ALLOC
#include <stdlib.h>
#include <crtdbg.h>
```

Instrukcja `#define` mapuje podstawową wersję funkcji sterty CRT do odpowiedniej wersji debugowania. Jeśli opuścisz instrukcję `#define`, zrzut przecieku pamięci będzie [mniej szczegółowy](#interpret-the-memory-leak-report).

W tym *CRTDBG. h* mapuje `malloc` i `free` funkcje do ich wersji debugowania, [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg) i [_free_dbg](/cpp/c-runtime-library/reference/free-dbg), które śledzą alokację pamięci i cofanie alokacji. To mapowanie odbywa się tylko w kompilacjach debugowania, które mają `_DEBUG`. Kompilacje wydań używają zwykłych `malloc` i `free` funkcji.

Po włączeniu funkcji sterty debugowania za pomocą powyższych instrukcji należy umieścić wywołanie [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) przed punktem wyjścia aplikacji, aby wyświetlić raport o przecieku pamięci po zakończeniu działania aplikacji.

```cpp
_CrtDumpMemoryLeaks();
```

Jeśli aplikacja ma kilka wyjść, nie musisz ręcznie umieszczać `_CrtDumpMemoryLeaks` w każdym punkcie wyjścia. Aby spowodować automatyczne wywołanie `_CrtDumpMemoryLeaks` w każdym punkcie wyjścia, należy nawiązać połączenie `_CrtSetDbgFlag` na początku aplikacji z polami bitowymi przedstawionymi tutaj:

```cpp
_CrtSetDbgFlag ( _CRTDBG_ALLOC_MEM_DF | _CRTDBG_LEAK_CHECK_DF );
```

Domyślnie `_CrtDumpMemoryLeaks` wyprowadza raport o przecieku pamięci do okienka **debugowanie** w oknie **danych wyjściowych** . Jeśli używasz biblioteki, biblioteka może zresetować dane wyjściowe do innej lokalizacji.

Możesz użyć `_CrtSetReportMode`, aby przekierować raport do innej lokalizacji, lub z powrotem do okna **danych wyjściowych** , jak pokazano poniżej:

```cpp
_CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_DEBUG );
```

## <a name="interpret-the-memory-leak-report"></a>Interpretuj raport przecieku pamięci

Jeśli aplikacja nie definiuje `_CRTDBG_MAP_ALLOC`, [_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks) wyświetla raport przecieku pamięci, który wygląda następująco:

```cmd
Detected memory leaks!
Dumping objects ->
{18} normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

Jeśli aplikacja definiuje `_CRTDBG_MAP_ALLOC`, raport o przecieku pamięci wygląda następująco:

```cmd
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\leaktest\leaktest.cpp(20) : {18}
normal block at 0x00780E80, 64 bytes long.
 Data: <                > CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD CD
Object dump complete.
```

Drugi raport przedstawia nazwę pliku i numer wiersza, w którym jest najpierw przydzielono przeciek pamięci.

Niezależnie od tego, czy `_CRTDBG_MAP_ALLOC`, raport o przecieku pamięci wyświetla:

- Numer alokacji pamięci, który jest `18` w przykładzie
- Typ bloku, `normal` w przykładzie.
- Lokalizacja pamięci szesnastkowej, `0x00780E80` w przykładzie.
- Rozmiar bloku, `64 bytes` w przykładzie.
- Pierwsze 16 bajtów danych w bloku w postaci szesnastkowej.

Typy bloków pamięci to *Normal*, *Client*lub *CRT*. *Zwykły blok* to zwykłe pamięci przydzielone przez program. *Blok klienta* jest specjalnym typem bloku pamięci używanym przez programy MFC dla obiektów, które wymagają destruktora. Operator `new` MFC tworzy blok normalny lub blok klienta, zgodnie z potrzebami dla tworzonego obiektu.

*Blok CRT* jest przypisywany przez bibliotekę CRT do własnego użytku. Biblioteka CRT obsługuje cofanie alokacji dla tych bloków, więc bloki CRT nie będą wyświetlane w raporcie przecieku pamięci, chyba że występują poważne problemy z biblioteką CRT.

Istnieją dwa inne typy bloków pamięci, które nigdy nie pojawiają się w raportach przecieków pamięci. *Bezpłatny blok* to pamięć, która została wydana, więc definicja nie jest wycieka. *Blok ignorowanie* to pamięć, która została jawnie oznaczona jako wykluczona z raportu przecieków pamięci.

Powyższe metody identyfikują przecieki pamięci dla pamięci przydzieloną przy użyciu standardowej funkcji `malloc` CRT. Jeśli program alokuje pamięć przy użyciu operatora C++ `new`, można zobaczyć tylko nazwę pliku i numer wiersza, w którym `operator new` wywołuje `_malloc_dbg` w raporcie przecieku pamięci. Aby utworzyć bardziej przydatny raport przecieku pamięci, można napisać makro podobne do poniższego, aby zgłosić wiersz, który dokonał alokacji:

```cpp
#ifdef _DEBUG
    #define DBG_NEW new ( _NORMAL_BLOCK , __FILE__ , __LINE__ )
    // Replace _NORMAL_BLOCK with _CLIENT_BLOCK if you want the
    // allocations to be of _CLIENT_BLOCK type
#else
    #define DBG_NEW new
#endif
```

Teraz można zastąpić operator `new` przy użyciu makra `DBG_NEW` w kodzie. W kompilacjach debugowania `DBG_NEW` używa przeciążenia globalnego `operator new`, który pobiera dodatkowe parametry dla typu bloku, pliku i numeru wiersza. Przeciążenie `new` wywołań `_malloc_dbg` do rejestrowania dodatkowych informacji. Raporty przecieków pamięci pokazują nazwę pliku i numer wiersza, w którym zostały przydzielono przecieki obiektów. Kompilacje wydań nadal używają `new`domyślnego. Oto przykład techniki:

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

Po uruchomieniu tego kodu w debugerze programu Visual Studio wywołanie `_CrtDumpMemoryLeaks` generuje raport w oknie **danych wyjściowych** , który wygląda podobnie do:

```Output
Detected memory leaks!
Dumping objects ->
c:\users\username\documents\projects\debug_new\debug_new.cpp(20) : {75}
 normal block at 0x0098B8C8, 4 bytes long.
 Data: <    > CD CD CD CD
Object dump complete.
```

Ta wartość wyjściowa zgłasza, że przeciek został ujawniony w wierszu 20 *DEBUG_NEW. cpp*.

>[!NOTE]
>Nie zalecamy tworzenia makra preprocesora o nazwie `new`ani żadnego innego słowa kluczowego języka.

## <a name="set-breakpoints-on-a-memory-allocation-number"></a>Ustawianie punktów przerwania na numer przydziału pamięci

Numer alokacji pamięci informuje o przydzieleniu przecieku pamięci. Blok z liczbą alokacji pamięci 18, na przykład, to 18-blok pamięci przydzielonej podczas uruchamiania aplikacji. Raport CRT zlicza wszystkie alokacje bloków pamięci podczas przebiegu, w tym przydziały przez bibliotekę CRT i inne biblioteki, takie jak MFC. W związku z tym, blok alokacji pamięci o numerze 18 prawdopodobnie nie jest tym osiemnastym blokiem pamięci przydzielonym przez kod.

Możesz użyć numeru alokacji, aby ustawić punkt przerwania dla alokacji pamięci.

**Aby ustawić punkt przerwania alokacji pamięci przy użyciu okno wyrażeń kontrolnych:**

1. Ustaw punkt przerwania w bliskim początku aplikacji i Rozpocznij debugowanie.

1. Gdy aplikacja wstrzymuje się w punkcie przerwania, Otwórz okno **czujki** , wybierając pozycję **debuguj** > **Windows** > **Obejrzyj 1** (lub **Obejrzyj 2**, **Obejrzyj 3**lub **Obejrzyj 4**).

1. W oknie **czujka** wpisz `_crtBreakAlloc` w kolumnie **Nazwa** .

   Jeśli używasz wielowątkowej biblioteki DLL w bibliotece CRT (opcja/MD), Dodaj Operator kontekstu: `{,,ucrtbased.dll}_crtBreakAlloc`
   
   Upewnij się, że symbole debugowania są załadowane. W przeciwnym razie `_crtBreakAlloc` będą raportowane jako *niezidentyfikowane*.

1. Naciśnij klawisz **wprowadź**.

   Debuger oblicza wywołanie i umieszcza wynik w kolumnie **wartość** . Ta wartość będzie równa **-1** , jeśli nie ustawisz żadnych punktów przerwania dla alokacji pamięci.

1. W kolumnie **wartość** Zastąp wartość numerem alokacji alokacji pamięci, w której debuger ma przerwać.

Po ustawieniu punktu przerwania w numerze alokacji pamięci Kontynuuj debugowanie. Upewnij się, że jest uruchomiona w tych samych warunkach, więc numer alokacji pamięci nie zmieni się. Gdy program przerwie się w określonej alokacji pamięci, użyj okna **stosu wywołań** i innych okien debugera, aby określić warunki, w których przydzielono pamięć. Następnie można kontynuować wykonywanie, aby zobaczyć, co się dzieje z obiektem i określić przyczynę nieprawidłowego cofnięcia przydziału.

Ustawienie punktu przerwania danych na obiekcie może być również pomocne. Aby uzyskać więcej informacji, zobacz [Używanie punktów przerwania](../debugger/using-breakpoints.md).

Można również ustawić punkty przerwania alokacji pamięci w kodzie. Można ustawić:

```cpp
_crtBreakAlloc = 18;
```

 lub:

```cpp
_CrtSetBreakAlloc(18);
```

## <a name="compare-memory-states"></a>Porównanie Stanów pamięci

Inna technika lokalizowania przecieków pamięci polega na tworzeniu migawek stanu pamięci aplikacji w kluczowych punktach. Aby wykonać migawkę stanu pamięci w danym punkcie w aplikacji, Utwórz strukturę `_CrtMemState` i przekaż ją do funkcji `_CrtMemCheckpoint`.

```cpp
_CrtMemState s1;
_CrtMemCheckpoint( &s1 );
```

Funkcja `_CrtMemCheckpoint` wypełnia strukturę migawką bieżącego stanu pamięci.

Aby wyprowadzić zawartość struktury `_CrtMemState`, Przekaż strukturę do funkcji `_ CrtMemDumpStatistics`:

```cpp
_CrtMemDumpStatistics( &s1 );
```

`_ CrtMemDumpStatistics` wyprowadza zrzut stanu pamięci, który wygląda następująco:

```cmd
0 bytes in 0 Free Blocks.
0 bytes in 0 Normal Blocks.
3071 bytes in 16 CRT Blocks.
0 bytes in 0 Ignore Blocks.
0 bytes in 0 Client Blocks.
Largest number used: 3071 bytes.
Total allocations: 3764 bytes.
```

Aby określić, czy przeciek pamięci wystąpił w sekcji kodu, można wykonać migawki stanu pamięci przed i po sekcji, a następnie użyć `_ CrtMemDifference`, aby porównać te dwa stany:

```cpp
_CrtMemCheckpoint( &s1 );
// memory allocations take place here
_CrtMemCheckpoint( &s2 );

if ( _CrtMemDifference( &s3, &s1, &s2) )
   _CrtMemDumpStatistics( &s3 );
```

`_CrtMemDifference` porównuje Stany pamięci `s1` i `s2` i zwraca wynik (`s3`), który jest różnicą między `s1` i `s2`.

Jedna z technik znajdowania przecieków pamięci rozpoczyna się od umieszczenia `_CrtMemCheckpoint` wywołań na początku i na końcu aplikacji, a następnie przy użyciu `_CrtMemDifference` do porównania wyników. Jeśli `_CrtMemDifference` pokazuje przeciek pamięci, możesz dodać więcej `_CrtMemCheckpoint` wywołań, aby podzielić program za pomocą wyszukiwania binarnego, dopóki nie wyizolowano źródła wycieku.

## <a name="false-positives"></a>Fałszywie dodatnie

 `_CrtDumpMemoryLeaks` może dać fałszywe wskazania przecieków pamięci, jeśli biblioteka oznacza wewnętrzne alokacje jako bloki normalne zamiast bloków CRT lub bloków klientów. W takim przypadku `_CrtDumpMemoryLeaks` nie jest w stanie rozpoznać różnicy między przydziałami użytkowników i wewnętrznymi przydziałami bibliotek. Jeśli globalne destruktory alokacji biblioteki są uruchamiane po punkcie, w którym jest wywoływana `_CrtDumpMemoryLeaks`, każda alokacja biblioteki wewnętrznej jest raportowana jako przeciek pamięci. Wersje biblioteki standardowego szablonu starszej niż Visual Studio .NET mogą spowodować, że `_CrtDumpMemoryLeaks` raportuje takie fałszywe pozytywy.

## <a name="see-also"></a>Zobacz także

- [Szczegóły dotyczące sterty debugowania CRT](../debugger/crt-debug-heap-details.md)
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
