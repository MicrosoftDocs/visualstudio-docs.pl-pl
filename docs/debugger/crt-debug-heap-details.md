---
title: Szczegóły sterty debugowania CRT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug heap, accessing
- heap functions
- _CRTDBG_CHECK_ALWAYS_DF macro
- _CrtMemDumpStatistics function
- debugging [C++], debug heap
- _CRT_BLOCK macro
- DBGINT.H file
- _CrtMemDumpAllObjectsSince function
- _crtBreakAlloc global variable
- _CrtMemState function
- _CLIENT_BLOCK macro
- _FREE_BLOCK block
- _CrtMemBlockHeader function
- heap state reporting functions
- _CRTDBG_ALLOC_MEM_DF macro
- _CrtSetBreakAlloc function
- memory blocks, allocation types on debug heap
- debugging [C++], CRT debug support
- debug heap, tracking heap allocation requests
- memory allocation, debug heap
- _NORMAL_BLOCK block
- crtBreakAlloc global variable
- _CrtDoForAllClientObjects function
- new operator, using debug heap from C++
- _CrtSetDumpClient function
- debugging [CRT], heap-related problems
- debug heap, solving memory allocation problems
- _CrtMemCheckpoint function
- debug builds, linking to debug heap
- _IGNORE_BLOCK block
- _crtDbgFlag function
- client blocks, specifying subtypes
- memory leaks, tracking
- _CrtSetDbgFlag function
- nBlockUse method
- memory leaks, CRT debug library functions
- _CRTDBG_DELAY_FREE_MEM_DF macro
- allocation request numbers
- _CRTDBG_LEAK_CHECK_DF macro
- debug heap
- memory, debugging
- _CrtReportBlockType function
- _CrtDumpMemoryLeaks function
- _CrtCheckMemory function
- debug heap, CRT
- memory blocks, free
- _BLOCK_TYPE macro
- debug heap, memory blocks
- heap allocation, debug
- debugging memory leaks
- _BLOCK_SUBTYPE macro
- debug heap, using from C++
- _CrtMemDifference function
- heap allocation, tracking requests
- debugging [Visual Studio], debug heap
- delete operator, using debug heap from C++
- blocks, types of on the debug heap
- _CRTDBG_CHECK_CRT_DF macro
- debug heap, reporting functions
ms.assetid: bf78ace6-28e4-4a04-97c6-39e0cdd00ba4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d09319e412d693fc9df95d9ae9b9773f0869afc3
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745623"
---
# <a name="crt-debug-heap-details"></a>Szczegóły dotyczące sterty debugowania CRT
Ten temat zawiera szczegółowy opis sterty debugowania CRT.

