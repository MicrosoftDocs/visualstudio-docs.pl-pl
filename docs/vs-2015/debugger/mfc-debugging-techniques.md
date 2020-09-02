---
title: Techniki debugowania MFC | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696904"
---
# <a name="mfc-debugging-techniques"></a>Techniki testowania MFC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W przypadku debugowania programu MFC te techniki debugowania mogą być przydatne.  
  
## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> W tym temacie  
 [AfxDebugBreak](#BKMK_AfxDebugBreak)  
  
 [Makro śledzenia](#BKMK_The_TRACE_macro)  
  
 [Wykrywanie przecieków pamięci w MFC](#BKMK_Memory_leak_detection_in_MFC)  
  
- [Śledzenie alokacji pamięci](#BKMK_Tracking_memory_allocations)  
  
- [Włączanie diagnostyki pamięci](#BKMK_Enabling_memory_diagnostics)  
  
- [Tworzenie migawek pamięci](#BKMK_Taking_memory_snapshots)  
  
- [Wyświetlanie statystyk pamięci](#BKMK_Viewing_memory_statistics)  
  
- [Pobieranie zrzutów obiektów](#BKMK_Taking_object_dumps)  
  
  - [Interpretowanie zrzutów pamięci](#BKMK_Interpreting_memory_dumps)  
  
  - [Dostosowywanie zrzutów obiektów](#BKMK_Customizing_object_dumps)  
  
    [Zmniejszanie rozmiaru kompilacji debugowania MFC](#BKMK_Reducing_the_size_of_an_MFC_Debug_build)  
  
  - [Kompilowanie aplikacji MFC z informacjami o debugowaniu dla wybranych modułów](#BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules)  
  
## <a name="afxdebugbreak"></a><a name="BKMK_AfxDebugBreak"></a> AfxDebugBreak  
 MFC udostępnia specjalną funkcję [AfxDebugBreak](https://msdn.microsoft.com/library/c4cd79b9-9327-4db5-a9d6-c4004a92aa30) dla twardych punktów przerwania kodowania w kodzie źródłowym:  
  
```  
AfxDebugBreak( );  
  
```  
  
 Na platformach firmy Intel program `AfxDebugBreak` tworzy Poniższy kod, który jest dzielony w kodzie źródłowym, a nie w kodzie jądra:  
  
```  
_asm int 3  
```  
  
 Na innych platformach, `AfxDebugBreak` tylko wywołania `DebugBreak` .  
  
 Pamiętaj, aby usunąć `AfxDebugBreak` instrukcje, gdy tworzysz kompilację wydania lub Użyj `#ifdef _DEBUG` , aby je obsłużyć.  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
## <a name="the-trace-macro"></a><a name="BKMK_The_TRACE_macro"></a> Makro śledzenia  
 Aby wyświetlić komunikaty z programu w [oknie danych wyjściowych](../ide/reference/output-window.md)debugera, można użyć makra [ATLTRACE](https://msdn.microsoft.com/library/c796baa5-e2b9-4814-a27d-d800590b102e) lub makro [śledzenia](https://msdn.microsoft.com/library/7b6f42d8-b55a-4bba-ab04-c46251778e6f) MFC. Podobnie jak [potwierdzenia](../debugger/c-cpp-assertions.md), makra śledzenia są aktywne tylko w wersji debugowanej programu i znikają po skompilowaniu w wersji wydania.  
  
 W poniższych przykładach pokazano, jak można użyć makra **śledzenia** . `printf`Na przykład makro **śledzenia** może obsłużyć wiele argumentów.  
  
```  
int x = 1;  
int y = 16;  
float z = 32.0;  
TRACE( "This is a TRACE statement\n" );  
  
TRACE( "The value of x is %d\n", x );  
  
TRACE( "x = %d and y = %d\n", x, y );  
  
TRACE( "x = %d and y = %x and z = %f\n", x, y, z );  
```  
  
 Makro śledzenia odpowiednio obsługuje parametry char * i wchar_t \* . W poniższych przykładach pokazano użycie makra śledzenia wraz z różnymi typami parametrów ciągu.  
  
```  
TRACE( "This is a test of the TRACE macro that uses an ANSI string: %s %d\n", "The number is:", 2);  
  
TRACE( L"This is a test of the TRACE macro that uses a UNICODE string: %s %d\n", L"The number is:", 2);  
  
TRACE( _T("This is a test of the TRACE macro that uses a TCHAR string: %s %d\n"), _T("The number is:"), 2);  
  
```  
  
 Aby uzyskać więcej informacji na temat makra **śledzenia** , zobacz [usługi diagnostyczne](https://msdn.microsoft.com/library/8d78454f-9fae-49c2-88c9-d3fabd5393e8).  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
## <a name="detecting-memory-leaks-in-mfc"></a><a name="BKMK_Memory_leak_detection_in_MFC"></a> Wykrywanie przecieków pamięci w MFC  
 MFC udostępnia klasy i funkcje do wykrywania pamięci, która jest przydzielna, ale nigdy nie została cofnięta.  
  
### <a name="tracking-memory-allocations"></a><a name="BKMK_Tracking_memory_allocations"></a> Śledzenie alokacji pamięci  
 W MFC można użyć makra [DEBUG_NEW](https://msdn.microsoft.com/library/9b379344-4093-4bec-a3eb-e0d8a63ada9d) zamiast operatora **New** , aby ułatwić lokalizowanie przecieków pamięci. W wersji debugowej programu Program `DEBUG_NEW` śledzi nazwę pliku i numer wiersza dla każdego przydzielonego obiektu. Podczas kompilowania wersji programu Program `DEBUG_NEW` rozwiązuje prostą **nową** operację bez informacji o nazwie pliku i numerze wiersza. W ten sposób płatność nie jest kara w wydanej wersji programu.  
  
 Jeśli nie chcesz ponownie pisać całego programu w celu użycia zamiast `DEBUG_NEW` **nowego**, możesz zdefiniować to makro w plikach źródłowych:  
  
```  
#define new DEBUG_NEW  
```  
  
 Gdy wykonujesz [zrzut obiektu](#BKMK_Taking_object_dumps), każdy obiekt przydzielony przy użyciu `DEBUG_NEW` będzie pokazywał plik i numer wiersza, w którym został przydzielony, co pozwala na lokalizowanie źródeł przecieków pamięci.  
  
 Wersja do debugowania środowiska MFC jest automatycznie stosowana `DEBUG_NEW` , ale kod nie. Jeśli potrzebujesz korzyści z programu `DEBUG_NEW` , musisz użyć `DEBUG_NEW` jawnie lub **#define nowe** , jak pokazano powyżej.  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
### <a name="enabling-memory-diagnostics"></a><a name="BKMK_Enabling_memory_diagnostics"></a> Włączanie diagnostyki pamięci  
 Aby można było korzystać z funkcji diagnostyki pamięci, należy włączyć śledzenie diagnostyki.  
  
 **Aby włączyć lub wyłączyć diagnostykę pamięci**  
  
- Wywołaj funkcję globalną [AfxEnableMemoryTracking](https://msdn.microsoft.com/library/0a40e0c4-855d-46e2-9577-a8f2346f47db) , aby włączyć lub wyłączyć Alokator pamięci diagnostyki. Ponieważ Diagnostyka pamięci jest domyślnie włączona w bibliotece debugowania, zazwyczaj ta funkcja jest używana do tymczasowego ich wyłączenia, co zwiększa szybkość wykonywania programu i zmniejsza liczbę danych wyjściowych diagnostycznych.  
  
  **Aby wybrać określone funkcje diagnostyki pamięci z afxMemDF**  
  
- Jeśli potrzebujesz bardziej precyzyjnej kontroli nad funkcjami diagnostyki pamięci, możesz wybiórczo włączać i wyłączać poszczególne funkcje diagnostyki pamięci przez ustawienie wartości zmiennej globalnej MFC [afxMemDF](https://msdn.microsoft.com/library/cf117501-5446-4fce-81b3-f7194bc95086). Ta zmienna może mieć następujące wartości określone przez Wyliczenie typu **afxMemDF**.  
  
  |Wartość|Opis|  
  |-----------|-----------------|  
  |**allocMemDF**|Włącz program przydzielania pamięci diagnostycznej (domyślnie).|  
  |**delayFreeMemDF**|Opóźnij zwalnianie pamięci podczas wywoływania `delete` lub `free` do zakończenia działania programu. Spowoduje to przydzielenie przez program maksymalnej możliwej ilości pamięci.|  
  |**checkAlwaysMemDF**|Wywołaj [AfxCheckMemory](https://msdn.microsoft.com/library/4644da71-7d14-41dc-adc0-ee9558fd7a28) za każdym razem, gdy pamięć jest alokowana lub zwalniana.|  
  
   Te wartości mogą być używane w połączeniu przez wykonywanie operacji logicznej lub, jak pokazano poniżej:  
  
  ```cpp  
  afxMemDF = allocMemDF | delayFreeMemDF | checkAlwaysMemDF;  
  ```  
  
  [W tym temacie](#BKMK_In_this_topic)  
  
### <a name="taking-memory-snapshots"></a><a name="BKMK_Taking_memory_snapshots"></a> Tworzenie migawek pamięci  
  
1. Utwórz obiekt [CMemoryState](https://msdn.microsoft.com/8fade6e9-c6fb-4b2a-8565-184a912d26d2) i wywołaj funkcję członkowską [CMemoryState:: Checkpoint](https://msdn.microsoft.com/library/b2d80fea-3d21-457e-816d-b035909bf21a) . Spowoduje to utworzenie pierwszej migawki pamięci.  
  
2. Gdy program wykona operacje alokacji pamięci i cofania alokacji, Utwórz inny `CMemoryState` obiekt i Wywołaj `Checkpoint` dla tego obiektu. Spowoduje to pobranie drugiej migawki użycia pamięci.  
  
3. Utwórz trzeci `CMemoryState` obiekt i Wywołaj jego [CMemoryState::D ifference](https://msdn.microsoft.com/library/aba69e2f-71dd-4255-99b5-3da2e56a0c9c) funkcja członkowska, dostarczając jako argumenty dwa poprzednie `CMemoryState` obiekty. W przypadku różnic między Stanami dwóch pamięci `Difference` Funkcja zwraca wartość różną od zera. Oznacza to, że niektóre bloki pamięci nie zostały cofnięte.  
  
    Ten przykład pokazuje, jak wygląda kod:  
  
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
  
    Należy zauważyć, że instrukcje sprawdzania pamięci są przedzielone przez `#ifdef` [_DEBUG](https://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a) /  **#endif** bloków, aby były kompilowane tylko w wersjach debugowania programu.  
  
    Teraz, gdy już istnieje przeciek pamięci, możesz użyć innej funkcji członkowskiej, [CMemoryState::D umpstatistics](https://msdn.microsoft.com/library/90d5f281-b92f-4725-a996-23ab94cf4b5d) , która ułatwi jego znalezienie.  
  
   [W tym temacie](#BKMK_In_this_topic)  
  
### <a name="viewing-memory-statistics"></a><a name="BKMK_Viewing_memory_statistics"></a> Wyświetlanie statystyk pamięci  
 Funkcja [CMemoryState::D ifference](https://msdn.microsoft.com/library/aba69e2f-71dd-4255-99b5-3da2e56a0c9c) przegląda dwa obiekty stanu pamięci i wykrywa wszystkie obiekty, które nie zostały cofnięte z sterty między Stanami początkowymi i końcowymi. Po wykonaniu migawek pamięci i porównaniu z nimi przy użyciu programu `CMemoryState::Difference` można wywołać [CMemoryState::D umpstatistics](https://msdn.microsoft.com/library/90d5f281-b92f-4725-a996-23ab94cf4b5d) w celu uzyskania informacji o obiektach, które nie zostały cofnięte.  
  
 Rozpatrzmy następujący przykład:  
  
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
  
 Bloki bezpłatne to bloki, których cofanie alokacji jest opóźnione `afxMemDF` , jeśli ustawiono wartość `delayFreeMemDF` .  
  
 Zwykłe bloki obiektów, pokazane w drugim wierszu, pozostają przydzieloną na stercie.  
  
 Bloki niebędące obiektami zawierają tablice i struktury przydzielono z `new` . W takim przypadku cztery bloki nie będące obiektami są przydzielane na stercie, ale nie zostały cofnięte.  
  
 `Largest number used` zapewnia maksymalną ilość pamięci używanej przez program w dowolnym momencie.  
  
 `Total allocations` podaje łączną ilość pamięci używanej przez program.  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
### <a name="taking-object-dumps"></a><a name="BKMK_Taking_object_dumps"></a> Pobieranie zrzutów obiektów  
 W programie MFC można użyć [CMemoryState::D umpallobjectssince](https://msdn.microsoft.com/library/a7f89034-bca4-4786-88d5-1571a5425ab2) do zrzutu opisu wszystkich obiektów na stercie, które nie zostały cofnięte. `DumpAllObjectsSince` Zrzuca wszystkie obiekty przydzielono od momentu ostatniego [CMemoryState:: Checkpoint](https://msdn.microsoft.com/library/b2d80fea-3d21-457e-816d-b035909bf21a). Jeśli `Checkpoint` wywołanie nie zostało wykonane, program `DumpAllObjectsSince` zrzuca wszystkie obiekty i elementy inne niż aktualnie znajdujące się w pamięci.  
  
> [!NOTE]
> Aby można było używać zatopienia obiektu MFC, należy [włączyć śledzenie diagnostyki](../debugger/mfc-debugging-techniques.md#BKMK_Enabling_memory_diagnostics).  
  
> [!NOTE]
> MFC automatycznie Zrzuca wszystkie wycieki obiektów po zakończeniu działania programu, dzięki czemu nie trzeba tworzyć kodu w celu zrzutu obiektów w tym momencie.  
  
 Poniższy kod testuje przeciek pamięci, porównując dwa stany pamięci i zrzuca wszystkie obiekty w przypadku wykrycia wycieku.  
  
```  
if( diffMemState.Difference( oldMemState, newMemState ) )  
{  
   TRACE( "Memory leaked!\n" );  
   diffMemState.DumpAllObjectsSince();  
}  
```  
  
 Zawartość zrzutu wygląda następująco:  
  
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
  
 Liczby w nawiasach klamrowych na początku większości wierszy określają kolejność, w jakiej obiekty zostały przydzieloną. Ostatnio przydzielony obiekt ma największą liczbę i pojawia się u góry zrzutu.  
  
 Aby uzyskać maksymalną ilość informacji z zrzutu obiektu, można zastąpić `Dump` funkcję członkowską dowolnego `CObject` pochodnego obiektu, aby dostosować zrzut obiektu.  
  
 Możesz ustawić punkt przerwania dla określonego przydziału pamięci, ustawiając zmienną globalną `_afxBreakAlloc` na liczbę pokazaną w nawiasach klamrowych. Po ponownym uruchomieniu programu debuger spowoduje przerwanie wykonywania, gdy ta alokacja zostanie wykonana. Następnie można przyjrzeć się stosowi wywołań, aby zobaczyć, jak Twój program uzyskał do tego punktu.  
  
 Biblioteka wykonawcza C ma podobną funkcję, [_CrtSetBreakAlloc](https://msdn.microsoft.com/library/33bfc6af-a9ea-405b-a29f-1c2d4d9880a1), której można użyć do przydziałów czasu wykonywania w języku c.  
  
 [W tym temacie](#BKMK_In_this_topic)  
  
#### <a name="interpreting-memory-dumps"></a><a name="BKMK_Interpreting_memory_dumps"></a> Interpretowanie zrzutów pamięci  
 Poszukaj zrzutu obiektu bardziej szczegółowo:  
  
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
  
 Program, który wygenerował ten zrzut miał tylko dwa Jawne alokacje — jeden na stosie i jeden na stosie:  
  
```  
// Do your memory allocations and deallocations.  
CString s("This is a frame variable");  
// The next object is a heap object.  
CPerson* p = new CPerson( "Smith", "Alan", "581-0215" );  
```  
  
 `CPerson`Konstruktor przyjmuje trzy argumenty, które są wskaźnikami do `char` , które są używane do inicjowania `CString` zmiennych składowych. W zrzucie pamięci można zobaczyć `CPerson` obiekt wraz z trzema blokami nieobiektowymi (3, 4 i 5). Zawierają one znaki dla `CString` zmiennych składowych i nie zostaną usunięte po `CPerson` wywołaniu destruktora obiektu.  
  
 Numer bloku 2 jest `CPerson` samym obiektem. `$51A4` reprezentuje adres bloku i następuje przez zawartość obiektu, który był wyprowadzany przez `CPerson` :: `Dump` po wywołaniu przez [DumpAllObjectsSince](https://msdn.microsoft.com/library/a7f89034-bca4-4786-88d5-1571a5425ab2).  
  
 Można odgadnąć, że blok o numerze 1 jest skojarzony ze `CString` zmienną ramki ze względu na numer i rozmiar sekwencji, który odpowiada liczbie znaków w `CString` zmiennej ramki. Zmienne przyłączone do ramki są automatycznie cofane, gdy ramka wykracza poza zakres.  
  
 **Zmienne ramek**  
  
 Ogólnie rzecz biorąc nie należy martwić się o obiekty sterty skojarzone ze zmiennymi ramek, ponieważ są one automatycznie cofane, gdy zmienne ramek wykraczają poza zakres. Aby uniknąć braku bałaganu w zrzutach diagnostycznych pamięci, należy umieścić wywołania w `Checkpoint` taki sposób, aby znajdowały się poza zakresem zmiennych ramek. Na przykład Umieść nawiasy zakresowe wokół poprzedniego kodu alokacji, jak pokazano poniżej:  
  
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
  
 W przypadku nawiasów zakresowych zrzut pamięci dla tego przykładu jest następujący:  
  
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
  
 **Alokacje nieobiektowe**  
  
 Należy zauważyć, że niektóre alokacje to obiekty (takie jak `CPerson` ), a niektóre nie są alokacjami obiektów. "Alokacje nieobiektowe" to alokacje obiektów, które nie pochodzą z `CObject` ani alokacji typów pierwotnych C, takich jak `char` , `int` , lub **Long**. Jeśli klasa pochodna **CObject**alokuje dodatkowe miejsce, na przykład w przypadku buforów wewnętrznych, te obiekty będą pokazywały zarówno alokacje obiektów, jak i innych obiektów.  
  
 **Zapobieganie przeciekom pamięci**  
  
 Zwróć uwagę na kod, że blok pamięci skojarzony ze `CString` zmienną ramki został cofnięty automatycznie i nie jest wyświetlany jako przeciek pamięci. Automatyczne cofanie alokacji skojarzone z regułami określania zakresu uwzględnia większość przecieków pamięci skojarzonych ze zmiennymi ramek.  
  
 W przypadku obiektów przyznanych na stercie należy jednak jawnie usunąć obiekt, aby zapobiec wyciekowi pamięci. Aby wyczyścić ostatni przeciek pamięci w poprzednim przykładzie, Usuń `CPerson` obiekt przydzielony na stercie w następujący sposób:  
  
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
  
#### <a name="customizing-object-dumps"></a><a name="BKMK_Customizing_object_dumps"></a> Dostosowywanie zrzutów obiektów  
 Podczas wyprowadzania klasy z [CObject](https://msdn.microsoft.com/library/95e9acd3-d9eb-4ac0-b52b-ca4a501a7a3a)można zastąpić `Dump` funkcję członkowską, aby podać dodatkowe informacje w przypadku używania [DumpAllObjectsSince](https://msdn.microsoft.com/library/a7f89034-bca4-4786-88d5-1571a5425ab2) do zrzutu obiektów do [okna danych wyjściowych](../ide/reference/output-window.md).  
  
 `Dump`Funkcja zapisuje tekstową reprezentację zmiennych składowych obiektu w kontekście zrzutu ([CDumpContext](https://msdn.microsoft.com/library/98c52b2d-14b5-48ed-b423-479a4d1c60fa)). Kontekst zrzutu jest podobny do strumienia we/wy. Do wysyłania danych do programu można użyć operatora dołączania ( **<<** ) `CDumpContext` .  
  
 Podczas przesłonięcia `Dump` funkcji należy najpierw wywołać wersję klasy bazowej, `Dump` aby zrzucić zawartość obiektu klasy bazowej. Następnie wyprowadza tekstowy opis i wartość dla każdej zmiennej składowej klasy pochodnej.  
  
 Deklaracja `Dump` funkcji wygląda następująco:  
  
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
  
 Ponieważ zatopienie obiektu ma sens tylko w przypadku debugowania programu, deklaracja `Dump` funkcji jest przenawiasem klamrowym **#ifdef _DEBUG/#endif** .  
  
 W poniższym przykładzie `Dump` Funkcja najpierw wywołuje `Dump` funkcję dla swojej klasy bazowej. Następnie zapisuje Krótki opis każdej zmiennej składowej wraz z wartością elementu członkowskiego w strumieniu diagnostyki.  
  
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
  
 Musisz podać argument, `CDumpContext` Aby określić miejsce wyjścia zrzutu. Wersja debugowania MFC dostarcza wstępnie zdefiniowany `CDumpContext` obiekt o nazwie `afxDump` , który wysyła dane wyjściowe do debugera.  
  
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
  
## <a name="reducing-the-size-of-an-mfc-debug-build"></a><a name="BKMK_Reducing_the_size_of_an_MFC_Debug_build"></a> Zmniejszanie rozmiaru kompilacji debugowania MFC  
 Informacje o debugowaniu dla dużej aplikacji MFC mogą zająć dużo miejsca na dysku. Aby zmniejszyć rozmiar, można użyć jednej z następujących procedur:  
  
1. Ponownie skompiluj biblioteki MFC przy użyciu opcji [/Z7,/Zi,/ZI (Debug Information Format)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) zamiast **/Z7**. Te opcje tworzą plik bazy danych pojedynczego programu (PDB), który zawiera informacje o debugowaniu dla całej biblioteki, zmniejszając nadmiarowość i oszczędność miejsca.  
  
2. Skompiluj ponownie biblioteki MFC bez informacji o debugowaniu (brak [/Z7,/Zi,/ZI (format informacji o debugowaniu)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) . W takim przypadku brak informacji debugowania uniemożliwi korzystanie z większości obiektów debugera w kodzie biblioteki MFC, ale ponieważ biblioteki MFC są już dokładnie debugowane, może to nie być problem.  
  
3. Utwórz własną aplikację z informacjami o debugowaniu dla wybranych modułów, tak jak opisano poniżej.  
  
   [W tym temacie](#BKMK_In_this_topic)  
  
### <a name="building-an-mfc-app-with-debug-information-for-selected-modules"></a><a name="BKMK_Building_an_MFC_app_with_debug_information_for_selected_modules"></a> Kompilowanie aplikacji MFC z informacjami o debugowaniu dla wybranych modułów  
 Kompilowanie wybranych modułów przy użyciu bibliotek debugowania MFC umożliwia korzystanie z funkcji krokowe i innych obiektów debugowania w tych modułach. Ta procedura korzysta z trybów debugowania i wydawania Visual C++ pliku reguł programu make, co wymaga wprowadzenia zmian opisanych w poniższych krokach (a także w przypadku konieczności przeprowadzenia ponownego kompilowania wszystkich), gdy wymagana jest pełna kompilacja wydania).  
  
1. W Eksplorator rozwiązań wybierz projekt.  
  
2. Z menu **Widok** wybierz polecenie **strony właściwości**.  
  
3. Najpierw utworzysz nową konfigurację projektu.  
  
   1. W oknie dialogowym ** \<Project> strony właściwości** kliknij przycisk **Configuration Manager** .  
  
   2. W [oknie dialogowym Configuration Manager](https://msdn.microsoft.com/fa182dca-282e-4ae5-bf37-e155344ca18b)Znajdź swój projekt w siatce. W kolumnie **Konfiguracja** wybierz opcję **\<New...>** .  
  
   3. W [oknie dialogowym Konfiguracja nowego projektu](https://msdn.microsoft.com/cca616dc-05a6-4fe3-bdc1-40c72a66f2be)wpisz nazwę nowej konfiguracji, na przykład "Debugowanie częściowe" w polu **nazwa konfiguracji projektu** .  
  
   4. Na liście **Kopiuj ustawienia z** wybierz pozycję **Zwolnij**.  
  
   5. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Konfiguracja nowego projektu**.  
  
   6. Zamknij okno dialogowe **Configuration Manager** .  
  
4. Teraz można ustawić opcje dla całego projektu.  
  
   1. W oknie dialogowym **strony właściwości** w folderze **Właściwości konfiguracji** wybierz kategorię **Ogólne** .  
  
   2. W siatce ustawienia projektu rozwiń pozycję **wartości domyślne projektu** (w razie potrzeby).  
  
   3. W obszarze **wartości domyślne projektu**Znajdź **użycie MFC**. Bieżące ustawienie pojawia się w prawej kolumnie siatki. Kliknij bieżące ustawienie i zmień je tak, aby **używało MFC w bibliotece statycznej**.  
  
   4. W lewym okienku okna dialogowego **strony właściwości** Otwórz folder **C/C++** i wybierz **preprocesor**. W siatce właściwości Znajdź **Definicje preprocesora** i Zastąp ciąg "NDEBUG" "_DEBUG".  
  
   5. W lewym okienku okna dialogowego **strony właściwości** Otwórz folder **konsolidatora** i wybierz kategorię **dane wejściowe** . W siatce właściwości Znajdź **dodatkowe zależności**. W ustawieniu **dodatkowe zależności** wpisz "NAFXCWD. LIB "i" LIBCMT ".  
  
   6. Kliknij przycisk **OK** , aby zapisać nowe opcje kompilacji i zamknąć okno dialogowe **strony właściwości** .  
  
5. Z menu **kompilacja** wybierz opcję **Kompiluj ponownie**. Spowoduje to usunięcie wszystkich informacji debugowania z modułów, ale nie ma wpływu na bibliotekę MFC.  
  
6. Teraz musisz dodać informacje debugowania z powrotem do wybranych modułów w aplikacji. Należy pamiętać, że można ustawić punkty przerwania i wykonać inne funkcje debugera tylko w modułach, które zostały skompilowane z informacjami o debugowaniu. Dla każdego pliku projektu, w którym chcesz dołączyć informacje debugowania, wykonaj następujące czynności:  
  
   1. W Eksplorator rozwiązań otwórz folder **pliki źródłowe** znajdujący się w ramach projektu.  
  
   2. Wybierz plik, dla którego chcesz ustawić informacje o debugowaniu.  
  
   3. Z menu **Widok** wybierz polecenie **strony właściwości**.  
  
   4. W oknie dialogowym **strony właściwości** w folderze **Ustawienia konfiguracji** Otwórz folder **C/C++** , a następnie wybierz kategorię **Ogólne** .  
  
   5. W siatce właściwości Znajdź **Format informacji o debugowaniu.**  
  
   6. Kliknij ustawienia **formatu informacji debugowania** i wybierz żądaną opcję (zazwyczaj **/Zi**), aby uzyskać informacje o debugowaniu.  
  
   7. Jeśli używasz aplikacji wygenerowanej przez Kreatora aplikacji lub mającej prekompilowane nagłówki, musisz wyłączyć prekompilowane nagłówki lub skompilować je ponownie przed skompilowaniem innych modułów. W przeciwnym razie pojawi się ostrzeżenie C4650 i komunikat o błędzie C2855. Można wyłączyć prekompilowane nagłówki, zmieniając ustawienie **Utwórz/Użyj prekompilowanych nagłówków** w oknie dialogowym ** \<Project> Właściwości** (folder**Właściwości konfiguracji** , podfolder **C/C++** , Kategoria **prekompilowanych nagłówków** ).  
  
7. Z menu **kompilacja** wybierz opcję **Kompiluj** , aby ponownie skompilować pliki projektu, które są nieaktualne.  
  
   Jako alternatywę dla techniki opisanej w tym temacie można użyć zewnętrznego pliku reguł programu make, aby zdefiniować poszczególne opcje dla każdego z nich. W takim przypadku aby połączyć z bibliotekami debugowania MFC, należy zdefiniować flagę [_DEBUG](https://msdn.microsoft.com/library/a9901568-4846-4731-a404-399d947e2e7a) dla każdego modułu. Jeśli chcesz używać bibliotek wersji MFC, musisz zdefiniować NDEBUG. Aby uzyskać więcej informacji na temat pisania zewnętrznych plików reguł programu make, zobacz [odwołanie NMAKE](https://msdn.microsoft.com/library/0421104d-8b7b-4bf3-86c1-928d9b7c1a8c).  
  
   [W tym temacie](#BKMK_In_this_topic)  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie Visual C++](../debugger/debugging-native-code.md)
