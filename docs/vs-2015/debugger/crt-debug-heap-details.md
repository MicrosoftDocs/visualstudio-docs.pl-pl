---
title: Szczegóły sterty debugowania CRT | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 158aff0f14886ea5d714c35456bf53d5768f57b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697872"
---
# <a name="crt-debug-heap-details"></a>Szczegóły dotyczące sterty debugowania CRT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten temat zawiera szczegółowy opis sterty debugowania CRT.  
  
## <a name="contents"></a><a name="BKMK_Contents"></a> Contents  
 [Znajdź przepełnienia buforów za pomocą sterty debugowania](#BKMK_Find_buffer_overruns_with_debug_heap)  
  
 [Typy bloków na stercie debugowania](#BKMK_Types_of_blocks_on_the_debug_heap)  
  
 [Sprawdź, czy nie ma integralności sterty i przecieków pamięci](#BKMK_Check_for_heap_integrity_and_memory_leaks)  
  
 [Konfigurowanie sterty debugowania](#BKMK_Configure_the_debug_heap)  
  
 [nowe, Usuń i _CLIENT_BLOCKs w stercie debugowania C++](#BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap)  
  
 [Funkcje raportowania stanu sterty](#BKMK_Heap_State_Reporting_Functions)  
  
 [Śledź żądania alokacji sterty](#BKMK_Track_Heap_Allocation_Requests)  
  
## <a name="find-buffer-overruns-with-debug-heap"></a><a name="BKMK_Find_buffer_overruns_with_debug_heap"></a> Znajdź przepełnienia buforów za pomocą sterty debugowania  
 Dwa z najczęstszych i niezwiązanych z problemami problemów, które napotykają programiści, zastąpią koniec przydzielonego buforu i przecieków pamięci (nie można zwolnić alokacji, gdy nie są już potrzebne). Sterta debugowania udostępnia zaawansowane narzędzia do rozwiązywania problemów z alokacją pamięci tego rodzaju.  
  
 Wersje debugowania funkcji sterty wywołują wersje standardowe lub podstawowe używane w kompilacjach wydania. Po zażądaniu bloku pamięci Menedżer sterty debugowania przydziela z sterty podstawowej nieco większy blok pamięci niż żądany i zwraca wskaźnik do części tego bloku. Załóżmy na przykład, że aplikacja zawiera wywołanie: `malloc( 10 )` . W kompilacji wydania [malloc](https://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0) wywoła procedurę alokacji sterty podstawowej żądającą alokacji 10 bajtów. Jednak w kompilacji debugowania `malloc` wywoła [_malloc_dbg](https://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb), który następnie wywoła procedurę alokacji sterty bazowej żądającą przydziału 10 bajtów i około 36 bajtów dodatkowej pamięci. Wszystkie wynikowe bloki pamięci w stercie debugowania są połączone w pojedynczej połączonej liście uporządkowanej według momentu przydzielenia.  
  
 Dodatkowa pamięć przypisana przez procedury debugowania stosu jest używana do informacji o księgowości, dla wskaźników łączących bloki pamięci debugowania ze sobą oraz dla małych buforów po obu stronach danych w celu przechwytywania zastępowanie przydzielonego regionu.  
  
 Obecnie struktura nagłówka bloku służąca do przechowywania informacji księgowych sterty debugowania jest zadeklarowana w następujący sposób w DBGINT. Plik nagłówkowy H:  
  
```  
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
  
 `NoMansLand`Bufory po obu stronach obszaru danych użytkownika bloku mają obecnie 4 bajty i są wypełnione znaną wartością bajtową używaną przez procedury stosu debugowania, aby sprawdzić, czy limity bloku pamięci użytkownika nie zostały zastąpione. Sterta debugowania wypełnia również nowe bloki pamięci o znanej wartości. Jeśli wybierzesz opcję zachowania zwolnionych bloków na liście połączonej sterty, jak wyjaśniono poniżej, te zwolnione bloki również są wypełnione znaną wartością. Obecnie rzeczywiste wartości bajtów są następujące:  
  
 NoMansLand (0xFD)  
 Bufory "NoMansLand" po obu stronach pamięci używanej przez aplikację są obecnie wypełnione wartością 0xFD.  
  
 Zwolnione bloki (0xDD)  
 Zwolnione bloki, które nie są używane na połączonej liście sterty debugowania, gdy `_CRTDBG_DELAY_FREE_MEM_DF` flaga jest ustawiona, są obecnie wypełnione 0xDD.  
  
 Nowe obiekty (0xCD)  
 Nowe obiekty są wypełniane 0xCD po ich przydzieleniu.  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop")  
  
 ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
## <a name="types-of-blocks-on-the-debug-heap"></a><a name="BKMK_Types_of_blocks_on_the_debug_heap"></a> Typy bloków na stercie debugowania  
 Każdy blok pamięci w stercie debugowania jest przypisany do jednego z pięciu typów alokacji. Te typy są śledzone i raportowane inaczej w celu wykrywania przecieków i raportowania stanu. Można określić typ bloku, przydzielając go za pomocą bezpośredniego wywołania jednej z funkcji alokacji sterty debugowania, takiej jak [_malloc_dbg](https://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb). Pięć typów bloków pamięci w stercie debugowania (ustawionych w **elemencie** **_CrtMemBlockHeader** składowej struktury) są następujące:  
  
 **_NORMAL_BLOCK**  
 Wywołanie [malloc](https://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0) lub [calloc](https://msdn.microsoft.com/library/17bb79a1-98cf-4096-90cb-1f9365cd6829) tworzy blok normalny. Jeśli zamierzasz używać tylko bloków normalnych i nie ma potrzeby blokowania klienta, możesz zdefiniować [_CRTDBG_MAP_ALLOC](https://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b), co spowoduje zamapowanie wszystkich wywołań alokacji sterty na ich odpowiedniki debugowania w kompilacjach debugowania. Pozwoli to na przechowywanie w odpowiednim nagłówku bloku informacji o nazwie pliku i numerze wiersza.  
  
 `_CRT_BLOCK`  
 Bloki pamięci przydzielone wewnętrznie przez wiele funkcji biblioteki wykonawczej są oznaczane jako bloki CRT, dzięki czemu mogą być obsługiwane osobno. W związku z tym wykrywanie przecieków i inne operacje nie muszą mieć na nie wpływ. Alokacja nie może nigdy przydzielać, przydzielać ani zwalniać żadnego bloku typu CRT.  
  
 `_CLIENT_BLOCK`  
 Aplikacja może zachować specjalną ścieżkę do danej grupy alokacji do celów debugowania przez przydzielenie ich jako bloku pamięci tego typu przy użyciu jawnych wywołań funkcji sterty debugowania. MFC, na przykład przypisuje wszystkie **obiektów CObject** jako bloki klienta; inne aplikacje mogą przechowywać różne obiekty pamięci w blokach klienta. Można również określić podtypy bloków klienta, aby zwiększyć stopień szczegółowości śledzenia. Aby określić podtypy bloków klienta, przesuń liczbę w lewo o 16 bitów i `OR` z `_CLIENT_BLOCK` . Na przykład:  
  
```  
#define MYSUBTYPE 4  
freedbg(pbData, _CLIENT_BLOCK|(MYSUBTYPE<<16));  
```  
  
 Dostarczona przez klienta funkcja podłączania służąca do zatopienia obiektów przechowywanych w blokach klienta może być instalowana przy użyciu [_CrtSetDumpClient](https://msdn.microsoft.com/library/f3dd06d0-c331-4a12-b68d-25378d112033), a następnie wywoływana za każdym razem, gdy blok klienta jest zrzucany przez funkcję debugowania. Ponadto [_CrtDoForAllClientObjects](https://msdn.microsoft.com/library/d0fdb835-3cdc-45f1-9a21-54208e8df248) może służyć do wywołania danej funkcji dostarczonej przez aplikację dla każdego bloku klienta w stercie debugowania.  
  
 **_FREE_BLOCK**  
 Zwykle bloki, które są zwalniane, zostaną usunięte z listy. Aby sprawdzić, czy zwolniona pamięć nie jest jeszcze zapisywana w lub w celu symulowania warunków niedostatecznej ilości pamięci, możesz pozostawić zwolnione bloki na połączonej liście, oznaczone jako wolne i wypełnione wartością znanego bajtu (obecnie 0xDD).  
  
 **_IGNORE_BLOCK**  
 Można wyłączyć operacje debugowania sterty przez pewien czas. W tym czasie bloki pamięci są przechowywane na liście, ale są oznaczone jako bloki ignorowania.  
  
 Aby określić typ i podtyp danego bloku, użyj funkcji [_CrtReportBlockType](https://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b) i makr **_BLOCK_TYPE** i **_BLOCK_SUBTYPE**. Makra są zdefiniowane (w CRTDBG. h) w następujący sposób:  
  
```  
#define _BLOCK_TYPE(block)          (block & 0xFFFF)  
#define _BLOCK_SUBTYPE(block)       (block >> 16 & 0xFFFF)  
```  
  
 ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
## <a name="check-for-heap-integrity-and-memory-leaks"></a><a name="BKMK_Check_for_heap_integrity_and_memory_leaks"></a> Sprawdź, czy nie ma integralności sterty i przecieków pamięci  
 Wiele funkcji sterty debugowania musi być dostępnych z poziomu kodu. W poniższej sekcji opisano niektóre funkcje i sposoby ich używania.  
  
 `_CrtCheckMemory`  
 Możesz użyć wywołania do [_CrtCheckMemory](https://msdn.microsoft.com/library/457cc72e-60fd-4177-ab5c-6ae26a420765), na przykład, aby sprawdzić integralność sterty w dowolnym momencie. Ta funkcja sprawdza każdy blok pamięci w stercie, sprawdza, czy informacje nagłówka bloku pamięci są prawidłowe i potwierdza, że bufory nie zostały zmodyfikowane.  
  
 `_CrtSetDbgFlag`  
 Można kontrolować sposób, w jaki sterta debugowania śledzi alokacje przy użyciu flagi wewnętrznej, [_crtDbgFlag](https://msdn.microsoft.com/library/9e7adb47-8ab9-4e19-81d5-e2f237979973), którą można odczytać i ustawić przy użyciu funkcji [_CrtSetDbgFlag](https://msdn.microsoft.com/library/b5657ffb-6178-4cbf-9886-1af904ede94c) . Zmieniając tę flagę, można nakazać stosowi debugowania sprawdzanie przecieków pamięci, gdy program zakończy pracę i zgłasza wykryte wycieki. Analogicznie, można określić, że zwolnione bloki pamięci nie zostaną usunięte z listy połączonej, aby symulować sytuacje niskiej ilości pamięci. Po sprawdzeniu sterty te zwolnione bloki są sprawdzane w całości, aby upewnić się, że nie zostały one naruszone.  
  
 Flaga **_crtDbgFlag** zawiera następujące pola bitowe:  
  
|Pole bitowe|Domyślne<br /><br /> value|Opis|  
|---------------|-----------------------|-----------------|  
|**_CRTDBG_ALLOC_MEM_DF**|Włączone|Włącza alokację debugowania. Gdy ten bit jest wyłączony, alokacje pozostają powiązane ze sobą, ale ich typ bloku jest **_IGNORE_BLOCK**.|  
|**_CRTDBG_DELAY_FREE_MEM_DF**|Wyłączony|Uniemożliwia rzeczywiste zwolnienie pamięci, co w przypadku symulowania warunków braku pamięci. Gdy ten bit jest włączony, zwolnione bloki są przechowywane na połączonej liście sterty debugowania, ale są oznaczone jako **_FREE_BLOCK** i wypełnione specjalną wartością bajtową.|  
|**_CRTDBG_CHECK_ALWAYS_DF**|Wyłączony|Powoduje, że **_CrtCheckMemory** być wywoływana przy każdej alokacji i cofa alokacji. To spowalnia wykonywanie, ale szybko przechwytuje błędy.|  
|**_CRTDBG_CHECK_CRT_DF**|Wyłączony|Powoduje, że bloki oznaczone jako typu **_CRT_BLOCK** mają być uwzględniane w operacjach wykrywania przecieków i różnic stanu. Gdy ten bit jest wyłączony, pamięć używana wewnętrznie przez bibliotekę wykonawczą jest ignorowana podczas takich operacji.|  
|**_CRTDBG_LEAK_CHECK_DF**|Wyłączony|Powoduje, że sprawdzanie wycieków odbywa się przy zamykaniu programu za pośrednictwem wywołania do **_CrtDumpMemoryLeaks**. Raport o błędach jest generowany, jeśli aplikacja nie może zwolnić całej przypisanej pamięci.|  
  
 ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
## <a name="configure-the-debug-heap"></a><a name="BKMK_Configure_the_debug_heap"></a> Konfigurowanie sterty debugowania  
 Wszystkie wywołania funkcji sterty, takie jak,,,, `malloc` `free` `calloc` `realloc` `new` i `delete` rozpoznają się z debugowaniem wersji tych funkcji, które działają w stercie debugowania. Po zwolnieniu bloku pamięci sterta debugowania automatycznie sprawdza integralność buforów po obu stronach przyznanego obszaru i wystawia raport o błędach, jeśli nastąpiło zastąpienie.  
  
 **Aby użyć sterty debugowania**  
  
- Połącz kompilację debugowania aplikacji z wersją debugową biblioteki wykonawczej C.  
  
  **Aby zmienić co najmniej jedno _crtDbgFlag pól bitowych i utworzyć nowy stan dla flagi**  
  
1. Wywołaj `_CrtSetDbgFlag` z `newFlag` parametrem ustawionym na `_CRTDBG_REPORT_FLAG` (Aby uzyskać bieżący `_crtDbgFlag` stan) i Zapisz zwracaną wartość w zmiennej tymczasowej.  
  
2. Włącz dowolną liczbę bitów w `OR` miejscu (symbol &#124; bitowego) zmiennej tymczasowej o odpowiednim masek bitowych (przedstawionym w kodzie aplikacji według stałych manifestu).  
  
3. Wyłącz inne bity `AND` (symbol & bitowego) zmiennej z (symbolem bitowym `NOT` ) odpowiedniej masek bitowych.  
  
4. Wywołaj `_CrtSetDbgFlag` z `newFlag` parametrem ustawionym na wartość przechowywaną w zmiennej tymczasowej, aby utworzyć nowy stan dla `_crtDbgFlag` .  
  
   Na przykład następujące wiersze kodu włączają automatyczne wykrywanie przecieków i wyłączanie sprawdzania dla bloków typu `_CRT_BLOCK` :  
  
```  
// Get current flag  
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );  
  
// Turn on leak-checking bit.  
tmpFlag |= _CRTDBG_LEAK_CHECK_DF;  
  
// Turn off CRT block checking bit.  
tmpFlag &= ~_CRTDBG_CHECK_CRT_DF;  
  
// Set flag to the new value.  
_CrtSetDbgFlag( tmpFlag );  
```  
  
 ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
## <a name="new-delete-and-_client_blocks-in-the-c-debug-heap"></a><a name="BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap"></a> nowe, Usuń i _CLIENT_BLOCKs w stercie debugowania C++  
 Wersje debugowe biblioteki wykonawczej C zawierają wersje debugowania języka C++ `new` i `delete` operatorów. W przypadku użycia `_CLIENT_BLOCK` typu alokacji należy wywołać wersję Debug `new` operatora bezpośrednio lub utworzyć makra, które zastępują `new` operator w trybie debugowania, jak pokazano w następującym przykładzie:  
  
```  
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
  
 Wersja do debugowania `delete` operatora działa ze wszystkimi typami bloków i nie wymaga zmian w programie podczas kompilowania wersji wydania.  
  
 ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
## <a name="heap-state-reporting-functions"></a><a name="BKMK_Heap_State_Reporting_Functions"></a> Funkcje raportowania stanu sterty  
 **_CrtMemState**  
  
 Aby przechwycić migawkę podsumowania stanu sterty w danym momencie, użyj struktury _CrtMemState zdefiniowanej w CRTDBG. C  
  
```  
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
  
 Ta struktura zapisuje wskaźnik do pierwszego bloku (ostatnio przydzielony) na liście połączonej sterty debugowania. Następnie w dwóch tablicach rejestruje, ile typów bloków pamięci (_NORMAL_BLOCK, `_CLIENT_BLOCK` , _FREE_BLOCK itd.) znajdują się na liście i liczbę bajtów przydzieloną w każdym typie bloku. Na koniec rejestruje największą liczbę bajtów przydzieloną na stercie jako całość do tego momentu i liczbę aktualnie przyznanych bajtów.  
  
 **Inne funkcje raportowania CRT**  
  
 Poniższe funkcje raportują stan i zawartość sterty oraz wykorzystują te informacje w celu wykrycia przecieków pamięci i innych problemów.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|[_CrtMemCheckpoint](https://msdn.microsoft.com/library/f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc)|Zapisuje migawkę sterty w strukturze **_CrtMemState** dostarczonej przez aplikację.|  
|[_CrtMemDifference](https://msdn.microsoft.com/library/0f327278-b551-482f-958b-76941f796ba4)|Porównuje dwie struktury stanu pamięci, zapisuje różnicę między nimi w trzeciej strukturze stanu i zwraca wartość TRUE, jeśli dwa stany są różne.|  
|[_CrtMemDumpStatistics](https://msdn.microsoft.com/library/27b9d731-3184-4a2d-b9a7-6566ab28a9fe)|Zrzuca daną strukturę **_CrtMemState** . Struktura może zawierać migawkę stanu sterty debugowania w danym momencie lub różnicę między dwiema migawkami.|  
|[_CrtMemDumpAllObjectsSince](https://msdn.microsoft.com/library/c48a447a-e6bb-475c-9271-a3021182a0dc)|Zrzuca informacje o wszystkich obiektach przydzielono od momentu utworzenia danej migawki sterty lub od początku wykonania. Za każdym razem, gdy zrzuca blok **_CLIENT_BLOCK** , wywołuje funkcję Hook dostarczoną przez aplikację, jeśli została ona zainstalowana przy użyciu **_CrtSetDumpClient**.|  
|[_CrtDumpMemoryLeaks](https://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c)|Określa, czy wystąpiły wycieki pamięci od momentu rozpoczęcia wykonywania programu i, jeśli tak, spowoduje zrzut wszystkich przyznanych obiektów. Za każdym razem, **_CrtDumpMemoryLeaks** zrzuca blok **_CLIENT_BLOCK** , wywołuje funkcję Hook dostarczoną przez aplikację, jeśli została zainstalowana przy użyciu **_CrtSetDumpClient**.|  
  
 ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
## <a name="track-heap-allocation-requests"></a><a name="BKMK_Track_Heap_Allocation_Requests"></a> Śledź żądania alokacji sterty  
 Chociaż lokalizację źródłową i numer wiersza, w którym wykonywane jest makro potwierdzenia lub raportowania, często bardzo przydatne w lokalizowaniu przyczyny problemu, to samo nie jest tak samo prawdziwe w przypadku funkcji alokacji sterty. Chociaż makra mogą być wstawiane do kilku odpowiednich punktów w drzewie logiki aplikacji, przydzielanie jest często składowane w specjalnej procedurze, która jest wywoływana z wielu różnych miejsc w wielu różnych porach. Pytanie zazwyczaj nie jest, w jakim wierszu kodu wprowadzono złą alokację, ale zamiast jednego z tysięcy przydziałów dokonanych przez ten wiersz kodu był nieodpowiedni i dlaczego.  
  
 **Unikatowe numery żądań alokacji i _crtBreakAlloc**  
  
 Najprostszym sposobem identyfikacji określonego wywołania alokacji sterty, które poszło źle, jest skorzystanie z unikatowego numeru żądania alokacji skojarzonego z każdym blokiem w stercie debugowania. Gdy informacje o bloku są raportowane przez jedną z funkcji zrzutu, ten numer żądania alokacji jest ujęty w nawiasy klamrowe (na przykład " {36} ").  
  
 Po poznaniu numeru żądania alokacji niewłaściwie przydzielonego bloku można przekazać ten numer do [_CrtSetBreakAlloc](https://msdn.microsoft.com/library/33bfc6af-a9ea-405b-a29f-1c2d4d9880a1) , aby utworzyć punkt przerwania. Wykonanie zostanie przerwane tuż przed przydzieleniem bloku i można nawrotu ustalić, jakie procedury były odpowiedzialne za złe wywołanie. Aby uniknąć ponownego kompilowania, możesz wykonać tę samą czynność w debugerze, ustawiając **_crtBreakAlloc** na numer żądania alokacji, który Cię interesuje.  
  
 **Tworzenie wersji debugowania procedur alokacji**  
  
 Nieco bardziej skomplikowane podejście polega na tworzeniu wersji debugowania własnych procedur alokacji, porównywalnych z wersjami **_dbg** [funkcji alokacji sterty](../debugger/debug-versions-of-heap-allocation-functions.md). Następnie można przekazać argumenty z pliku źródłowego i numeru wiersza do podstawowych procedur alokacji sterty, a natychmiast będzie można zobaczyć, z której pochodzi niewłaściwa alokacja.  
  
 Załóżmy na przykład, że aplikacja zawiera powszechnie używaną procedurę podobną do następującej:  
  
```  
int addNewRecord(struct RecStruct * prevRecord,  
                 int recType, int recAccess)  
{  
    // ...code omitted through actual allocation...   
    if ((newRec = malloc(recSize)) == NULL)  
    // ... rest of routine omitted too ...   
}  
```  
  
 W pliku nagłówkowym można dodać kod, taki jak następujące:  
  
```  
#ifdef _DEBUG  
#define  addNewRecord(p, t, a) \  
            addNewRecord(p, t, a, __FILE__, __LINE__)  
#endif  
```  
  
 Następnie można zmienić alokację w procedurze tworzenia rekordów w następujący sposób:  
  
```  
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
  
 Teraz nazwa pliku źródłowego i numer wiersza, gdzie `addNewRecord` został wywołany, będą przechowywane w każdym wyznaczonym bloku przydzielonym w stercie debugowania i zostanie zgłoszony po zbadaniu tego bloku.  
  
 ![Z powrotem do najwyższej](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartości](#BKMK_Contents)  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
