---
title: Szczegóły dotyczące sterty debugowania CRT | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 95add394f6f3e3e62a7441fe5bb0b4c415509527
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54760589"
---
# <a name="crt-debug-heap-details"></a>Szczegóły dotyczące sterty debugowania CRT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ten temat zawiera szczegółowy widok sterty debugowania CRT.  
  
##  <a name="BKMK_Contents"></a> Zawartość  
 [Znajdź przepełnienia bufora z debugowaniem sterty](#BKMK_Find_buffer_overruns_with_debug_heap)  
  
 [Typy bloków na stercie debugowania](#BKMK_Types_of_blocks_on_the_debug_heap)  
  
 [Sprawdzanie sterty integralności i przecieki pamięci](#BKMK_Check_for_heap_integrity_and_memory_leaks)  
  
 [Skonfiguruj debugowanie sterty](#BKMK_Configure_the_debug_heap)  
  
 [New, delete i _CLIENT_BLOCKs w języku C++ sterta debugowania](#BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap)  
  
 [Funkcje raportowania stanu stosu](#BKMK_Heap_State_Reporting_Functions)  
  
 [Śledź zlecenia alokacji sterty](#BKMK_Track_Heap_Allocation_Requests)  
  
##  <a name="BKMK_Find_buffer_overruns_with_debug_heap"></a> Znajdź przepełnienia bufora z debugowaniem sterty  
 Dwie najbardziej typowe i trudne problemy, które napotykają programiści to zastępowanie końca przydzielonego buforu i przecieki pamięci (nie można zwolnić alokacji, które są już potrzebne). Stos debugowania oferuje zaawansowane narzędzia do rozwiązywania problemów z alokacją pamięci tego rodzaju.  
  
 Debuguj wersje funkcji w stosie wywołań wersje standardowe lub podstawowe używane w wersji kompilacji. Żądając bloku pamięci, Menedżer stosu debugowania przydziela ze stosu podstawowego nieco większy blok pamięci niż żądany, a następnie zwraca wskaźnik do Twojej części tego bloku. Załóżmy, że aplikacja zawiera wywołanie: `malloc( 10 )`. W kompilacji wydania [— funkcja malloc](http://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0) wywołuje procedurę alokacji stosu podstawowego z żądaniem o przydział 10 bajtów. Do kompilacji debugowanej, jednak `malloc` wywoływałby [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb), która będzie następnie wywołaj procedurę alokacji stosu podstawowego z żądaniem przydziału 10 bajtów plus około 36 bajtów dodatkowej pamięci. Wszystkie wynikające bloki pamięci w stercie debugowania są połączone na pojedynczej liście połączonej, uporządkowane według daty alokacji.  
  
 Dodatkowa pamięć przydzielana przez procedury stosu debugowania jest używana na potrzeby informacji księgowych, wskaźników, bloki pamięci debugowania łączy ze sobą oraz małych buforów po obu stronach danych, aby przechwycić zastępuje przydzielonego regionu.  
  
 Obecnie Struktura nagłówka bloku używana do przechowywania informacji księgowych sterty debugowania jest zadeklarowana w następujący sposób w DBGINT. Plik nagłówka H:  
  
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
  
 `NoMansLand` Buforów po obu stronach obszaru danych użytkownika bloku są obecnie rozmiar 4 bajtów i są wypełnione znaną wartością bajtową używane przez procedury stosu debugowania, aby sprawdzić, czy limity bloku pamięci użytkownika nie zostały zastąpione. Stos debugowania wypełnia również nowe bloki pamięci znaną wartością. Jeśli zostanie wybrana opcja zachowania zwolnionych bloków połączonej liście stosu jak wyjaśniono poniżej, te bloki zwolnione również są wypełnione znaną wartością. Obecnie rzeczywiste wartości bajt są następujące:  
  
 NoMansLand (0xFD)  
 "NoMansLand" buforów po obu stronach pamięci używanej przez aplikację są obecnie wypełniane wartością 0xFD.  
  
 Bloki zwolnione (0xDD)  
 Zwolnione bloki, które pozostają nieużywane dwukierunkowej stosu debugowania po liście `_CRTDBG_DELAY_FREE_MEM_DF` jest ustawiona flaga są obecnie wypełnione wartością 0xDD.  
  
 Nowe obiekty (0xCD)  
 Nowe obiekty są wypełnione 0xcd, gdy są przydzielone.  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop")  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
##  <a name="BKMK_Types_of_blocks_on_the_debug_heap"></a> Typy bloków na stercie debugowania  
 Każdy blok pamięci w stosie debugowania jest przypisany do jednego z pięciu typów alokacji. Te typy są śledzone i raportowane inaczej do celów wykrywania przecieków i raportowania stanu. Można określić typ bloku, przydzielając go za pomocą bezpośredniego wywołania jednej z funkcji alokacji sterty debugowania, takie jak [_malloc_dbg](http://msdn.microsoft.com/library/c97eca51-140b-4461-8bd2-28965b49ecdb). Pięć typów bloków pamięci w stosie debugowania (w **nBlockUse** członkiem **_CrtMemBlockHeader** struktury) są następujące:  
  
 **_NORMAL_BLOCK**  
 Wywołanie [— funkcja malloc](http://msdn.microsoft.com/library/144fcee2-be34-4a03-bb7e-ed6d4b99eea0) lub [calloc](http://msdn.microsoft.com/library/17bb79a1-98cf-4096-90cb-1f9365cd6829) tworzy Blok normalny. Jeśli zamierzasz używać tylko bloków normalnych i nie potrzebujesz bloków klienta, warto zdefiniować [_CRTDBG_MAP_ALLOC](http://msdn.microsoft.com/library/435242b8-caea-4063-b765-4a608200312b), co powoduje, że wszystkie alokacji stosu wywołań mają być mapowane do ich odpowiedników debugowania w kompilacjach do debugowania. Umożliwi to pliku nazwa i wierszu numer informacji na temat każdego wywołania alokacji mogą być przechowywane w odpowiednim nagłówku bloku.  
  
 `_CRT_BLOCK`  
 Bloki pamięci przydzielane wewnętrznie przez wiele funkcji biblioteki wykonawczej są oznaczane jako bloki CRT, dzięki czemu mogą być obsługiwane osobno. W rezultacie, wykrywanie przecieków i inne operacje nie wpływa to przez nich. Alokacji nigdy nie należy przydzielić, ponownego przydzielenia lub bloku typu CRT.  
  
 `_CLIENT_BLOCK`  
 Aplikacja może śledzić daną grupę alokacji na potrzeby debugowania, alokując je jako ten typ bloku pamięci, za pomocą jawnych wywołań funkcji debugowania sterty. MFC, na przykład przydziela wszystkim **obiektów CObject** jako bloki klienta; inne aplikacje mogą zachować pamięci różnych obiektów w blokach klienta. Można również określić podtypy bloków klienta ziarnistość śledzenia. Aby określić podtypy bloków klienta, przesuń liczbę lewo o 16 bitów i `OR` ją za pomocą `_CLIENT_BLOCK`. Na przykład:  
  
```  
#define MYSUBTYPE 4  
freedbg(pbData, _CLIENT_BLOCK|(MYSUBTYPE<<16));  
```  
  
 Funkcję klienta hak służąca do zrzucania obiektów przechowywanych w blokach klienta można zainstalować przy użyciu [_CrtSetDumpClient](http://msdn.microsoft.com/library/f3dd06d0-c331-4a12-b68d-25378d112033), a następnie wywoływana zawsze wtedy, gdy blok klienta jest zrzucany przez funkcję debugowania. Ponadto [_CrtDoForAllClientObjects](http://msdn.microsoft.com/library/d0fdb835-3cdc-45f1-9a21-54208e8df248) może służyć do wywołania danej funkcji dostarczanej przez aplikację dla każdego bloku klient w stercie debugowania.  
  
 **_FREE_BLOCK**  
 Normalnie bloki, które są zwalniane, są usuwane z listy. Aby sprawdzić, czy zwolniona pamięć jest nadal nie zapisywana lub do symulacji warunków braku pamięci, można zachować zwolnione bloki na liście połączonej, oznaczone jako wolne i wypełnione za pomocą znanej wartości bajtu (obecnie 0xDD).  
  
 **_IGNORE_BLOCK**  
 Istnieje możliwość wyłączyć operacje debugowania sterty przez pewien czas. W tym czasie bloki pamięci są przechowywane na liście, ale są oznaczone jako bloki do ignorowania.  
  
 Aby określić typ i podtyp bloku, należy użyć funkcji [_CrtReportBlockType](http://msdn.microsoft.com/library/0f4b9da7-bebb-4956-9541-b2581640ec6b) i makr **_BLOCK_TYPE** i **_BLOCK_SUBTYPE**. Makra są zdefiniowane (w pliku crtdbg.h), w następujący sposób:  
  
```  
#define _BLOCK_TYPE(block)          (block & 0xFFFF)  
#define _BLOCK_SUBTYPE(block)       (block >> 16 & 0xFFFF)  
```  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
##  <a name="BKMK_Check_for_heap_integrity_and_memory_leaks"></a> Sprawdzanie sterty integralności i przecieki pamięci  
 Wiele funkcji sterty debugowania musi być dostępny z w obrębie kodu. W poniższej sekcji opisano niektóre funkcje i sposobu ich używania.  
  
 `_CrtCheckMemory`  
 Można użyć wywołania [_CrtCheckMemory](http://msdn.microsoft.com/library/457cc72e-60fd-4177-ab5c-6ae26a420765), na przykład, aby sprawdzić integralność sterty w dowolnym momencie. Ta funkcja sprawdza każdy blok pamięci w stercie, sprawdza, czy informacje nagłówka bloku pamięci są prawidłowe i potwierdza, że bufory nie zostały zmodyfikowane.  
  
 `_CrtSetDbgFlag`  
 Można kontrolować, jak śledzi informacje o stercie debugowania alokacje za pomocą flagi wewnętrznej, [_crtDbgFlag](http://msdn.microsoft.com/library/9e7adb47-8ab9-4e19-81d5-e2f237979973), który można odczytać i ustawić za pomocą [_CrtSetDbgFlag](http://msdn.microsoft.com/library/b5657ffb-6178-4cbf-9886-1af904ede94c) funkcji. Zmieniając tę flagę, możesz poinstruować stertę debugowania, tak aby sprawdzała przecieki pamięci, gdy zamyka program i zgłoś wszelkie wykryte nieszczelności. Podobnie można określić, że zwolnione bloki pamięci nie można usunąć z listy dwukierunkowej, aby symulować sytuacje małej ilości pamięci. Podczas sprawdzania stosu zwolnione bloki są kontrolowane w całości, aby upewnić się, że ich nie zostały zajęte.  
  
 **_CrtDbgFlag** Flaga zawiera następujące pola bitowe:  
  
|Pole bitowe|Domyślny<br /><br /> value|Opis|  
|---------------|-----------------------|-----------------|  
|**_CRTDBG_ALLOC_MEM_DF**|On|Włącza debugowanie alokacji. Jeśli ten bit jest wyłączony, alokacje są powiązane ze sobą, ale ich typem bloku jest **_IGNORE_BLOCK**.|  
|**_CRTDBG_DELAY_FREE_MEM_DF**|Off|Zapobiega faktycznemu, jeśli chodzi o symulowanie warunków małej ilości pamięci w pamięci. Jeśli ten bit jest włączony, zwolnione bloki są trzymane w połączonej liście stosu debugowania, ale są oznaczone jako **_FREE_BLOCK** i wypełnione specjalną wartością bajtu.|  
|**_CRTDBG_CHECK_ALWAYS_DF**|Off|Powoduje, że **_CrtCheckMemory** do wywoływania na każdej alokacji i dezalokacji. To spowalnia wykonanie, ale zapewnia szybkie wyłapywanie błędów.|  
|**_CRTDBG_CHECK_CRT_DF**|Off|Powoduje, że bloki oznaczone jako typ **_CRT_BLOCK** mają zostać uwzględnione w operacjach wykrywania przecieków i różnic stanów. Jeśli ten bit jest wyłączony, pamięć używana wewnętrznie przez bibliotekę uruchomieniową jest ignorowana podczas takich operacji.|  
|**_CRTDBG_LEAK_CHECK_DF**|Off|Powoduje sprawdzanie przecieków, wykonywane przy zamykaniu programu poprzez wywołanie **_CrtDumpMemoryLeaks**. Raport o błędzie jest generowany, gdy aplikacja nie udało się zwolnić pamięć, jaką przydzieliła.|  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
##  <a name="BKMK_Configure_the_debug_heap"></a> Skonfiguruj debugowanie sterty  
 Wszystkie wywołania do funkcji sterty, takich jak `malloc`, `free`, `calloc`, `realloc`, `new`, i `delete` rozwiązania do wersje tych funkcji, które działają na stercie debugowania. Po zwolnieniu bloku pamięci stos debugowania automatycznie sprawdza spójność buforów po obu stronach obszaru przydzielonego i generuje raport o błędach, jeżeli zastąpienie wystąpiło.  
  
 **Aby używać debugowania sterty**  
  
- Połącz debugera kompilacji swojej aplikacji przy użyciu debugowania wersji biblioteki wykonawczej C.  
  
  **Aby zmienić jedno lub więcej pól bitowych _crtDbgFlag i utworzyć nowy stan flagi**  
  
1. Wywołaj `_CrtSetDbgFlag` z `newFlag` parametr `_CRTDBG_REPORT_FLAG` (Aby uzyskać bieżący `_crtDbgFlag` stanu) i przechowuj zwracaną wartość w zmiennej tymczasowej.  
  
2. Włącz wszystkie bity, używając `OR`- ing (bitowe &#124; symbol) zmienną tymczasową i odpowiednimi maskami bitowymi (reprezentowane przez stałe manifestu w kodzie aplikacji).  
  
3. Wyłącz usługi bits przez `AND`- ing (bitowe & symbol) zmiennej `NOT` (bitowe ~ symbol) z odpowiednią masek bitowych.  
  
4. Wywołaj `_CrtSetDbgFlag` z `newFlag` parametr ustawiony na wartość przechowywana w zmiennej tymczasowej, aby utworzyć nowy stan dla `_crtDbgFlag`.  
  
   Na przykład następujące wiersze kodu, włączyć funkcję automatycznego wykrywania przecieków i wyłączają sprawdzanie bloków typu `_CRT_BLOCK`:  
  
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
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
##  <a name="BKMK_new__delete__and__CLIENT_BLOCKs_in_the_C___debug_heap"></a> New, delete i _CLIENT_BLOCKs w języku C++ sterta debugowania  
 Wersje do debugowania biblioteki wykonawczej języka C zawierają wersje do debugowania języka C++ `new` i `delete` operatorów. Jeśli używasz `_CLIENT_BLOCK` typu alokacji, należy wywołać wersję debugowania `new` operator bezpośrednio lub utworzyć makra, które zastępują `new` operatora w trybie debugowania, jak pokazano w poniższym przykładzie:  
  
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
  
 Wersja debugowania `delete` operator współpracuje z bloku wszystkich typów i nie wymaga wprowadzania zmian w programie podczas kompilowania wersji do.  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
##  <a name="BKMK_Heap_State_Reporting_Functions"></a> Funkcje raportowania stanu stosu  
 **_CrtMemState**  
  
 Aby przechwycić migawkę podsumowania stanu stosu w danym momencie, użyj struktury _CrtMemState zdefiniowanej w CRTDBG. GODZ.:  
  
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
  
 Struktura ta zapisuje wskaźnik do pierwszego bloku (najbardziej niedawno przydzielonego) połączonej liście stosu debugowania. Następnie w dwóch tablicach rejestruje block ile poszczególnych typów pamięci (_NORMAL_BLOCK, `_CLIENT_BLOCK`, _FREE_BLOCK itd.) są na liście oraz liczbę bajtów alokowanych w każdym typie bloku. Na koniec rejestruje najwyższą liczbą bajtów alokowaną w stercie jako całość do tego punktu oraz liczbę aktualnie przydzielonych bajtów.  
  
 **Inne funkcje raportowania CRT**  
  
 Poniższe funkcje raportują stan i zawartość stosu i skorzystaj z informacji w celu wykrycia przecieków pamięci i innych problemów.  
  
|Funkcja|Opis|  
|--------------|-----------------|  
|[_CrtMemCheckpoint](http://msdn.microsoft.com/library/f1bacbaa-5a0c-498a-ac7a-b6131d83dfbc)|Zapisuje migawkę stosu w **_CrtMemState** struktury dostarczoną przez aplikację.|  
|[_CrtMemDifference](http://msdn.microsoft.com/library/0f327278-b551-482f-958b-76941f796ba4)|Porównuje dwie struktury stanu pamięci, zapisuje różnicę między nimi w trzeciej strukturze i zwraca wartość PRAWDA, jeśli dwa stany są różne.|  
|[_CrtMemDumpStatistics](http://msdn.microsoft.com/library/27b9d731-3184-4a2d-b9a7-6566ab28a9fe)|Zrzuca danego **_CrtMemState** struktury. Struktura może zawierać migawkę stanu sterty debugowania w danym momencie lub różnicę między dwiema migawkami.|  
|[_CrtMemDumpAllObjectsSince](http://msdn.microsoft.com/library/c48a447a-e6bb-475c-9271-a3021182a0dc)|Zrzuca informacje o wszystkich obiektach przydzielonych od wykonania danej migawki stosu lub od początku wykonywania. Za każdym razem, gdy Zrzuca **_CLIENT_BLOCK** bloku, wywołuje funkcję zaczepienia dostarczoną przez aplikację, jeśli została ona zainstalowana za pomocą **_CrtSetDumpClient**.|  
|[_CrtDumpMemoryLeaks](http://msdn.microsoft.com/library/71b2eab4-7f55-44e8-a55a-bfea4f32d34c)|Określa, czy wszystkie pamięci przecieków wystąpił od momentu rozpoczęcia wykonywania programu, a jeśli tak, zrzuca wszystkie przydzielone obiekty. Za każdym razem, gdy **_CrtDumpMemoryLeaks** zrzuty **_CLIENT_BLOCK** bloku, wywołuje funkcję zaczepienia dostarczoną przez aplikację, jeśli została ona zainstalowana za pomocą **_CrtSetDumpClient**.|  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
##  <a name="BKMK_Track_Heap_Allocation_Requests"></a> Śledź zlecenia alokacji sterty  
 Mimo że precyzyjne określenie źródła pliku nazwa i numer wiersza w którym działa makro raportowania lub potwierdzenia jest często bardzo pomocne w odnalezieniu przyczyny problemu, nie jest taka sama jak mogą być istotne w funkcji alokacji sterty. Podczas gdy makra można wstawiać w wielu odpowiednich punktach w drzewie logiki aplikacji, przydział jest często ukryty w specjalnej procedurze, która jest wywoływana z wielu różnych miejsc w wielu różnych okresach. Pytanie jest zwykle nie wiersz kodu dokonał złej alokacji, ale raczej która z tysięcy alokacji dokonanych przez ten wiersz kodu była zła i dlaczego.  
  
 **Unikatowe numery żądań alokacji i _crtBreakAlloc**  
  
 Najprostszym sposobem określenia konkretnej alokacji stosu, udała, jest korzystanie z zalet unikatowy numer żądania alokacji związanego z każdym blokiem w stosie debugowania. Gdy informacje o bloku są raportowane przez jedną z funkcji zrzutu, ten numer żądania alokacji jest ujęty w nawiasy klamrowe (na przykład "{36}").  
  
 Znając numer żądania alokacji nieprawidłowo zaalokowanego bloku, możesz przekazać ten numer do [_CrtSetBreakAlloc](http://msdn.microsoft.com/library/33bfc6af-a9ea-405b-a29f-1c2d4d9880a1) do utworzenia punktu przerwania. Wykonywanie zostanie przerwane tuż przed alokowanie bloku i używa wycofywania, aby określić, która procedura była odpowiedzialna za błędne wywołanie. Aby uniknąć konieczności ponownego kompilowania, można osiągnąć to samo w debugerze, ustawiając **_crtBreakAlloc** numer żądania alokacji Cię interesuje.  
  
 **Tworzenie wersji debugowania procedur Twojej alokacji**  
  
 Nieco bardziej skomplikowane podejście dotyczy Tworzenie wersji debugowania własnych procedur alokacji, porównywalnych do **_dbg** wersje [funkcji alokacji sterty](../debugger/debug-versions-of-heap-allocation-functions.md). Możesz następnie przekazać plik źródłowy i wiersz argumentów za pośrednictwem do źródłowych procedur alokacji sterty, a następnie od razu będzie można zobaczyć, skąd pochodzi zła Alokacja.  
  
 Na przykład załóżmy, że aplikacja zawiera często używaną procedurę podobną do następującej:  
  
```  
int addNewRecord(struct RecStruct * prevRecord,  
                 int recType, int recAccess)  
{  
    // ...code omitted through actual allocation...   
    if ((newRec = malloc(recSize)) == NULL)  
    // ... rest of routine omitted too ...   
}  
```  
  
 W pliku nagłówkowym można dodać kod, takie jak następujące:  
  
```  
#ifdef _DEBUG  
#define  addNewRecord(p, t, a) \  
            addNewRecord(p, t, a, __FILE__, __LINE__)  
#endif  
```  
  
 Następnie możesz zmienić przydział w swojej procedurze tworzenie rekordu w następujący sposób:  
  
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
  
 Teraz źródła pliku nazwa i numer wiersza gdzie `addNewRecord` wywołano będą przechowywane w każdym bloku wynikowym przydzielony w stercie debugowania i będą raportowane przy tym bloku jest sprawdzany pod.  
  
 ![Powrót do początku](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [zawartość](#BKMK_Contents)  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie kodu natywnego](../debugger/debugging-native-code.md)
