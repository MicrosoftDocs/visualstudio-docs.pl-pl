---
title: Określ symboli (.pdb) i pliki w debugerze źródłowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Debugger.Native
- VS.ToolsOptionsPages.Debugger.Symbols
- vs.debug.options.Native
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- source code
- .dbg files
- source code, managing
- symbols, managing
- .pdb files
- dbg files
- pdb files
- debugger
ms.assetid: 1105e169-5272-4e7c-b3e7-cda1b7798a6b
caps.latest.revision: 36
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b8fc64588962c7f3adaa05eb33543802672b57e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53931218"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger"></a>Określanie plików symboli (.pdb) i plików źródłowych w debugerze programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Plik bazy danych programu (.pdb), nazywany także plikiem symboli, mapuje identyfikatory, które tworzysz w plikach źródłowych dla klas, metod i innego kodu, na identyfikatory które są używane w skompilowanych plikach wykonywalnych projektu. Plik .pdb mapuje również instrukcje zawarte w kodzie źródłowym na instrukcje wykonania w plikach wykonywalnych. Debuger używa tych informacji do określenia dwóch informacji o znaczeniu kluczowym: plik źródłowy i numer wiersza, które są wyświetlane w programie Visual Studio IDE oraz lokalizacja w pliku wykonywalnym, w której program się zatrzyma, jeśli ustawisz punkt przerwania. Plik symboli zawiera także oryginalną lokalizację plików źródłowych i opcjonalnie lokalizację serwera źródeł, z którego mogą być pobierane pliki źródłowe.

 Podczas debugowania projektu w programie Visual Studio IDE debuger wie, domyślna lokalizacja dla plików .pdb i źródła, w kodzie. Jeśli chcesz debugować kod poza kodem źródłowym projektu, taki jak kod systemu Windows lub kod zewnętrznych aplikacji wywoływanych w projekcie, należy określić lokalizację pliku .pdb (i opcjonalnie plików źródłowych kodu zewnętrznego), i te pliki muszą dokładnie odpowiadać kompilacji plików wykonywalnych.

 Przed Visual Studio 2012 podczas debugowania kodu zarządzanego na urządzeniu zdalnym niezbędna do umieszczenia plików symboli na komputerze zdalnym. Obecnie taka ewentualność nie zachodzi. Wszystkie pliki symboli muszą znajdować się na komputerze lokalnym lub w lokalizacji określonej w **narzędzia / Opcje / Debugowanie / symbole** strony.

##  <a name="BKMK_Find_symbol___pdb__files"></a> Gdzie debuger wyszukuje pliki .pdb

1.  Lokalizacja określona w pliku DLL lub pliku wykonywalnym.

     (Domyślnie, jeśli skompilowałeś bibliotekę DLL lub plik wykonywalny na swoim komputerze, konsolidator umieszcza pełną ścieżkę i nazwę skojarzonego pliku .pdb wewnątrz pliku DLL lub pliku wykonywalnego. Debuger najpierw sprawdza, czy plik symboli znajduje się w lokalizacji określonej w pliku DLL lub pliku wykonywalnym. Jest to pomocne, ponieważ zawsze masz dostępne symbole dla kodu, który skompilowałeś na swoim komputerze.)

2.  Pliki .pdb, które mogą się znajdować w tym samym folderze, co plik DLL lub plik wykonywalny.

3.  Wszystkie lokalne foldery pamięci podręcznej symboli.

4.  Wszelkie sieci, Internet lub określone lokalne serwery symboli i lokalizacje, takie jak serwer symboli Microsoft, jeśli są włączone.