## <a name="BKMK_Contents"></a>Contents
[Znajdź przepełnienia buforów za pomocą sterty debugowania](#BKMK_Find_buffer_overruns_with_debug_heap)

[Typy bloków na stercie debugowania](#BKMK_Types_of_blocks_on_the_debug_heap)

[Sprawdź, czy nie ma integralności sterty i przecieków pamięci](#BKMK_Check_for_heap_integrity_and_memory_leaks)

[Konfigurowanie sterty debugowania](#BKMK_Configure_the_debug_heap)

[nowe, Usuń i _CLIENT_BLOCKs w stercie C++ debugowania](#BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap)

[Funkcje raportowania stanu sterty](#BKMK_Heap_State_Reporting_Functions)

[Śledź żądania alokacji sterty](#BKMK_Track_Heap_Allocation_Requests)

## <a name="BKMK_Find_buffer_overruns_with_debug_heap"></a>Znajdź przepełnienia buforów za pomocą sterty debugowania
Dwa z najczęstszych i niezwiązanych z problemami problemów, które napotykają programiści, zastąpią koniec przydzielonego buforu i przecieków pamięci (nie można zwolnić alokacji, gdy nie są już potrzebne). Sterta debugowania udostępnia zaawansowane narzędzia do rozwiązywania problemów z alokacją pamięci tego rodzaju.

Wersje debugowania funkcji sterty wywołują wersje standardowe lub podstawowe używane w kompilacjach wydania. Po zażądaniu bloku pamięci Menedżer sterty debugowania przydziela z sterty podstawowej nieco większy blok pamięci niż żądany i zwraca wskaźnik do części tego bloku. Załóżmy na przykład, że aplikacja zawiera wywołanie: `malloc( 10 )`. W kompilacji wydania [malloc](/cpp/c-runtime-library/reference/malloc) wywoła procedurę alokacji sterty podstawowej żądającą alokacji 10 bajtów. Jednak w kompilacji debugowania `malloc` wywoła [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg), która następnie wywoła procedurę alokacji sterty bazowej żądającą przydziału 10 bajtów i około 36 bajtów dodatkowej pamięci. Wszystkie wynikowe bloki pamięci w stercie debugowania są połączone w pojedynczej połączonej liście uporządkowanej według momentu przydzielenia.

Dodatkowa pamięć przypisana przez procedury debugowania stosu jest używana do informacji o księgowości, dla wskaźników łączących bloki pamięci debugowania ze sobą oraz dla małych buforów po obu stronach danych w celu przechwytywania zastępowanie przydzielonego regionu.

Obecnie struktura nagłówka bloku służąca do przechowywania informacji księgowych sterty debugowania jest zadeklarowana w następujący sposób w DBGINT. Plik nagłówkowy H:

```cpp
typedef struct _CrtMemBlockHeader
{
// Pointer to the block allocated just before this one:
    struct _CrtMemBlockHeader *pBlockHeaderNext;
// Pointer to the block allocated just after this one:
    struct _CrtMemBlockHeader *pBlockHeaderPrev;
    char *szFileName;    // File name
    int nLine;           // Line number
    size_t nDataSize;    // Size of user block
    int nBlockUse;       // Type of block
    long lRequest;       // Allocation number
// Buffer just before (lower than) the user's memory:
    unsigned char gap[nNoMansLandSize];
} _CrtMemBlockHeader;

/* In an actual memory block in the debug heap,
 * this structure is followed by:
 *   unsigned char data[nDataSize];
 *   unsigned char anotherGap[nNoMansLandSize];
 */
```

Bufory `NoMansLand` po obu stronach obszaru danych użytkownika bloku mają obecnie 4 bajty i są wypełnione znaną wartością bajtową używaną przez procedury debugowania stosu, aby sprawdzić, czy limity bloku pamięci użytkownika nie zostały zastąpione. Sterta debugowania wypełnia również nowe bloki pamięci o znanej wartości. Jeśli wybierzesz opcję zachowania zwolnionych bloków na liście połączonej sterty, jak wyjaśniono poniżej, te zwolnione bloki również są wypełnione znaną wartością. Obecnie rzeczywiste wartości bajtów są następujące:

NoMansLand (0xFD) bufory "NoMansLand" po obu stronach pamięci używanej przez aplikację są obecnie wypełnione 0xFD.

Zwolnione bloki (0xDD) zwolnione bloki, które są nieużywane na połączonej liście sterty debugowania, gdy flaga `_CRTDBG_DELAY_FREE_MEM_DF` jest ustawiona, jest obecnie uzupełniona o 0xDD.

Nowe obiekty (0xCD) są wypełniane przy użyciu 0xCD po przydzieleniu.

![Z powrotem do najwyższej](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)

## <a name="BKMK_Types_of_blocks_on_the_debug_heap"></a>Typy bloków na stercie debugowania
Każdy blok pamięci w stercie debugowania jest przypisany do jednego z pięciu typów alokacji. Te typy są śledzone i raportowane inaczej w celu wykrywania przecieków i raportowania stanu. Można określić typ bloku, przydzielając go za pomocą bezpośredniego wywołania jednej z funkcji alokacji sterty debugowania, takich jak [_malloc_dbg](/cpp/c-runtime-library/reference/malloc-dbg). Pięć typów bloków pamięci w stercie debugowania (ustawionych w **elemencie** składowej struktury **_CrtMemBlockHeader** ) są następujące:

**_NORMAL_BLOCK** Wywołanie [malloc](/cpp/c-runtime-library/reference/malloc) lub [calloc](/cpp/c-runtime-library/reference/calloc) tworzy blok normalny. Jeśli zamierzasz używać tylko bloków normalnych i nie ma potrzeby blokowania klienta, możesz zdefiniować [_CRTDBG_MAP_ALLOC](/cpp/c-runtime-library/crtdbg-map-alloc), co spowoduje zamapowanie wszystkich wywołań alokacji sterty na ich odpowiedniki debugowania w kompilacjach debugowania. Pozwoli to na przechowywanie w odpowiednim nagłówku bloku informacji o nazwie pliku i numerze wiersza.

`_CRT_BLOCK` bloki pamięci przydzielone wewnętrznie przez wiele funkcji biblioteki wykonawczej są oznaczane jako bloki CRT, dzięki czemu mogą być obsługiwane osobno. W związku z tym wykrywanie przecieków i inne operacje nie muszą mieć na nie wpływ. Alokacja nie może nigdy przydzielać, przydzielać ani zwalniać żadnego bloku typu CRT.

`_CLIENT_BLOCK` aplikacja może zachować specjalną ścieżkę do danej grupy alokacji do celów debugowania przez przydzielenie ich jako bloku pamięci tego typu przy użyciu jawnych wywołań funkcji sterty debugowania. MFC, na przykład przypisuje wszystkie **obiektów CObject** jako bloki klienta; inne aplikacje mogą przechowywać różne obiekty pamięci w blokach klienta. Można również określić podtypy bloków klienta, aby zwiększyć stopień szczegółowości śledzenia. Aby określić podtypy bloków klienta, przesuń liczbę w lewo o 16 bitów i `OR` ją z `_CLIENT_BLOCK`. Na przykład:

```cpp
#define MYSUBTYPE 4
freedbg(pbData, _CLIENT_BLOCK|(MYSUBTYPE<<16));
```

Dostarczona przez klienta funkcja podłączania służąca do zatopienia obiektów przechowywanych w blokach klienta może być instalowana przy użyciu [_CrtSetDumpClient](/cpp/c-runtime-library/reference/crtsetdumpclient), a następnie wywoływana za każdym razem, gdy blok klienta jest zrzucany przez funkcję debugowania. Ponadto [_CrtDoForAllClientObjects](/cpp/c-runtime-library/reference/crtdoforallclientobjects) może służyć do wywołania danej funkcji dostarczonej przez aplikację dla każdego bloku klienta w stercie debugowania.

**_FREE_BLOCK** Zwykle bloki, które są zwalniane, zostaną usunięte z listy. Aby sprawdzić, czy zwolniona pamięć nie jest jeszcze zapisywana w lub w celu symulowania warunków niedostatecznej ilości pamięci, możesz pozostawić zwolnione bloki na połączonej liście, oznaczone jako wolne i wypełnione wartością znanego bajtu (obecnie 0xDD).

**_IGNORE_BLOCK** Można wyłączyć operacje debugowania sterty przez pewien czas. W tym czasie bloki pamięci są przechowywane na liście, ale są oznaczone jako bloki ignorowania.

Aby określić typ i podtyp danego bloku, użyj funkcji [_CrtReportBlockType](/cpp/c-runtime-library/reference/crtreportblocktype) oraz makr **_BLOCK_TYPE** i **_BLOCK_SUBTYPE**. Makra są zdefiniowane (w CRTDBG. h) w następujący sposób:

```cpp
#define _BLOCK_TYPE(block)          (block & 0xFFFF)
#define _BLOCK_SUBTYPE(block)       (block >> 16 & 0xFFFF)
```

![Z powrotem do najwyższej](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)

## <a name="BKMK_Check_for_heap_integrity_and_memory_leaks"></a>Sprawdź, czy nie ma integralności sterty i przecieków pamięci
Wiele funkcji sterty debugowania musi być dostępnych z poziomu kodu. W poniższej sekcji opisano niektóre funkcje i sposoby ich używania.

`_CrtCheckMemory` można użyć wywołania [_CrtCheckMemory](/cpp/c-runtime-library/reference/crtcheckmemory), na przykład, aby sprawdzić integralność sterty w dowolnym momencie. Ta funkcja sprawdza każdy blok pamięci w stercie, sprawdza, czy informacje nagłówka bloku pamięci są prawidłowe i potwierdza, że bufory nie zostały zmodyfikowane.

`_CrtSetDbgFlag` można kontrolować sposób, w jaki sterta debugowania śledzi alokacje przy użyciu flagi wewnętrznej [_crtDbgFlag](/cpp/c-runtime-library/crtdbgflag), którą można odczytać i ustawić przy użyciu funkcji [_CrtSetDbgFlag](/cpp/c-runtime-library/reference/crtsetdbgflag) . Zmieniając tę flagę, można nakazać stosowi debugowania sprawdzanie przecieków pamięci, gdy program zakończy pracę i zgłasza wykryte wycieki. Analogicznie, można określić, że zwolnione bloki pamięci nie zostaną usunięte z listy połączonej, aby symulować sytuacje niskiej ilości pamięci. Po sprawdzeniu sterty te zwolnione bloki są sprawdzane w całości, aby upewnić się, że nie zostały one naruszone.

Flaga **_crtDbgFlag** zawiera następujące pola bitowe:

|Pole bitowe|Domyślny<br /><br /> value|Opis|
|---------------|-----------------------|-----------------|
|**_CRTDBG_ALLOC_MEM_DF**|On|Włącza alokację debugowania. Gdy ten bit jest wyłączony, alokacje pozostają powiązane ze sobą, ale ich typ bloku to **_IGNORE_BLOCK**.|
|**_CRTDBG_DELAY_FREE_MEM_DF**|Off|Uniemożliwia rzeczywiste zwolnienie pamięci, co w przypadku symulowania warunków braku pamięci. Gdy ten bit jest włączony, zwolnione bloki są przechowywane na połączonej liście sterty debugowania, ale są oznaczone jako **_FREE_BLOCK** i wypełnione specjalną wartością bajtową.|
|**_CRTDBG_CHECK_ALWAYS_DF**|Off|Powoduje, że **_CrtCheckMemory** być wywoływana przy każdej alokacji i cofa alokacji. To spowalnia wykonywanie, ale szybko przechwytuje błędy.|
|**_CRTDBG_CHECK_CRT_DF**|Off|Powoduje, że bloki oznaczone jako typu **_CRT_BLOCK** mają być uwzględniane w operacjach wykrywania przecieków i różnic stanu. Gdy ten bit jest wyłączony, pamięć używana wewnętrznie przez bibliotekę wykonawczą jest ignorowana podczas takich operacji.|
|**_CRTDBG_LEAK_CHECK_DF**|Off|Powoduje, że sprawdzanie wycieków odbywa się przy zamykaniu programu przez wywołanie do **_CrtDumpMemoryLeaks**. Raport o błędach jest generowany, jeśli aplikacja nie może zwolnić całej przypisanej pamięci.|

![Z powrotem do najwyższej](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)

## <a name="BKMK_Configure_the_debug_heap"></a>Konfigurowanie sterty debugowania
Wszystkie wywołania funkcji sterty, takie jak `malloc`, `free`, `calloc`, `realloc`, `new` i `delete` rozwiązują, aby debugować wersje tych funkcji, które działają w stercie debugowania. Po zwolnieniu bloku pamięci sterta debugowania automatycznie sprawdza integralność buforów po obu stronach przyznanego obszaru i wystawia raport o błędach, jeśli nastąpiło zastąpienie.

**Aby użyć sterty debugowania**

- Połącz kompilację debugowania aplikacji z wersją debugową biblioteki wykonawczej C.

  **Aby zmienić co najmniej jedno pole bitowe _crtDbgFlag i utworzyć nowy stan dla flagi**

1. Wywołaj `_CrtSetDbgFlag` z parametrem `newFlag` ustawionym na `_CRTDBG_REPORT_FLAG` (Aby uzyskać bieżący stan `_crtDbgFlag`) i Zapisz zwróconą wartość w zmiennej tymczasowej.

2. Włącz wszelkie bity przez `OR`-do (symbol bitowy &#124; ) zmiennej tymczasowej o odpowiednim masek bitowych (przedstawionym w kodzie aplikacji według stałych manifestu).

3. Wyłącz inne bity przez `AND`-do (symbol & bitowego) zmiennej z `NOT` (bitowym symbolem ~) odpowiedniej masek bitowych.

4. Wywołaj `_CrtSetDbgFlag` z parametrem `newFlag` ustawionym na wartość przechowywaną w zmiennej tymczasowej, aby utworzyć nowy stan dla `_crtDbgFlag`.

   Na przykład następujące wiersze kodu włączają automatyczne wykrywanie przecieków i wyłączanie sprawdzania bloków typu `_CRT_BLOCK`:

```cpp
// Get current flag
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );

// Turn on leak-checking bit.
tmpFlag |= _CRTDBG_LEAK_CHECK_DF;

// Turn off CRT block checking bit.
tmpFlag &= ~_CRTDBG_CHECK_CRT_DF;

// Set flag to the new value.
_CrtSetDbgFlag( tmpFlag );
```

![Z powrotem do najwyższej](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)

## <a name="BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap"></a>nowe, Usuń i _CLIENT_BLOCKs w stercie C++ debugowania
Wersje debugowe biblioteki wykonawczej C zawierają wersje debugowania operatorów C++ `new` i `delete`. Jeśli używasz typu alokacji `_CLIENT_BLOCK`, musisz wywołać wersję Debug operatora `new` bezpośrednio lub utworzyć makra, które zastępują operator `new` w trybie debugowania, jak pokazano w następującym przykładzie:

```cpp
/* MyDbgNew.h
 Defines global operator new to allocate from
 client blocks
*/

#ifdef _DEBUG
   #define DEBUG_CLIENTBLOCK   new( _CLIENT_BLOCK, __FILE__, __LINE__)
#else
   #define DEBUG_CLIENTBLOCK
#endif // _DEBUG

/* MyApp.cpp
        Use a default workspace for a Console Application to
 *      build a Debug version of this code
*/

#include "crtdbg.h"
#include "mydbgnew.h"

#ifdef _DEBUG
#define new DEBUG_CLIENTBLOCK
#endif

int main( )   {
    char *p1;
    p1 =  new char[40];
    _CrtMemDumpAllObjectsSince( NULL );
}
```

Wersja do debugowania operatora `delete` działa ze wszystkimi typami bloków i nie wymaga żadnych zmian w programie podczas kompilowania wersji wydania.

![Z powrotem do najwyższej](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)

## <a name="BKMK_Heap_State_Reporting_Functions"></a>Funkcje raportowania stanu sterty
 **_CrtMemState**

 Aby przechwycić migawkę podsumowania stanu sterty w danym momencie, użyj struktury _CrtMemState zdefiniowanej w CRTDBG. C

```cpp
typedef struct _CrtMemState
{
    // Pointer to the most recently allocated block:
    struct _CrtMemBlockHeader * pBlockHeader;
    // A counter for each of the 5 types of block:
    size_t lCounts[_MAX_BLOCKS];
    // Total bytes allocated in each block type:
    size_t lSizes[_MAX_BLOCKS];
    // The most bytes allocated at a time up to now:
    size_t lHighWaterCount;
    // The total bytes allocated at present:
    size_t lTotalCount;
} _CrtMemState;
```

Ta struktura zapisuje wskaźnik do pierwszego bloku (ostatnio przydzielony) na liście połączonej sterty debugowania. Następnie w dwóch tablicach rejestruje, ile typów bloków pamięci (_NORMAL_BLOCK, `_CLIENT_BLOCK`, _FREE_BLOCK i tak dalej) znajdują się na liście i liczbę bajtów przyznanych w każdym typie bloku. Na koniec rejestruje największą liczbę bajtów przydzieloną na stercie jako całość do tego momentu i liczbę aktualnie przyznanych bajtów.

**Inne funkcje raportowania CRT**

Poniższe funkcje raportują stan i zawartość sterty oraz wykorzystują te informacje w celu wykrycia przecieków pamięci i innych problemów.

|Funkcja|Opis|
|--------------|-----------------|
|[_CrtMemCheckpoint](/cpp/c-runtime-library/reference/crtmemcheckpoint)|Zapisuje migawkę sterty w strukturze **_CrtMemState** dostarczonej przez aplikację.|
|[_CrtMemDifference](/cpp/c-runtime-library/reference/crtmemdifference)|Porównuje dwie struktury stanu pamięci, zapisuje różnicę między nimi w trzeciej strukturze stanu i zwraca wartość TRUE, jeśli dwa stany są różne.|
|[_CrtMemDumpStatistics](/cpp/c-runtime-library/reference/crtmemdumpstatistics)|Zrzuca daną strukturę **_CrtMemState** . Struktura może zawierać migawkę stanu sterty debugowania w danym momencie lub różnicę między dwiema migawkami.|
|[_CrtMemDumpAllObjectsSince](/cpp/c-runtime-library/reference/crtmemdumpallobjectssince)|Zrzuca informacje o wszystkich obiektach przydzielono od momentu utworzenia danej migawki sterty lub od początku wykonania. Przy każdym zrzucie bloku **_CLIENT_BLOCK** wywołuje funkcję Hook dostarczoną przez aplikację, jeśli została ona zainstalowana przy użyciu **_CrtSetDumpClient**.|
|[_CrtDumpMemoryLeaks](/cpp/c-runtime-library/reference/crtdumpmemoryleaks)|Określa, czy wystąpiły wycieki pamięci od momentu rozpoczęcia wykonywania programu i, jeśli tak, spowoduje zrzut wszystkich przyznanych obiektów. Za każdym razem, gdy **_CrtDumpMemoryLeaks** zrzuca blok **_CLIENT_BLOCK** , wywołuje funkcję Hook dostarczoną przez aplikację, jeśli została zainstalowana przy użyciu **_CrtSetDumpClient**.|

![Z powrotem do najwyższej](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)

## <a name="BKMK_Track_Heap_Allocation_Requests"></a>Śledź żądania alokacji sterty
Chociaż lokalizację źródłową i numer wiersza, w którym wykonywane jest makro potwierdzenia lub raportowania, często bardzo przydatne w lokalizowaniu przyczyny problemu, to samo nie jest tak samo prawdziwe w przypadku funkcji alokacji sterty. Chociaż makra mogą być wstawiane do kilku odpowiednich punktów w drzewie logiki aplikacji, przydzielanie jest często składowane w specjalnej procedurze, która jest wywoływana z wielu różnych miejsc w wielu różnych porach. Pytanie zazwyczaj nie jest, w jakim wierszu kodu wprowadzono złą alokację, ale zamiast jednego z tysięcy przydziałów dokonanych przez ten wiersz kodu był nieodpowiedni i dlaczego.

**Unikatowe numery żądań alokacji i _crtBreakAlloc**

Najprostszym sposobem identyfikacji określonego wywołania alokacji sterty, które poszło źle, jest skorzystanie z unikatowego numeru żądania alokacji skojarzonego z każdym blokiem w stercie debugowania. Gdy informacje o bloku są raportowane przez jedną z funkcji zrzutu, ten numer żądania alokacji jest ujęty w nawiasy klamrowe (na przykład "{36}").

Po poznaniu numeru żądania alokacji niewłaściwie przydzielonego bloku można przekazać ten numer do [_CrtSetBreakAlloc](/cpp/c-runtime-library/reference/crtsetbreakalloc) w celu utworzenia punktu przerwania. Wykonanie zostanie przerwane tuż przed przydzieleniem bloku i można nawrotu ustalić, jakie procedury były odpowiedzialne za złe wywołanie. Aby uniknąć ponownego kompilowania, możesz wykonać tę samą czynność w debugerze, ustawiając **_crtBreakAlloc** na numer żądania alokacji, który Cię interesuje.

**Tworzenie wersji debugowania procedur alokacji**

Nieco bardziej skomplikowane podejście polega na tworzeniu wersji debugowania własnych procedur alokacji, które są porównywalne z wersjami **_dbg** [funkcji alokacji sterty](../debugger/debug-versions-of-heap-allocation-functions.md). Następnie można przekazać argumenty z pliku źródłowego i numeru wiersza do podstawowych procedur alokacji sterty, a natychmiast będzie można zobaczyć, z której pochodzi niewłaściwa alokacja.

Załóżmy na przykład, że aplikacja zawiera powszechnie używaną procedurę podobną do następującej:

```cpp
int addNewRecord(struct RecStruct * prevRecord,
                 int recType, int recAccess)
{
    // ...code omitted through actual allocation...
    if ((newRec = malloc(recSize)) == NULL)
    // ... rest of routine omitted too ...
}
```

W pliku nagłówkowym można dodać kod, taki jak następujące:

```cpp
#ifdef _DEBUG
#define  addNewRecord(p, t, a) \
            addNewRecord(p, t, a, __FILE__, __LINE__)
#endif
```

Następnie można zmienić alokację w procedurze tworzenia rekordów w następujący sposób:

```cpp
int addNewRecord(struct RecStruct *prevRecord,
                int recType, int recAccess
#ifdef _DEBUG
               , const char *srcFile, int srcLine
#endif
    )
{
    /* ... code omitted through actual allocation ... */
    if ((newRec = _malloc_dbg(recSize, _NORMAL_BLOCK,
            srcFile, scrLine)) == NULL)
    /* ... rest of routine omitted too ... */
}
```

Teraz nazwa pliku źródłowego i numer wiersza, w którym wywołano `addNewRecord`, będą przechowywane w każdym wyznaczonym bloku przydzielonym w stercie debugowania i zostanie zgłoszone po zbadaniu tego bloku.

![Z powrotem do najwyższej](../debugger/media/pcs_backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)

## <a name="see-also"></a>Zobacz także
[Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
