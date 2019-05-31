---
title: Techniki debugowania MFC | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- AfxEnableMemoryTracking
- CMemoryState
- delayFreeMemDF
- checkAlwaysMemDF
- vs.debug.mfc
- vs.debug.objects.dump
- vs.debug.memory.dump
- allocMemDF
- afxMemDF
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [MFC]
ms.assetid: b154fc31-5e90-4734-8cbd-58dd9fe1f750
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3c795e978de3911b3c5e815583c32e878fd7b173
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65696904"
---
# <a name="mfc-debugging-techniques"></a>Techniki testowania MFC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli debugujesz program MFC te techniki debugowania mogą być przydatne.  
  
## <a name="BKMK_In_this_topic"></a> W tym temacie  
 [AfxDebugBreak](#BKMK_AfxDebugBreak)  
  
 [TRACE — makro](#BKMK_The_TRACE_macro)  
  
 [Wykrywanie przecieków pamięci w MFC](#BKMK_Memory_leak_detection_in_MFC)  
  
- [Śledzenia alokacji pamięci](#BKMK_Tracking_memory_allocations)  
  
- [Włączenie diagnostyki pamięci](#BKMK_Enabling_memory_diagnostics)  
  
- [Tworzenie migawek pamięci](#BKMK_Taking_memory_snapshots)  
  
- [Wyświetlanie statystyk pamięci](#BKMK_Viewing_memory_statistics)  
  
- [Pobieranie obiektu zrzutów](#BKMK_Taking_object_dumps)  
  
  - [Interpretowanie pamięci zrzutów](#BKMK_Interpreting_memory_dumps)  
  
  - [Dostosowywanie obiektu zrzutów](#BKMK_Customizing_object_dumps)  
  
    [Zmniejszenie rozmiaru kompilacji debugowania MFC](#BKMK_Reducing_the_size_of_an_MFC_Debug_build)  
  
  - [Tworzenie aplikacji MFC za pomocą informacji o debugowaniu dla wybranych modułów](#BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules)  
  
## <a name="BKMK_AfxDebugBreak"></a> AfxDebugBreak  
 Biblioteka MFC zawiera specjalny [afxdebugbreak —](https://msdn.microsoft.com/library/c4cd79b9-9327-4db5-a9d6-c4004a92aa30) funkcja, przypadku kodować punktów przerwania w kodzie źródłowym:  
  
```  
AfxDebugBreak( );  
  
```  
  
 Na platformach firmy Intel `AfxDebugBreak` generuje następujący kod, który przerwy w źródle kod zamiast kodu jądra:  
  
```  
_asm int 3  
```  
  
 Na innych platformach usługa `AfxDebugBreak` jedynie wywołuje `DebugBreak`.  
  
 Pamiętaj usunąć `AfxDebugBreak` instrukcji po utworzeniu wersji kompilacji lub użyć `#ifdef _DEBUG` otaczającego je.  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
## <a name="BKMK_The_TRACE_macro"></a> TRACE — makro  
 Aby wyświetlić komunikaty z programu w debugerze [okno danych wyjściowych](../ide/reference/output-window.md), możesz użyć [ATLTRACE](https://msdn.microsoft.com/library/c796baa5-e2b9-4814-a27d-d800590b102e) makro lub MFC [śledzenia](https://msdn.microsoft.com/library/7b6f42d8-b55a-4bba-ab04-c46251778e6f) — makro. Podobnie jak [potwierdzenia](../debugger/c-cpp-assertions.md), makra śledzenia są aktywne tylko w wersji debugowania programu i znikają podczas kompilowania w pełnej wersji.  
  
 W poniższych przykładach pokazano niektóre sposoby używania **śledzenia** makra. Podobnie jak `printf`, **śledzenia** — makro może obsługiwać liczbę argumentów.  
  
```  
int x = 1;  
int y = 16;  
float z = 32.0;  
TRACE( "This is a TRACE statement\n" );  
  
TRACE( "The value of x is %d\n", x );  
  
TRACE( "x = %d and y = %d\n", x, y );  
  
TRACE( "x = %d and y = %x and z = %f\n", x, y, z );  
```  
  
 TRACE — makro prawidłowo obsługuje zarówno char * i wchar_t\* parametrów. W poniższych przykładach pokazano użycie TRACE — makro wraz z różnych typów parametrów.  
  
```  
TRACE( "This is a test of the TRACE macro that uses an ANSI string: %s %d\n", "The number is:", 2);  
  
TRACE( L"This is a test of the TRACE macro that uses a UNICODE string: %s %d\n", L"The number is:", 2);  
  
TRACE( _T("This is a test of the TRACE macro that uses a TCHAR string: %s %d\n"), _T("The number is:"), 2);  
  
```  
  
 Aby uzyskać więcej informacji na temat **śledzenia** makr, zobacz [usługi diagnostyczne](https://msdn.microsoft.com/library/8d78454f-9fae-49c2-88c9-d3fabd5393e8).  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
## <a name="BKMK_Memory_leak_detection_in_MFC"></a> Wykrywanie przecieków pamięci w MFC  
 Biblioteka MFC zawiera klasy i funkcje wykrywania pamięci, który jest przydzielony, ale nigdy z cofniętą alokacją.  
  
### <a name="BKMK_Tracking_memory_allocations"></a> Śledzenia alokacji pamięci  
 W MFC, można użyć makra [DEBUG_NEW](https://msdn.microsoft.com/library/9b379344-4093-4bec-a3eb-e0d8a63ada9d) zamiast **nowe** przecieków operatora, aby łatwiej zlokalizować pamięci. W wersji debugowania programu `DEBUG_NEW` śledzi informacje o pliku nazwa i numer wiersza dla każdego obiektu, który go przydziela. Podczas kompilowania wersji programu, `DEBUG_NEW` jest rozpoznawana jako prosty **nowe** operację bez nazwy i wierszu numer informacje o pliku. W związku z tym opłaty są naliczane nie opłaty karnej szybkość w wydanej wersji programu.  
  
 Jeśli nie chcesz ponownie zapisać całego programu do użycia `DEBUG_NEW` zamiast **nowe**, można zdefiniować makro w plikach źródłowych:  
  
```  
#define new DEBUG_NEW  
```  
  
 Po wykonaniu [zrzutu obiektu](#BKMK_Taking_object_dumps), każdy obiekt przydzielony za pomocą `DEBUG_NEW` pokaże pliku i numer wiersza, gdzie została przydzielona, co pozwala na dokładne wskazanie źródła przecieków pamięci.  
  
 Wersja do debugowania programu MFC framework używa `DEBUG_NEW` automatycznie, ale nie w kodzie. Jeśli chcesz, aby zalety `DEBUG_NEW`, należy użyć `DEBUG_NEW` jawnie lub **#define nowe** jak pokazano powyżej.  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
### <a name="BKMK_Enabling_memory_diagnostics"></a> Włączenie diagnostyki pamięci  
 Przed użyciem funkcji diagnostyki pamięci, należy włączyć śledzenia diagnostycznego.  
  
 **Aby włączyć lub wyłączyć Diagnostyka pamięci**  
  
- Wywołaj funkcję globalnego [afxenablememorytracking —](https://msdn.microsoft.com/library/0a40e0c4-855d-46e2-9577-a8f2346f47db) Aby włączyć lub wyłączyć alokatora pamięci diagnostycznych. Ponieważ Diagnostyka pamięci są włączone domyślnie w bibliotece debugowania, zwykle użyjesz tej funkcji, aby tymczasowo wyłączyć je, zwiększa szybkość wykonywania programu, która ogranicza dane wyjściowe diagnostyki.  
  
  **Aby wybrać funkcje diagnostyczne dotyczące pamięci za pomocą afxmemdf —**  
  
- Jeśli chcesz bardziej precyzyjną kontrolę nad funkcji diagnostycznych pamięci, można selektywnie włączyć funkcje diagnostyczne poszczególnych pamięci włączać i wyłączać, ustawiając wartość zmiennej globalnej MFC [afxmemdf —](https://msdn.microsoft.com/library/cf117501-5446-4fce-81b3-f7194bc95086). Ta zmienna może mieć następujące wartości, określony przez Typ wyliczany **afxmemdf —** .  
  
  |Wartość|Opis|  
  |-----------|-----------------|  
  |**allocMemDF**|Włącz alokatora pamięci diagnostyczne (ustawienie domyślne).|  
  |**delayFreeMemDF**|Opóźnienie zwalnianie pamięci podczas wywoływania `delete` lub `free` dopóki program jest zamykany. Spowoduje to program, aby przydzielić maksymalną ilość pamięci.|  
  |**checkAlwaysMemDF**|Wywołaj [afxcheckmemory —](https://msdn.microsoft.com/library/4644da71-7d14-41dc-adc0-ee9558fd7a28) za każdym razem, gdy przydzielone lub zwolnienie pamięci.|  
  
   Te wartości mogą służyć w połączeniu za pomocą operacji logiczne OR, jak pokazano poniżej:  
  
  ```cpp  
  afxMemDF = allocMemDF | delayFreeMemDF | checkAlwaysMemDF;  
  ```  
  
  [W tym temacie](#BKMK_In_this_topic)  
  
### <a name="BKMK_Taking_memory_snapshots"></a> Tworzenie migawek pamięci  
  
1. Tworzenie [CMemoryState](https://msdn.microsoft.com/8fade6e9-c6fb-4b2a-8565-184a912d26d2) obiektu, a następnie wywołać [CMemoryState::Checkpoint](https://msdn.microsoft.com/library/b2d80fea-3d21-457e-816d-b035909bf21a) funkcja elementu członkowskiego. Spowoduje to utworzenie pierwszego migawkę pamięci.  
  
2. Po program wykonuje jego operacji alokacji i dezalokacji pamięci, należy utworzyć inny `CMemoryState` obiektu, a następnie wywołać `Checkpoint` dla tego obiektu. Pobiera to drugi migawki użycia pamięci.  
  
3. Utwórz trzecią `CMemoryState` obiektu, a następnie wywołać jej [CMemoryState::Difference](https://msdn.microsoft.com/library/aba69e2f-71dd-4255-99b5-3da2e56a0c9c) funkcji członkowskiej, podając jako argumenty dwóch poprzednich `CMemoryState` obiektów. Jeśli istnieje różnica pomiędzy stanami dwóch pamięci `Difference` funkcja zwraca wartość różną od zera. Oznacza to, że, niektóre bloki pamięci ma nie została wycofana.  
  
    Ten przykład przedstawia kod wygląda następująco:  
  
   ```  
   // Declare the variables needed  
   #ifdef _DEBUG  
       CMemoryState oldMemState, newMemState, diffMemState;  
       oldMemState.Checkpoint();  
   #endif  
  
       // Do your memory allocations and deallocations.  
       CString s("This is a frame variable");  
       // The next object is a heap object.  
      CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
  
   #ifdef _DEBUG  
       newMemState.Checkpoint();  
       if( diffMemState.Difference( oldMemState, newMemState ) )  
       {  
           TRACE( "Memory leaked!\n" );  
       }  
   #endif  
   ```  
  
    Należy zauważyć, że instrukcje sprawdzanie pamięci jest oddzielona przez `#ifdef` [_DEBUG](https://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a)/  **#endif** blokuje, dzięki czemu są one kompilowane tylko w wersji debugowania programu.  
  
    Teraz, gdy wiesz, występuje przeciek pamięci, można użyć innej funkcji członkowskiej, [CMemoryState::DumpStatistics](https://msdn.microsoft.com/library/90d5f281-b92f-4725-a996-23ab94cf4b5d) pomoże Ci go zlokalizować.  
  
   [W tym temacie](#BKMK_In_this_topic)  
  
### <a name="BKMK_Viewing_memory_statistics"></a> Wyświetlanie statystyk pamięci  
 [CMemoryState::Difference](https://msdn.microsoft.com/library/aba69e2f-71dd-4255-99b5-3da2e56a0c9c) funkcji analizuje dwa obiekty stanu pamięci i wykrywa wszystkie obiekty nie cofnięto przydziału ze stosu między Stanami początku i na końcu. Po migawki pamięci oraz ich porównanie przy użyciu `CMemoryState::Difference`, można wywołać [CMemoryState::DumpStatistics](https://msdn.microsoft.com/library/90d5f281-b92f-4725-a996-23ab94cf4b5d) można pobrać informacji o obiektach, które nie została wycofana.  
  
 Rozważmy następujący przykład:  
  
```  
if( diffMemState.Difference( oldMemState, newMemState ) )  
{  
   TRACE( "Memory leaked!\n" );  
   diffMemState.DumpStatistics();  
}  
```  
  
 Przykładowy zrzut z przykładu wygląda następująco:  
  
```  
0 bytes in 0 Free Blocks  
22 bytes in 1 Object Blocks  
45 bytes in 4 Non-Object Blocks  
Largest number used: 67 bytes  
Total allocations: 67 bytes  
```  
  
 Wolne bloki są bloków, których dezalokacji zostanie opóźnione, jeśli `afxMemDF` została ustawiona na `delayFreeMemDF`.  
  
 Bloki zwykły obiekt, w drugim wierszu, pozostają przydzielony na stosie.  
  
 Bloki non-object obejmują tablic i struktur przydzielonymi `new`. W tym przypadku cztery bloki niebędących obiektami zostały przydzielony na stosie, ale nie cofnięto przydziału.  
  
 `Largest number used` daje maksymalny rozmiar pamięci używane przez program w dowolnym momencie.  
  
 `Total allocations` zapewnia całkowitej ilości pamięci używanej przez program.  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
### <a name="BKMK_Taking_object_dumps"></a> Pobieranie obiektu zrzutów  
 W programie MFC można użyć [CMemoryState::DumpAllObjectsSince](https://msdn.microsoft.com/library/a7f89034-bca4-4786-88d5-1571a5425ab2) do porzucenia opis wszystkich obiektów na stosie, które nie została wycofana. `DumpAllObjectsSince` Zrzuca wszystkich obiektach przydzielonych od momentu ostatniego [CMemoryState::Checkpoint](https://msdn.microsoft.com/library/b2d80fea-3d21-457e-816d-b035909bf21a). Jeśli nie `Checkpoint` wywołanie miało miejsce, `DumpAllObjectsSince` Zrzuca wszystkie obiekty i nonobjects aktualnie w pamięci.  
  
> [!NOTE]
> Zanim użyjesz zrzucania obiektów MFC, należy najpierw [Włączanie śledzenia diagnostycznego](../debugger/mfc-debugging-techniques.md#BKMK_Enabling_memory_diagnostics).  
  
> [!NOTE]
> MFC automatycznie zrzuty ujawnione wszystkie obiekty, gdy program kończy działanie, dzięki czemu nie trzeba tworzyć kodu, zrzut obiektów w tym momencie.  
  
 Poniższy kod sprawdza przeciek pamięci przez porównywanie dwa stany pamięci i zrzuca wszystkie obiekty w przypadku wykrycia przeciek.  
  
```  
if( diffMemState.Difference( oldMemState, newMemState ) )  
{  
   TRACE( "Memory leaked!\n" );  
   diffMemState.DumpAllObjectsSince();  
}  
```  
  
 Zawartość zrzutu wyglądać następująco:  
  
```  
Dumping objects ->  
  
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long  
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long  
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long  
{2} a CPerson at $51A4  
  
Last Name: Smith  
First Name: Alan  
Phone #: 581-0215  
  
{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long  
```  
  
 Liczba w nawiasach klamrowych na początku większość linii określić kolejność, w którym zostały przydzielone obiekty. Najbardziej niedawno przydzielonego obiektu o najwyższym numerze i pojawia się w górnej części zrzutu.  
  
 Aby uzyskać maksymalną ilość informacji poza zrzutu obiektu, można zastąpić `Dump` funkcja elementu członkowskiego dowolnego `CObject`-pochodzi obiekt, aby dostosować zrzutu obiektu.  
  
 Można ustawić punkt przerwania w alokacji pamięci, ustawiając zmienną globalną `_afxBreakAlloc` do liczby wyświetlane w nawiasy klamrowe. Jeśli uruchomisz program debuger spowoduje przerwanie wykonywania przy tym alokacji. Następnie można sprawdzić stos wywołań, aby zobaczyć, jak program stało się do tego punktu.  
  
 Biblioteki wykonawczej C ma podobną funkcję [_CrtSetBreakAlloc](https://msdn.microsoft.com/library/33bfc6af-a9ea-405b-a29f-1c2d4d9880a1), użyć dla alokacji środowiska wykonawczego języka C.  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
#### <a name="BKMK_Interpreting_memory_dumps"></a> Interpretowanie pamięci zrzutów  
 Przyjrzyj się ten zrzut obiektu bardziej szczegółowo:  
  
```  
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long  
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long  
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long  
{2} a CPerson at $51A4  
  
Last Name: Smith  
First Name: Alan  
Phone #: 581-0215  
  
{1} strcore.cpp(80) : non-object block at $00A7516E, 25 bytes long  
```  
  
 Program, który wygenerował tego zrzutu ma tylko dwie jawne alokacji — na stosie, a drugi na stosie:  
  
```  
// Do your memory allocations and deallocations.  
CString s("This is a frame variable");  
// The next object is a heap object.  
CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
```  
  
 `CPerson` Konstruktor przyjmuje trzy argumenty, które są wskaźnikami do `char`, które są używane do zainicjowania `CString` zmiennych Członkowskich. W zrzutu pamięci możesz zobaczyć `CPerson` obiektu wraz z trzech bloków nonobject (3, 4 i 5). Przechowywania tych znaków dla `CString` zmienne Członkowskie i nie zostaną usunięte, gdy `CPerson` obiektu destruktor jest wywoływany.  
  
 Blok Numer 2 jest `CPerson` sam obiekt. `$51A4` reprezentuje adres bloku i następuje zawartości obiektu, który były generowane przez `CPerson`::`Dump` wywołanego [DumpAllObjectsSince](https://msdn.microsoft.com/library/a7f89034-bca4-4786-88d5-1571a5425ab2).  
  
 Można odgadnąć, z którymi skojarzony jest blok o numerze 1 `CString` zmiennej ramki ze względu na jego numer sekwencyjny i wielkości, która jest zgodna z liczbą znaków w ramce `CString` zmiennej. Zmienne przydzieleni do ramki są dealokowane automatycznie, gdy ramka wykracza poza zakres.  
  
 **Zmienne ramek**  
  
 Ogólnie rzecz biorąc należy nie obawiać się obiekty sterty skojarzone z zmienne ramek, ponieważ automatycznie są dealokowane gdy zmienne ramek wykraczają poza zakres. Aby uniknąć zaśmiecania swoje zrzuty diagnostycznych pamięci, należy umieścić wywołaniami `Checkpoint` aby były one poza zakresem zmienne ramek. Na przykład umieścić zakres w nawiasach poprzednim kodzie alokacji, jak pokazano poniżej:  
  
```  
oldMemState.Checkpoint();  
{  
    // Do your memory allocations and deallocations ...  
    CString s("This is a frame variable");  
    // The next object is a heap object.  
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
}  
newMemState.Checkpoint();  
```  
  
 W nawiasach kwadratowych zakresu w miejscu zrzut pamięci, w tym przykładzie jest następująca:  
  
```  
Dumping objects ->  
  
{5} strcore.cpp(80) : non-object block at $00A7521A, 9 bytes long  
{4} strcore.cpp(80) : non-object block at $00A751F8, 5 bytes long  
{3} strcore.cpp(80) : non-object block at $00A751D6, 6 bytes long  
{2} a CPerson at $51A4  
  
Last Name: Smith  
First Name: Alan  
Phone #: 581-0215  
```  
  
 **Alokacje nonobject**  
  
 Zwróć uwagę, że pewne przydziały są obiektami (takich jak `CPerson`), a inne nonobject alokacji. "Nonobject" są alokacji dla obiektów nie pochodzi od `CObject` lub alokacji C typów pierwotnych, takie jak `char`, `int`, lub **długie**. Jeśli **CObject —** klasy pochodnej przydziela dodatkowe miejsce, takie jak dla wewnętrznego buforów tych obiektów pokaże obiekt i nonobject alokacji.  
  
 **Zapobieganie przecieki pamięci**  
  
 Należy zauważyć w powyższym kodzie, blok pamięci skojarzone `CString` ramek zmienna została automatycznie wycofana i nie są wyświetlane jako przeciek pamięci. Automatyczne dezalokację skojarzonych reguł ustawiania zakresu zajmuje się większość przecieki pamięci, skojarzone z zmienne ramek.  
  
 Dla obiektów zaalokowanych na stosie jednak należy je jawnie usunąć obiektu, aby zapobiec przeciek pamięci. Aby wyczyścić ostatniego przeciek pamięci w poprzednim przykładzie, należy usunąć `CPerson` obiekt przydzielony na stosie, w następujący sposób:  
  
```  
{  
    // Do your memory allocations and deallocations.  
    CString s("This is a frame variable");  
    // The next object is a heap object.  
    CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
    delete p;  
}  
```  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
#### <a name="BKMK_Customizing_object_dumps"></a> Dostosowywanie obiektu zrzutów  
 Po utworzeniu klasy pochodnej klasy z [CObject](https://msdn.microsoft.com/library/95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a), możesz zastąpić `Dump` funkcja elementu członkowskiego, aby podać dodatkowe informacje, gdy używasz [DumpAllObjectsSince](https://msdn.microsoft.com/library/a7f89034-bca4-4786-88d5-1571a5425ab2) do obiektów zrzutu [Okno danych wyjściowych](../ide/reference/output-window.md).  
  
 `Dump` Funkcji zapisuje tekstową reprezentację wartości elementu członkowskiego obiektu zmienne kontekstowe zrzutu ([CDumpContext](https://msdn.microsoft.com/library/98c52b2d-14b5-48ed-b423-479a4d1c60fa)). Kontekst zrzutu jest podobne do strumienia we/wy. Możesz użyć operatora append ( **<<** ) do wysyłania danych do `CDumpContext`.  
  
 Gdy zastąpisz `Dump` funkcji, należy najpierw wywołać klasy bazowej wersję `Dump` do porzucenia zawartości obiektu klasy bazowej. Następnie wyprowadzić tekstowy opis i wartość każdej zmiennej składowej klasy pochodnej.  
  
 Deklaracja `Dump` funkcja wygląda następująco:  
  
```  
class CPerson : public CObject  
{  
public:  
#ifdef _DEBUG  
    virtual void Dump( CDumpContext& dc ) const;  
#endif  
  
    CString m_firstName;  
    CString m_lastName;  
    // And so on...  
};  
```  
  
 Ponieważ zrzucania obiektów ma sens tylko podczas debugowania programu deklaracji `Dump` funkcji jest oddzielona z **#ifdef _DEBUG / #endif** bloku.  
  
 W poniższym przykładzie `Dump` działać pierwszego wywołania `Dump` funkcji dla swojej klasy bazowej. Następnie zapisuje krótki opis każdego zmiennej elementu członkowskiego wraz z wartością elementu członkowskiego do strumienia diagnostyki.  
  
```  
#ifdef _DEBUG  
void CPerson::Dump( CDumpContext& dc ) const  
{  
    // Call the base class function first.  
    CObject::Dump( dc );  
  
    // Now do the stuff for our specific class.  
    dc << "last name: " << m_lastName << "\n"  
        << "first name: " << m_firstName << "\n";  
}  
#endif  
```  
  
 Należy podać `CDumpContext` argumentu, aby określić, gdzie dane wyjściowe zrzutu. Wersja do debugowania MFC dostarcza wstępnie zdefiniowanej `CDumpContext` obiektu o nazwie `afxDump` wysyłającą dane wyjściowe do debugera.  
  
```  
CPerson* pMyPerson = new CPerson;  
// Set some fields of the CPerson object.  
//...  
// Now dump the contents.  
#ifdef _DEBUG  
pMyPerson->Dump( afxDump );  
#endif  
```  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
## <a name="BKMK_Reducing_the_size_of_an_MFC_Debug_build"></a> Zmniejszenie rozmiaru kompilacji debugowania MFC  
 Informacje o debugowaniu dla dużych aplikacji MFC mogą zajmować dużo miejsca na dysku. Można użyć jednej z tych procedur, aby zmniejszyć rozmiar:  
  
1. Odbuduj biblioteki MFC, za pomocą [/z7, / zi, /ZI (Format informacji debugowania)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) opcji zamiast **/z7**. Te opcje kompilacji pliku bazy danych (PDB) jednego programu, który zawiera informacje o debugowaniu dla całej biblioteki, ograniczenie nadmiarowości i oszczędzanie miejsca.  
  
2. Ponownie skompiluj biblioteki MFC, bez informacji o debugowaniu (nie [/z7, / zi, /ZI (Format informacji debugowania)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) opcji). W przypadku braku informacji o debugowaniu uniemożliwi przy użyciu większość funkcji debugera w obrębie kodu biblioteki MFC, ale ponieważ biblioteki MFC są już dokładnie debugowany, nie może to być problem.  
  
3. Tworzenie aplikacji przy użyciu informacji o debugowaniu dla wybranych modułów tylko zgodnie z poniższym opisem.  
  
   [W tym temacie](#BKMK_In_this_topic)  
  
### <a name="BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules"></a> Tworzenie aplikacji MFC za pomocą informacji o debugowaniu dla wybranych modułów  
 Tworzenie modułów wybranych z biblioteki debugowania MFC umożliwia używanie przechodzenie krok po kroku i innych narzędzi debugowania w tych modułach. Ta procedura korzysta z obu Debuguj i zwolnij tryby pliku reguł programu make Visual C++, co wymaga zmiany opisane w następujące czynności (i również niezbędne wprowadzania "Kompiluj wszystko ponownie", gdy wymagana jest pełna kompilacja wydania).  
  
1. W Eksploratorze rozwiązań wybierz projekt.  
  
2. Z **widoku** menu, wybierz opcję **stron właściwości**.  
  
3. Najpierw należy utworzyć nową konfigurację projektu.  
  
   1. W  **\<Projekt > strony właściwości** okno dialogowe, kliknij przycisk **programu Configuration Manager** przycisku.  
  
   2. W [programu Configuration Manager, okno dialogowe](https://msdn.microsoft.com/fa182dca-282e-4ae5-bf37-e155344ca18b), Znajdź projekt w siatce. W **konfiguracji** kolumny wybierz  **\<nowy... >** .  
  
   3. W [nowa konfiguracja projektu, okno dialogowe](https://msdn.microsoft.com/cca616dc-05a6-4fe3-bdc1-40c72a66f2be), wpisz nazwę dla nowej konfiguracji, takich jak "Częściowe Debug", **Nazwa konfiguracji projektu** pole.  
  
   4. W **Skopiuj ustawienia z** wybierz **wersji**.  
  
   5. Kliknij przycisk **OK** zamknąć **nowa konfiguracja projektu**okno dialogowe.  
  
   6. Zamknij **programu Configuration Manager** okno dialogowe.  
  
4. Teraz będzie ustawić opcje dla całego projektu.  
  
   1. W **stron właściwości** dialogowego **właściwości konfiguracji** folderu, wybierz **ogólne** kategorii.  
  
   2. W siatce ustawienia projektu, rozwiń węzeł **domyślne wartości projektu** (jeśli jest to konieczne).  
  
   3. W obszarze **domyślne wartości projektu**, Znajdź **użycie MFC**. Bieżące ustawienie pojawia się w prawej kolumnie siatki. Kliknij pozycję bieżące ustawienia i zmień go na **Użyj MFC w bibliotece statycznej**.  
  
   4. W okienku po lewej stronie **strony właściwości** po otwarciu okna dialogowego **C/C++** i wybierz polecenie **preprocesora**. W siatce właściwości Znajdź **definicje preprocesora** i zastąp "NDEBUG" "_DEBUG".  
  
   5. W okienku po lewej stronie **strony właściwości** po otwarciu okna dialogowego **konsolidatora** i wybierz polecenie **dane wejściowe** kategorii. W siatce właściwości Znajdź **dodatkowe zależności**. W **dodatkowe zależności** ustawienie, wpisz "NAFXCWD. LIB"i"LIBCMT."  
  
   6. Kliknij przycisk **OK** nowych opcji kompilacji Zapisz i Zamknij **stron właściwości** okno dialogowe.  
  
5. Z **kompilacji** menu, wybierz opcję **odbudować**. Usuwa wszystkie informacje debugowania z moduły, ale nie ma wpływu na bibliotece MFC.  
  
6. Teraz należy dodać informacje o debugowaniu do wybranych modułów w aplikacji. Należy pamiętać, że można ustawić punkty przerwania i wykonywać inne funkcje debugera, tylko w modułach, które mają skompilowany według informacji o debugowaniu. Dla każdego pliku projektu, w której chcesz dołączyć informacje o debugowaniu, wykonaj następujące czynności:  
  
   1. W Eksploratorze rozwiązań Otwórz **pliki źródłowe** folder znajdujący się w projekcie.  
  
   2. Wybierz plik, aby ustawić informacje o debugowaniu dla.  
  
   3. Z **widoku** menu, wybierz opcję **stron właściwości**.  
  
   4. W **stron właściwości** dialogowego **ustawienia konfiguracji** folder, otwórz **C/C++** następnie wybierz folder **ogólne** Kategoria.  
  
   5. W siatce właściwości Znajdź **formatu informacji debugowania.**  
  
   6. Kliknij przycisk **formatu informacji debugowania** ustawienia i wybierz odpowiednią opcję (zazwyczaj **/zi**) dla informacji debugowania.  
  
   7. Jeśli używasz aplikacji generowanych przez Kreatora aplikacji lub mają prekompilowanych nagłówków, musisz wyłączyć wstępnie skompilowanych nagłówków, lub ponownie skompilować je przed skompilowaniem innych modułów. W przeciwnym razie ostrzeżenie C4650 i otrzymasz komunikat o błędzie C2855. Można wyłączyć wstępnie skompilowanych nagłówków, zmieniając **Utwórz bądź Użyj wstępnie skompilowanych nagłówków** w  **\<projektu > właściwości** okno dialogowe (**właściwości konfiguracji**  folderze **C/C++** podfolder, **prekompilowanych nagłówków** kategorii).  
  
7. Z **kompilacji** menu, wybierz opcję **kompilacji** odbudować pliki projektu, które są nieaktualne.  
  
   Jako alternatywa techniki opisanej w tym temacie, można użyć zewnętrznego pliku reguł programu make do definiowania poszczególne opcje dla każdego pliku. W takim przypadku należy połączyć się z biblioteki debugowania MFC, należy zdefiniować [_DEBUG](https://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a) flagi dla każdego modułu. Jeśli chcesz korzystać z bibliotek wersji MFC, należy zdefiniować NDEBUG. Aby uzyskać więcej informacji na temat pisania zewnętrznych plików reguł programu make, zobacz [odwołanie NMAKE](https://msdn.microsoft.com/library/0421104d-8b7b-4bf3-86c1-928d9b7c1a8c).  
  
   [W tym temacie](#BKMK_In_this_topic)  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie języka Visual C++](../debugger/debugging-native-code.md)