###  <a name="BKMK_Why_do_symbol_files_need_to_exactly_match_the_executable_files_"></a> Dlaczego pliki symboli muszą dokładnie odpowiadać plikom wykonywalnym?
 Debuger będzie ładował tylko plik .pdb dla pliku wykonywalnego, który dokładnie pasuje do pliku .pdb, który z kolei został utworzony podczas kompilowania pliku wykonywalnego (czyli .pdb musi być plikiem oryginalnym lub kopią oryginalnego pliku .pdb). Ponieważ kompilator jest zoptymalizowany pod kątem szybkości kompilacji, oprócz swojego głównego zadania utworzenia prawidłowego i efektywnego kodu, można zmienić układ pliku wykonywalnego, nawet jeśli nie zmienił się sam kod. Aby uzyskać więcej informacji, zobacz [Dlaczego Visual Studio wymaga, aby debuger symbol dokładnej zgodności plików plików binarnych, które zostały skompilowane?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/).

###  <a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a> Określ lokalizacje symboli i zachowanie ładowania
 Podczas debugowania projektu w VS IDE, debuger automatycznie ładuje pliki symboli, które znajdują się w katalogu projektu. Możesz określić alternatywne ścieżki wyszukiwania i serwery symboli dla Microsoft, Windows lub składników innych firm w **narzędzia / Opcje / Debugowanie / symbole**. Można również określić określone moduły, które mają debuger ma automatycznie ładować symbole. Można też następnie zmienić te ustawienia ręcznie podczas aktywnego debugowania.

1. W programie Visual Studio, otwórz **narzędzia / Opcje / Debugowanie / symbole** strony.

    ![Narzędzia &#45; opcje &#45; debugowanie &#45; strony symbole](../debugger/media/dbg-tools-options-symbols.png "DBG_Tools_Options_Symbols")

2. Wybierz folder ![narzędzia&#47; opcje&#47; debugowanie&#47;ikonę folderu symbole](../debugger/media/dbg-tools-options-foldersicon.png "DBG_Tools_Options_FoldersIcon") ikony. Tekst edytowalny pojawia się w **symboli (.pdb) lokalizacji** pole.

3. Wpisz adres URL lub ścieżkę katalogu serwera symboli lub lokalizację symboli. Uzupełnianie instrukcji pomaga w znalezieniu właściwego formatu.

4. Aby zwiększyć symbolu wydajność ładowania, wpisz ścieżkę do katalogu lokalnego, gdzie symbole mogą być kopiowane przez serwery symboli w **pamięci podręcznej symboli w tym katalogu** polu, które symbole mogą być kopiowane do katalogu lokalnego.

   > [!NOTE]
   >  Pamięci podręcznej symboli nie należy umieszczać w folderze chronionym (na przykład C:\Windows lub jednym z jego podfolderów). Zamiast tego użyj folderu przeznaczonego do odczytu i zapisu.

   **Określanie zachowania ładowania symboli**

   Można określić pliki, które chcesz załadować automatycznie z **symboli (.pdb) lokalizacji** lokalizacji pola podczas uruchamiania debugowania. Pliki symboli w katalogu projektu są zawsze załadowane.

5. Wybierz **wszystkie moduły, chyba że wykluczone** załadować wszystkie symbole dla wszystkich modułów, z wyjątkiem tych, które określisz po wybraniu **Określ wyłączone moduły** łącza.

6. Wybierz **tylko określonych modułów** opcji, a następnie wybierz **Określ moduły** aby oznaczyć moduły symbolizujące pliki, które chcesz ładować automatycznie. Pliki symboli dla innych modułów są ignorowane.

   **Określ opcje dodatkowe symboli**

   Można również ustawić następujące opcje na **narzędzia / Opcje / Debugowanie / symbole** strony:

   **Ostrzegaj, jeśli brak symboli podczas uruchamiania (tylko natywne)**

   Po wybraniu wyświetlane jest okno dialogowe ostrzeżenia podczas próby debugowania programu, dla którego debuger nie ma informacji o symbolach.

   **Ładuj eksporty DLL**

   Po wybraniu ładuje tabele eksportu bibliotek DLL. Informacje symboliczne z tabel eksportu bibliotek DLL mogą być przydatne, jeśli pracujesz z komunikatami systemu Windows, procedurami systemu Windows (WindowProcs), obiektami COM, kierowaniem lub dowolną biblioteką DLL, dla której nie masz symboli. Odczytywanie informacji o eksportowaniu biblioteki DLL są związane z pewnym dodatkowym obciążeniem. Dlatego ta funkcja jest domyślnie wyłączona.

   Aby zobaczyć, jakie symbole są dostępne w tabeli eksportu biblioteki dll, użyj `dumpbin /exports`. Symbole są dostępne dla dowolnej 32-bitowej systemowej biblioteki DLL. Czytając `dumpbin /exports` danych wyjściowych, możesz zobaczyć dokładną nazwę funkcji, w tym znaki inne niż alfanumeryczne. Jest to przydatne przy ustawianiu punktu przerwania w funkcji. Nazwy funkcji tabel eksportu biblioteki DLL mogą być pojawić się obcięte gdzie indziej w debugerze. Wywołania są wymienione w kolejności wywołań, z bieżącą funkcją (najgłębiej zagnieżdżoną) na początku. Aby uzyskać więcej informacji, zobacz [dumpbin/EXPORTS](http://msdn.microsoft.com/library/2971ab7e-4ee6-478b-9c85-cda42a4ce1bf).

###  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a> Użyj serwerów symboli używanych do wyszukiwania plików symboli nie na komputerze lokalnym
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] można pobierać pliki symboli debugowania z serwerów symboli, które implementują protokół symsrv. [Visual Studio Team Foundation Server](http://msdn.microsoft.com/library/bd6977ca-e30a-491a-a153-671d81222ce6) i [Debugging Tools for Windows](http://msdn.microsoft.com/library/windows/hardware/ff551063\(v=VS.85\).aspx) to dwa narzędzia, które mogą implementować serwery symboli. Określasz serwery symboli do użycia w VS **opcje** okno dialogowe.

 Serwery symboli, z których możesz korzystać, obejmują:

 **Publiczne serwery symboli Microsoft**

 Aby debugować awarię, która występuje podczas wywoływania biblioteki DLL systemu lub innej biblioteki, często potrzebować będziesz systemowych plików .pdb, które zawierają symbole dla Windows DLL, EXE i sterowników urządzeń. Możesz uzyskać te symbole z serwerów publicznych firmy Microsoft. Serwery publiczne symboli firmy Microsoft zapewniają symbole dla systemów operacyjnych Windows, oprócz MDAC, IIS, a [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

 Aby korzystać z serwerów symboli Microsoft, wybierz **opcje i ustawienia** na **debugowania** menu, a następnie wybierz **symbole**. Wybierz **serwery symboli firmy Microsoft**.

 **Serwery symboli w sieci wewnętrznej lub na komputerze lokalnym**

 Zespół lub firma mogą tworzyć serwery symboli dla własnych produktów i w roli pamięci podręcznej dla symboli ze źródeł zewnętrznych. Możesz mieć serwer symboli na własnym komputerze. Możesz wprowadzić lokalizację serwerów symboli jako adres URL lub ścieżkę na **debugowanie**/**symbole** strona VS **okno dialogowe opcji**.

 **Serwery symboli innych firm**

 Inni dostawcy aplikacji systemu Windows i bibliotek mogą zapewnić dostęp do serwera symboli w Internecie. Wprowadzasz również adres URL tych serwerów symboli na **debugowanie**/**symbole** strony

> [!NOTE]
>  Jeśli używasz serwera symboli innego niż publiczne serwery symboli Microsoft, upewnij się, że serwer symboli i jego ścieżka są godne zaufania. Pliki symboli mogą zawierać dowolny kod wykonywalny, dlatego możesz być narażony na zagrożenia bezpieczeństwa.

###  <a name="BKMK_Find_and_load_symbols_while_debugging"></a> Znajdź i załaduj symbole podczas debugowania
 W dowolnym momencie, gdy debuger jest w trybie przerwania, można załadować symbole dla modułu, który wcześniej został wykluczony przez opcje debugera lub których kompilator nie mógł odnaleźć. Możesz załadować symbole z menu skrótów okien Stos wywołań, Moduły, Elementy lokalne, Automatyczne i wszystkich okien Czujka. Jeśli debuger przerwie działanie na kodzie, który nie zawiera dostępnych plików symboli lub źródłowych, pojawi się okno dokumentu. Tutaj można znaleźć informacje o brakujących plikach i podjąć działania w celu odszukania i załadowania ich.

 **Znajdź symbole przy użyciu stron dokumentu nie załadowano symboli**

 Istnieje szereg sposobów na to, aby debuger wszedł do kodu, który nie zawiera dostępnych symboli:

1. Przechodzenie do kodu.

2. Wejście do kodu z punktu przerwania lub wyjątku.

3. Przełączenie do innego wątku.

4. Zmiana ramek stosu przez dwukrotne kliknięcie ramki w oknie wywołania stosu.

   Gdy wystąpi jedno z tych zdarzeń, debuger wyświetla **Brak załadowanych symboli** strony, aby pomóc Ci znaleźć i załadować niezbędne symbole.

   ![Strona nie załadowano symboli](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")

- Aby zmienić ścieżki wyszukiwania, wybierz niezaznaczoną ścieżkę lub wybierz **New** i wprowadź nową ścieżkę. Wybierz **obciążenia** wyszukać ponownie ścieżki i załadować plik symbolu, jeśli zostanie znaleziony.

- Wybierz **Przeglądaj i Przeszukuj**_nazwę pliku wykonywalnego_**...**  zastąpić wszelkie opcje symbolu i ponów próbę ścieżki wyszukiwania. Plik symboli jest ładowany, jeśli zostanie odnaleziony, lub wyświetlany jest Eksplorator plików, aby użytkownik mógł ręczne wybrać plik symboli.

- Wybierz **Zmień ustawienia symboli...**  do wyświetlenia **debugowanie** / **symbole** strony okna dialogowego VS opcje.

- Wybierz **wyświetlić dezasemblację** aby pokazać demontaż w nowym oknie jeden raz.

- Aby zawsze pokazywać deasemblację, gdy nie znaleziono plików źródłowych lub symboli, wybierz opcję **okna dialogowego Opcje** link i zaznacz **Włącz debugowanie na poziomie adresów** i **Pokaż dezasemblację Jeśli źródło jest niedostępne**.

   ![Opcje &#47; debugowanie &#47; Opcje ogólne dezasemblacji](../debugger/media/dbg-options-general-disassembly-checkbox.png "DBG_Options_General_disassembly_checkbox")

  **Zmień opcje symboli z menu skrótów**

  Gdy jesteś w trybie przerwania możesz znaleźć i załadować symbole dla elementów, które są wyświetlane w oknach Stos wywołań, Moduły, Lokalne, Automatyczne i wszystkich oknach Czujka Zaznacz element w oknie, otwórz menu podręczne i wybierz jedną z następujących opcji:

|Opcja|Opis|
|------------|-----------------|
|**Załaduj symbole**|Próbuje załadować symbole z lokalizacji określonej na **debugowanie** / **symbole** strony **opcje** okno dialogowe. Jeśli nie można znaleźć pliku symboli, uruchamiany jest Eksplorator plików, tak aby można było określić nową lokalizację do wyszukiwania.|
|**Informacje o ładowaniu symboli**|Przedstawia informacje wskazujące lokalizację załadowanego pliku symboli lub lokalizacje, które były przeszukiwane, jeśli debuger nie może znaleźć pliku.|
|**Ustawienia symboli...**|Otwiera **debugowanie** / **symbole** strona VS **opcje** okno dialogowe.|
|**Zawsze ładuj automatycznie**|Dodaje plik symboli do listy plików, które są ładowane automatycznie przez debuger.|

###  <a name="BKMK_Set_compiler_options_for_symbol_files"></a> Ustaw opcje kompilatora dla plików symboli
 Podczas budowania projektu z VS IDE i stosowania standardowej **debugowania** konfigurację kompilacji, C++ i zarządzane kompilatory tworzyć pliki odpowiednich symboli dla kodu. Możesz również ustawić opcje kompilatora w wierszu polecenia, aby tworzyć pliki symboli.

 **Opcje języka C++**

 Plik bazy danych programu (.pdb) przechowuje informacje od debugowaniu i stanie projektu, co pozwala na łączenie przyrostowe konfiguracji debugowania programu. Tworzony jest plik .pdb podczas konstruowania z [/zi lub/zi](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) (dla C/C++).

 W [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], [/Fd](http://msdn.microsoft.com/library/3977a9ed-f0ac-45df-bf06-01cedd2ba85a) opcja nazywa plik .pdb utworzony przez kompilator. Podczas tworzenia projektu w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] przy użyciu kreatorów, **/Fd** opcja jest ustawiona na tworzenie pliku .pdb o nazwie *projektu*.pdb.

 Jeśli kompilujesz aplikację C/C++ za pomocą pliku reguł programu make i określisz **/zi** lub **/zi** bez **/Fd**, znajdą się z dwoma plikami .pdb:

- VC*x*.pdb, gdzie *x* oznacza wersję Visual C++, na przykład VC11.pdb. Ten plik przechowuje wszystkie informacje o debugowaniu dla poszczególnych plików OBJ i znajduje się w tym samym katalogu, co plik makefile projektu.

- Project.pdb ten plik przechowuje wszystkie informacje debugowania dla pliku the.exe. Dla języka C/C++ znajduje się w podkatalogu \debug.

  Zawsze tworzy plik OBJ, kompilator C/C++ scala informacje debugowania VC*x*.pdb. Informacje wstawione zawierają informacje o typie, ale nie zawierają informacji o symbolach, takich jak definicje funkcji. Tak, nawet jeśli każdy plik źródłowy zawiera wspólne pliki nagłówkowe \<windows.h >, definicje TypeDef z tych nagłówków są zapisywane tylko raz, a nie w każdym pliku OBJ.

  Konsolidator tworzy plik project.pdb, który zawiera informacje debugowania do pliku EXE projektu. Plik project.pdb zawiera pełne informacje o debugowaniu, w tym prototypy funkcji, nie tylko informacje o typie znalezione w VC*x*.pdb. Oba pliki .pdb zezwalają na aktualizacje przyrostowe. Konsolidator osadza także ścieżkę do pliku .pdb w pliku .exe lub .dll, który tworzy.

  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Debuger używa ścieżki do pliku .pdb w pliku EXE lub DLL do znajdowania pliku project.pdb. Jeśli debuger nie może odnaleźć pliku .pdb w tej lokalizacji lub jeśli ścieżka jest nieprawidłowa (na przykład, jeśli projekt został przeniesiony do innego komputera), debuger przeszukuje ścieżkę zawierającą plik EXE, następnie ścieżki symboli określone w **opcje** okno dialogowe (**debugowanie** folderze **symbole** węzła). Debuger nie załaduje pliku .pdb, który nie pasuje do debugowanego pliku wykonywalnego. Jeśli debuger nie może odnaleźć pliku .pdb, **Znajdź symbole** pojawi się okno dialogowe, które pozwala wyszukiwać symbole lub dodać dodatkowe lokalizacje do ścieżki wyszukiwania.

  **Opcje .NET framework**

  Plik bazy danych programu (.pdb) przechowuje informacje o debugowaniu i stanie projektu, co pozwala na łączenie przyrostowe konfiguracji debugowania programu. Tworzony jest plik .pdb podczas konstruowania z **/debug**. Możesz tworzyć aplikacje przy użyciu **/Debug: full** lub **/debug:pdbonly**. Kompilowanie z użyciem **/Debug: full** generuje kod do debugowania. Kompilowanie z użyciem **/debug:pdbonly** generuje pliki .pdb, ale nie generuje `DebuggableAttribute` który informuje kompilator JIT, dostępne są informacje debugowania. Użyj **/debug:pdbonly** Jeśli chcesz wygenerować pliki .pdb dla kompilacji wydania, które nie chcesz debugować. Aby uzyskać więcej informacji, zobacz [/Debug (opcje kompilatora C#)](http://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969) lub [/Debug (Visual Basic)](http://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).

  [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Debuger używa ścieżki do pliku .pdb w pliku EXE lub DLL do znajdowania pliku project.pdb. Jeśli debuger nie może odnaleźć pliku .pdb w tej lokalizacji lub jeśli ścieżka jest nieprawidłowa, debuger przeszukuje ścieżkę zawierającą plik EXE, a następnie ścieżki symboli określone w **opcje** okno dialogowe. Ta ścieżka jest folderem **debugowanie** folderu w **symbole** węzła. Debuger nie załaduje pliku .pdb, który nie pasuje do debugowanego pliku wykonywalnego. Jeśli debuger nie może odnaleźć pliku .pdb, **Znajdź symbole** pojawi się okno dialogowe, które pozwala wyszukiwać symbole lub dodać dodatkowe lokalizacje do ścieżki wyszukiwania.

  **Aplikacje sieci Web**

  Plik konfiguracyjny aplikacji (Web.config) musi być ustawiony w tryb debugowania. Tryb debugowania powoduje, że ASP.NET generuje symbole dla dynamicznie generowanych plików i umożliwia debugerowi dołączenie do aplikacji ASP.NET. VS automatycznie ustawia to podczas uruchamiania debugowania, jeśli projekt został utworzony z szablonu projektów sieci Web.

##  <a name="BKMK_Find_source_files"></a> Znajdowanie plików źródłowych

###  <a name="BKMK_Where_the_debugger_searches_for_source_files"></a> Gdzie debuger wyszukuje pliki źródłowe
 Debuger szuka plików źródłowych w następujących lokalizacjach:

1.  Pliki otwarte w środowisku IDE wystąpienia programu Visual Studio, które uruchomiło debugera.

2.  Pliki w rozwiązaniu, które są otwarte w wystąpieniu programu Visual Studio.

3.  Katalogi, które są określone w **wspólne właściwości** / **Debuguj pliki źródłowe** strony właściwości rozwiązania. (W **Eksploratora rozwiązań**, wybierz węzeł rozwiązania, kliknij prawym przyciskiem myszy i wybierz **właściwości**. )

4.  Informacje źródłowe z .pdb modułu. Może to być lokalizacja pliku źródłowego, gdy moduł został skompilowany, lub może to być polecenie do serwera źródłowego.

###  <a name="BKMK_Find_and_load_source_files_with_the_No_Source___No_Symbols_Loaded_pages"></a> Znajdź i Załaduj pliki źródłowe z Brak źródła / Brak załadowanych symboli stron
 Kiedy debuger przerywa wykonywanie w miejscu, gdzie plik źródłowy nie jest dostępny, wyświetli **Brak załadowanego źródła** lub **Brak załadowanych symboli** stron, które mogą pomóc w znalezieniu pliku źródłowego. **Brak załadowanych symboli** pojawia się, kiedy debuger nie może odnaleźć pliku symboli (.pdb) dla pliku wykonywalnego zakończyć wyszukiwanie. Strona Brak symboli zawiera opcje wyszukiwania pliku. Jeśli plik .pdb zostanie znaleziony po wykonaniu jednej z opcji i debuger może pobrać plik źródłowy przy użyciu informacji w pliku symboli, źródło jest wyświetlane. W przeciwnym razie **Brak załadowanego źródła** strona jest wyświetlana, która opisuje problem. Na stronie są wyświetlane łącza do opcji mogących wykonywać akcje, które mogą rozwiązać problem.

###  <a name="BKMK_Add_source_file_search_paths_to_a_solution"></a> Dodawanie ścieżki wyszukiwania pliku źródłowego do rozwiązania
 Możesz określić sieć lub katalogi lokalne, aby w nich wyszukiwać pliki źródłowe.

1. Wybierz rozwiązanie w Eksploratorze rozwiązań, a następnie wybierz **właściwości** z menu skrótów.

2. W obszarze **wspólne właściwości** węzła, wybierz **Debuguj pliki źródłowe**.

3. Kliknij folder ![narzędzia&#47; opcje&#47; debugowanie&#47;ikonę folderu symbole](../debugger/media/dbg-tools-options-foldersicon.png "DBG_Tools_Options_FoldersIcon") ikony. Tekst edytowalny pojawia się w **katalogi zawierające kod źródłowy** listy.

4. Dodaj ścieżkę, którą chcesz przeszukać.

   Należy zauważyć, że przeszukiwany jest tylko określony katalog. Musisz dodać wpisy do wszystkich podkatalogów, które chcesz przeszukać.

###  <a name="BKMK_Use_source_servers"></a> Użyj serwerów źródłowych
 Gdy na komputerze lokalnym nie ma kodu źródłowego lub plik .pdb nie pasuje do kodu źródłowego, możesz użyć Serwera źródłowego, aby pomóc w debugowaniu aplikacji. Serwer źródłowy przyjmuje żądania dotyczące plików i zwraca rzeczywiste pliki. Serwer źródłowy jest uruchamiany za pomocą pliku DLL, o nazwie srcsrv.dll. Serwer źródłowy odczytuje plik .pdb aplikacji, który zawiera wskazówki do repozytorium kodu źródłowego, a także polecenia używane do pobierania kodu źródłowego z repozytorium. Możesz ograniczyć, jakie polecenia mogą być wykonywane z pliku .pdb aplikacji, poprzez wymienienie dozwolonych poleceń wewnątrz pliku o nazwie srcsrv.ini, który musi być umieszczony w tym samym katalogu, co srcsrv.dll i devenv.exe.

> [!IMPORTANT]
>  Dowolne polecenia mogą być osadzone w pliku .pdb aplikacji, więc upewnij się, że można umieścić tylko te, które chcesz wykonać w pliku srcsrv.ini. Każda próba wykonania polecenia nie w pliku srcsvr.ini spowoduje pojawienie się okna dialogowego potwierdzenia. Aby uzyskać więcej informacji, zobacz [ostrzeżenie o zabezpieczeniach: Debuger musi wykonać polecenie niezaufane](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Nie jest sprawdzana poprawność parametrów poleceń, więc należy być ostrożnym z poleceniami zaufanymi. Na przykład, jeśli użytkownik zaufał narzędziu cmd.exe, złośliwy użytkownik może określić parametry, które czyniłyby polecenie niebezpiecznym.

 **Aby włączyć korzystanie z serwera źródłowego**

1.  Upewnij się, że postępujesz zgodnie ze środkami bezpieczeństwa opisanymi w poprzedniej sekcji.

2.  Na **narzędzia** menu, wybierz **opcje**.

     **Opcje** pojawi się okno dialogowe.

3.  W **debugowanie** węzła, wybierz **ogólne**.

4.  Wybierz **Włącz obsługę serwera źródłowego** pole wyboru.

     ![Włącz opcje serwera źródłowego](../debugger/media/dbg-options-general-enablesrcsrvr-checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")

5.  (Opcjonalnie) Wybierz żądane opcje podrzędne.

     Należy pamiętać, że oba **Zezwalaj na serwerze źródłowym na częściowo zaufane zestawy (tylko kod zarządzany)** i **zawsze uruchamiaj niezaufane polecenia serwera źródłowego bez monitowania użytkownika o** mogą zwiększyć zagrożenia dla bezpieczeństwa omówione powyżej.

## <a name="see-also"></a>Zobacz też
 [Zdalnym zmiany w programie Visual Studio 2012 i 2013 ładowaniu symboli .NET](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013.aspx)
