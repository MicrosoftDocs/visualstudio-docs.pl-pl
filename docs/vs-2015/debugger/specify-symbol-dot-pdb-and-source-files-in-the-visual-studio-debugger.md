---
title: Określ symboli (.pdb) i pliki w debugerze źródłowe | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: d4d4b02d512480d96c501758f4cf0f1313158942
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300544"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger"></a>Określanie plików symboli (.pdb) i plików źródłowych w debugerze programu Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Plik bazy danych programu (.pdb), nazywany także plikiem symboli, mapuje identyfikatory, które tworzysz w plikach źródłowych dla klas, metod i innego kodu, na identyfikatory które są używane w skompilowanych plikach wykonywalnych projektu. Plik .pdb mapuje również instrukcje zawarte w kodzie źródłowym na instrukcje wykonania w plikach wykonywalnych. Debuger używa tych informacji do określenia dwóch informacji o znaczeniu kluczowym: plik źródłowy i numer wiersza, które są wyświetlane w programie Visual Studio IDE oraz lokalizacja w pliku wykonywalnym, w której program się zatrzyma, jeśli ustawisz punkt przerwania. Plik symboli zawiera także oryginalną lokalizację plików źródłowych i opcjonalnie lokalizację serwera źródeł, z którego mogą być pobierane pliki źródłowe.

 Podczas debugowania projektu w programie Visual Studio IDE debuger wie, domyślna lokalizacja dla plików .pdb i źródła, w kodzie. Jeśli chcesz debugować kod poza kodem źródłowym projektu, taki jak kod systemu Windows lub kod zewnętrznych aplikacji wywoływanych w projekcie, należy określić lokalizację pliku .pdb (i opcjonalnie plików źródłowych kodu zewnętrznego), i te pliki muszą dokładnie odpowiadać kompilacji plików wykonywalnych.

 Przed Visual Studio 2012 podczas debugowania kodu zarządzanego na urządzeniu zdalnym niezbędna do umieszczenia plików symboli na komputerze zdalnym. Obecnie taka ewentualność nie zachodzi. Wszystkie pliki symboli muszą znajdować się na komputerze lokalnym lub w lokalizacji określonej na stronie **Narzędzia/Opcje/debugowanie/symbole** .

## <a name="BKMK_Find_symbol___pdb__files"></a>Gdzie debuger wyszukuje pliki. pdb

1. Lokalizacja określona w pliku DLL lub pliku wykonywalnym.

     (Domyślnie, jeśli skompilowałeś bibliotekę DLL lub plik wykonywalny na swoim komputerze, konsolidator umieszcza pełną ścieżkę i nazwę skojarzonego pliku .pdb wewnątrz pliku DLL lub pliku wykonywalnego. Debuger najpierw sprawdza, czy plik symboli znajduje się w lokalizacji określonej w pliku DLL lub pliku wykonywalnym. Jest to pomocne, ponieważ zawsze masz dostępne symbole dla kodu, który skompilowałeś na swoim komputerze.)

2. Pliki .pdb, które mogą się znajdować w tym samym folderze, co plik DLL lub plik wykonywalny.

3. Wszystkie lokalne foldery pamięci podręcznej symboli.

4. Wszelkie sieci, Internet lub określone lokalne serwery symboli i lokalizacje, takie jak serwer symboli Microsoft, jeśli są włączone.

### <a name="BKMK_Why_do_symbol_files_need_to_exactly_match_the_executable_files_"></a>Dlaczego pliki symboli muszą dokładnie odpowiadać plikom wykonywalnym?
 Debuger będzie ładował tylko plik .pdb dla pliku wykonywalnego, który dokładnie pasuje do pliku .pdb, który z kolei został utworzony podczas kompilowania pliku wykonywalnego (czyli .pdb musi być plikiem oryginalnym lub kopią oryginalnego pliku .pdb). Ponieważ kompilator jest zoptymalizowany pod kątem szybkości kompilacji, oprócz swojego głównego zadania utworzenia prawidłowego i efektywnego kodu, można zmienić układ pliku wykonywalnego, nawet jeśli nie zmienił się sam kod. Aby uzyskać więcej informacji [, zobacz Dlaczego program Visual Studio wymaga, aby pliki symboli debugera były dokładnie zgodne z plikami binarnymi, z których zostały skompilowane?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/).

### <a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a>Określ lokalizacje symboli i zachowanie ładowania
 Podczas debugowania projektu w VS IDE, debuger automatycznie ładuje pliki symboli, które znajdują się w katalogu projektu. Możesz określić alternatywne ścieżki wyszukiwania i serwery symboli dla Microsoft, Windows lub składników innych firm w obszarze **Narzędzia/Opcje/debugowanie/symbole**. Można również określić konkretne moduły, dla których debuger ma automatycznie ładować symbole. Można też następnie zmienić te ustawienia ręcznie podczas aktywnego debugowania.

1. W programie Visual Studio Otwórz stronę **Narzędzia/Opcje/debugowanie/symbole** .

    ![Strona &#45; opcje &#45; narzędzi &#45; debugowania symboli](../debugger/media/dbg-tools-options-symbols.png "DBG_Tools_Options_Symbols")

2. Wybierz pozycję ![narzędzia&#47; folderów opcje&#47; debugowania&#47;ikona folderu symboli](../debugger/media/dbg-tools-options-foldersicon.png "DBG_Tools_Options_FoldersIcon") . Tekst edytowalny pojawia się w polu **lokalizacje pliku symboli (. pdb)** .

3. Wpisz adres URL lub ścieżkę katalogu serwera symboli lub lokalizację symboli. Uzupełnianie instrukcji pomaga w znalezieniu właściwego formatu.

4. Aby poprawić wydajność ładowania symboli, wpisz ścieżkę do katalogu lokalnego, gdzie symbole mogą być kopiowane przez serwery symboli w **symbolach pamięci podręcznej w tym katalogu** , do katalogu lokalnego, do którego można skopiować symbole.

   > [!NOTE]
   > Pamięci podręcznej symboli nie należy umieszczać w folderze chronionym (na przykład C:\Windows lub jednym z jego podfolderów). Zamiast tego użyj folderu przeznaczonego do odczytu i zapisu.

   **Określ zachowanie ładowania symboli**

   Możesz określić pliki, które mają być ładowane automatycznie z lokalizacji pola **lokalizacje plików symboli (. pdb)** po rozpoczęciu debugowania. Pliki symboli w katalogu projektu są zawsze załadowane.

5. Wybierz **wszystkie moduły, chyba że zostaną wykluczone,** aby załadować wszystkie symbole dla wszystkich modułów, z wyjątkiem tych, które określisz po wybraniu łącza **Określ wyłączone moduły** .

6. Wybierz opcję **tylko określone moduły** , a następnie wybierz pozycję **Określ moduły** , aby wyświetlić listę modułów, które mają być ładowane automatycznie. Pliki symboli dla innych modułów są ignorowane.

   **Określ dodatkowe opcje symboli**

   Możesz również ustawić następujące opcje na stronie **Narzędzia/Opcje/debugowanie/symbole** :

   **Ostrzegaj, jeśli nie ma symboli podczas uruchamiania (tylko kod natywny)**

   Po wybraniu wyświetlane jest okno dialogowe ostrzeżenia podczas próby debugowania programu, dla którego debuger nie ma informacji o symbolach.

   **Załaduj eksporty biblioteki DLL**

   Po wybraniu ładuje tabele eksportu bibliotek DLL. Informacje symboliczne z tabel eksportu bibliotek DLL mogą być przydatne, jeśli pracujesz z komunikatami systemu Windows, procedurami systemu Windows (WindowProcs), obiektami COM, kierowaniem lub dowolną biblioteką DLL, dla której nie masz symboli. Odczytywanie informacji o eksportowaniu biblioteki DLL są związane z pewnym dodatkowym obciążeniem. Dlatego ta funkcja jest domyślnie wyłączona.

   Aby zobaczyć, jakie symbole są dostępne w tabeli eksportu biblioteki DLL, użyj `dumpbin /exports`. Symbole są dostępne dla dowolnej 32-bitowej systemowej biblioteki DLL. Odczytując dane wyjściowe `dumpbin /exports`, można zobaczyć dokładną nazwę funkcji, w tym znaki inne niż alfanumeryczne. Jest to przydatne przy ustawianiu punktu przerwania w funkcji. Nazwy funkcji tabel eksportu biblioteki DLL mogą być pojawić się obcięte gdzie indziej w debugerze. Wywołania są wymienione w kolejności wywołań, z bieżącą funkcją (najgłębiej zagnieżdżoną) na początku. Aby uzyskać więcej informacji, zobacz [polecenia DUMPBIN/exports](https://msdn.microsoft.com/library/2971ab7e-4ee6-478b-9c85-cda42a4ce1bf).

### <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a>Użyj serwerów symboli, aby znaleźć pliki symboli, które nie znajdują się na komputerze lokalnym
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] może pobrać pliki symboli debugowania z serwerów symboli, które implementują protokół symsrv. [Program Visual Studio Team Foundation Server](https://msdn.microsoft.com/library/bd6977ca-e30a-491a-a153-671d81222ce6) i [narzędzia debugowania dla systemu Windows](https://msdn.microsoft.com/library/windows/hardware/ff551063\(v=VS.85\).aspx) to dwa narzędzia, które mogą implementować serwery symboli. Należy określić serwery symboli do użycia w oknie dialogowym **Opcje** programu vs.

 Serwery symboli, z których możesz korzystać, obejmują:

 **Publiczne serwery symboli Microsoft**

 Aby debugować awarię, która występuje podczas wywoływania biblioteki DLL systemu lub innej biblioteki, często potrzebować będziesz systemowych plików .pdb, które zawierają symbole dla Windows DLL, EXE i sterowników urządzeń. Możesz uzyskać te symbole z serwerów publicznych firmy Microsoft. Publiczne serwery symboli Microsoft zapewniają symbole dla systemów operacyjnych Windows, oprócz MDAC, IIS, ISA i [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

 Aby korzystać z serwerów symboli Microsoft, wybierz **Opcje i ustawienia** w menu **Debuguj** , a następnie wybierz **symbole**. Wybierz pozycję **serwery symboli firmy Microsoft**.

 **Serwery symboli w sieci wewnętrznej lub na komputerze lokalnym**

 Zespół lub firma mogą tworzyć serwery symboli dla własnych produktów i w roli pamięci podręcznej dla symboli ze źródeł zewnętrznych. Możesz mieć serwer symboli na własnym komputerze. Możesz wprowadzić lokalizację serwerów symboli jako adres URL lub ścieżkę na stronie " **debugowanie**/**symbole** " **okna dialogowego**programu vs.

 **Serwery symboli innych firm**

 Inni dostawcy aplikacji systemu Windows i bibliotek mogą zapewnić dostęp do serwera symboli w Internecie. Możesz również wprowadzić adres URL tych serwerów symboli na stronie **debugowanie** **symboli**/

> [!NOTE]
> Jeśli używasz serwera symboli innego niż publiczne serwery symboli Microsoft, upewnij się, że serwer symboli i jego ścieżka są godne zaufania. Pliki symboli mogą zawierać dowolny kod wykonywalny, dlatego możesz być narażony na zagrożenia bezpieczeństwa.

### <a name="BKMK_Find_and_load_symbols_while_debugging"></a>Znajdź i Załaduj symbole podczas debugowania
 W dowolnym momencie, gdy debuger jest w trybie przerwania, można załadować symbole dla modułu, który wcześniej został wykluczony przez opcje debugera lub których kompilator nie mógł odnaleźć. Możesz załadować symbole z menu skrótów okien Stos wywołań, Moduły, Elementy lokalne, Automatyczne i wszystkich okien Czujka. Jeśli debuger przerwie działanie na kodzie, który nie zawiera dostępnych plików symboli lub źródłowych, pojawi się okno dokumentu. Tutaj można znaleźć informacje o brakujących plikach i podjąć działania w celu odszukania i załadowania ich.

 **Znajdź symbole ze stronami dokumentu nie załadowano symboli**

 Istnieje szereg sposobów na to, aby debuger wszedł do kodu, który nie zawiera dostępnych symboli:

1. Przechodzenie do kodu.

2. Wejście do kodu z punktu przerwania lub wyjątku.

3. Przełączenie do innego wątku.

4. Zmiana ramek stosu przez dwukrotne kliknięcie ramki w oknie wywołania stosu.

   Gdy wystąpi jedno z tych zdarzeń, debuger wyświetla stronę **nie załadowano symboli** , aby pomóc Ci znaleźć i załadować niezbędne symbole.

   ![Nie załadowano żadnych symboli na stronie](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")

- Aby zmienić ścieżki wyszukiwania, wybierz niewybraną ścieżkę lub wybierz **Nowy** i wprowadź nową ścieżkę. Wybierz pozycję **Załaduj** , aby ponownie przeszukać ścieżki i załadować plik symboli, jeśli zostanie znaleziony.

- Wybierz **Przeglądaj i Znajdź**_nazwę pliku wykonywalnego_ **..** ., aby zastąpić wszelkie opcje symboli i ponów próbę ścieżki wyszukiwania. Plik symboli jest ładowany, jeśli zostanie odnaleziony, lub wyświetlany jest Eksplorator plików, aby użytkownik mógł ręczne wybrać plik symboli.

- Wybierz pozycję **Zmień ustawienia symboli..** ., aby wyświetlić stronę " **debugowanie** / **symbole** " okna dialogowego Opcje programu vs.

- Wybierz pozycję **Wyświetl demontaż** , aby wyświetlić demontaż w nowym oknie jeden raz.

- Aby zawsze pokazać demontaż, gdy nie znaleziono plików źródłowych lub symboli, wybierz łącze **okno dialogowe Opcje** i wybierz opcję **Włącz debugowanie na poziomie adresu** i **Pokaż demontaż, jeśli źródło jest niedostępne**.

   ![Opcje &#47; debugowania &#47; ogólnych opcji demontażu](../debugger/media/dbg-options-general-disassembly-checkbox.png "DBG_Options_General_disassembly_checkbox")

  **Zmień opcje symboli z menu skrótów**

  Gdy jesteś w trybie przerwania możesz znaleźć i załadować symbole dla elementów, które są wyświetlane w oknach Stos wywołań, Moduły, Lokalne, Automatyczne i wszystkich oknach Czujka Zaznacz element w oknie, otwórz menu podręczne i wybierz jedną z następujących opcji:

|Opcja|Opis|
|------------|-----------------|
|**Załaduj symbole**|Próbuje załadować symbole z lokalizacji określonych na stronie " **debugowanie** / **symbole** " okna dialogowego **Opcje** . Jeśli nie można znaleźć pliku symboli, uruchamiany jest Eksplorator plików, tak aby można było określić nową lokalizację do wyszukiwania.|
|**Informacje o ładowaniu symboli**|Przedstawia informacje wskazujące lokalizację załadowanego pliku symboli lub lokalizacje, które były przeszukiwane, jeśli debuger nie może znaleźć pliku.|
|**Ustawienia symboli...**|Otwiera stronę " **debugowanie** / **symbole** " okna dialogowego **Opcje** programu vs.|
|**Zawsze ładuj automatycznie**|Dodaje plik symboli do listy plików, które są ładowane automatycznie przez debuger.|

### <a name="BKMK_Set_compiler_options_for_symbol_files"></a>Ustawianie opcji kompilatora dla plików symboli
 Podczas kompilowania projektu z programu VS IDE i stosowania standardowej konfiguracji kompilacji do **debugowania** konstruktory C++ i zarządzane kompilatory tworzą odpowiednie pliki symboli dla kodu. Możesz również ustawić opcje kompilatora w wierszu polecenia, aby tworzyć pliki symboli.

 **C++Opcje**

 Plik bazy danych programu (.pdb) przechowuje informacje od debugowaniu i stanie projektu, co pozwala na łączenie przyrostowe konfiguracji debugowania programu. Plik. pdb jest tworzony podczas kompilowania z [/Zi lub/Zi](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8) (dla C/C++).

 W [!INCLUDE[vcprvc](../includes/vcprvc-md.md)]opcja [/FD](https://msdn.microsoft.com/library/3977a9ed-f0ac-45df-bf06-01cedd2ba85a) nadaje nazwę plikowi. pdb utworzonym przez kompilator. Podczas tworzenia projektu w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] przy użyciu kreatorów opcja **/FD** jest ustawiona na tworzenie pliku. pdb o nazwie *Project*. pdb.

 Jeśli tworzyszC++ aplikację C/, używając pliku reguł programu make i określisz **/Zi** lub **/Zi** bez **/FD**, utworzysz dwa pliki. pdb:

- VC*x*. pdb, gdzie *x* reprezentuje wersję wizualizacji C++, na przykład VC11. pdb. Ten plik przechowuje wszystkie informacje o debugowaniu dla poszczególnych plików OBJ i znajduje się w tym samym katalogu, co plik makefile projektu.

- Project.pdb ten plik przechowuje wszystkie informacje debugowania dla pliku the.exe. Dla języka C/C++ znajduje się w podkatalogu \debug.

  Za każdym razem, gdy tworzy plik OBJ, kompilator językaC++ C/scala informacje debugowania do pliku VC*x*. pdb. Informacje wstawione zawierają informacje o typie, ale nie zawierają informacji o symbolach, takich jak definicje funkcji. Nawet jeśli każdy plik źródłowy zawiera wspólne pliki nagłówkowe, takie jak \<Windows. h >, definicje TypeDef z tych nagłówków są zapisywane tylko raz, a nie w każdym pliku OBJ.

  Konsolidator tworzy plik project.pdb, który zawiera informacje debugowania do pliku EXE projektu. Plik Project. pdb zawiera pełne informacje o debugowaniu, w tym prototypy funkcji, a nie tylko informacje o typie Znalezione w VC*x*. pdb. Oba pliki .pdb zezwalają na aktualizacje przyrostowe. Konsolidator osadza także ścieżkę do pliku .pdb w pliku .exe lub .dll, który tworzy.

  Debuger [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] używa ścieżki do pliku. pdb w pliku EXE lub DLL do znajdowania pliku Project. pdb. Jeśli debuger nie może znaleźć pliku. pdb w tej lokalizacji lub jeśli ścieżka jest nieprawidłowa (na przykład jeśli projekt został przeniesiony do innego komputera), debuger przeszukuje ścieżkę zawierającą plik EXE, ścieżki symboli określone w oknie dialogowym **Opcje** (folder**debugowanie** , węzeł **symbole** ). Debuger nie załaduje pliku .pdb, który nie pasuje do debugowanego pliku wykonywalnego. Jeśli debuger nie może znaleźć pliku. pdb, pojawi się okno dialogowe **Znajdowanie symboli** , które pozwala wyszukiwać symbole lub dodać dodatkowe lokalizacje do ścieżki wyszukiwania.

  **Opcje .NET Framework**

  Plik bazy danych programu (.pdb) przechowuje informacje o debugowaniu i stanie projektu, co pozwala na łączenie przyrostowe konfiguracji debugowania programu. Plik. pdb jest tworzony podczas kompilowania za pomocą **/Debug**. Możesz tworzyć aplikacje za pomocą **przełącznika/Debug: Full** lub **/Debug: pdbonly**. Kompilowanie za pomocą **/Debug: Full** generuje kod możliwością debugowania. Kompilowanie za pomocą parametru **/Debug: pdbonly** generuje pliki. pdb, ale nie generuje `DebuggableAttribute`, który informuje kompilator JIT, że dostępne są informacje debugowania. Użyj **/Debug: pdbonly** , jeśli chcesz wygenerować pliki. pdb dla kompilacji wydania, której nie chcesz możliwością debugowania. Aby uzyskać więcej informacji, zobacz [/DebugC# (opcje kompilatora)](https://msdn.microsoft.com/library/e2b48c07-01bc-45cc-a52c-92e9085eb969) lub [/debug (Visual Basic)](https://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).

  Debuger [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] używa ścieżki do pliku. pdb w pliku EXE lub DLL do znajdowania pliku Project. pdb. Jeśli debuger nie może znaleźć pliku. pdb w tej lokalizacji lub jeśli ścieżka jest nieprawidłowa, debuger przeszukuje ścieżkę zawierającą plik EXE, a następnie ścieżki symboli określone w oknie dialogowym **Opcje** . Ta ścieżka jest zazwyczaj folderem **debugowania** w węźle **symbole** . Debuger nie załaduje pliku .pdb, który nie pasuje do debugowanego pliku wykonywalnego. Jeśli debuger nie może znaleźć pliku. pdb, pojawi się okno dialogowe **Znajdowanie symboli** , które pozwala wyszukiwać symbole lub dodać dodatkowe lokalizacje do ścieżki wyszukiwania.

  **Aplikacje sieci Web**

  Plik konfiguracyjny aplikacji (Web.config) musi być ustawiony w tryb debugowania. Tryb debugowania powoduje, że ASP.NET generuje symbole dla dynamicznie generowanych plików i umożliwia debugerowi dołączenie do aplikacji ASP.NET. VS automatycznie ustawia to podczas uruchamiania debugowania, jeśli projekt został utworzony z szablonu projektów sieci Web.

## <a name="BKMK_Find_source_files"></a>Znajdź pliki źródłowe

### <a name="BKMK_Where_the_debugger_searches_for_source_files"></a>Gdzie debuger wyszukuje pliki źródłowe
 Debuger szuka plików źródłowych w następujących lokalizacjach:

1. Pliki otwarte w środowisku IDE wystąpienia programu Visual Studio, które uruchomiło debugera.

2. Pliki w rozwiązaniu, które są otwarte w wystąpieniu programu Visual Studio.

3. Katalogi, które są określone na stronie **wspólne właściwości** / **pliki źródłowe debugowania** we właściwościach rozwiązania. (W **Eksplorator rozwiązań**wybierz węzeł rozwiązania, kliknij prawym przyciskiem myszy, a następnie wybierz polecenie **Właściwości**. )

4. Informacje źródłowe z .pdb modułu. Może to być lokalizacja pliku źródłowego, gdy moduł został skompilowany, lub może to być polecenie do serwera źródłowego.

### <a name="BKMK_Find_and_load_source_files_with_the_No_Source___No_Symbols_Loaded_pages"></a>Znajdź i Załaduj pliki źródłowe ze stronami brak źródła/brak załadowanych symboli
 Gdy debuger przerywa wykonywanie w miejscu, gdzie plik źródłowy nie jest dostępny, wyświetli **nie załadowane żadne Źródło** lub **nie załadowano żadnych symboli** , które mogą pomóc w znalezieniu pliku źródłowego. Gdy debuger nie może znaleźć pliku symbolu (. pdb) dla pliku wykonywalnego, nie zostanie **załadowany żaden symbol** , aby zakończyć wyszukiwanie. Strona Brak symboli zawiera opcje wyszukiwania pliku. Jeśli plik .pdb zostanie znaleziony po wykonaniu jednej z opcji i debuger może pobrać plik źródłowy przy użyciu informacji w pliku symboli, źródło jest wyświetlane. W przeciwnym razie nie zostanie wyświetlona strona **załadowana ze źródłem** , która opisuje problem. Na stronie są wyświetlane łącza do opcji mogących wykonywać akcje, które mogą rozwiązać problem.

### <a name="BKMK_Add_source_file_search_paths_to_a_solution"></a>Dodawanie ścieżek wyszukiwania plików źródłowych do rozwiązania
 Możesz określić sieć lub katalogi lokalne, aby w nich wyszukiwać pliki źródłowe.

1. Wybierz rozwiązanie w Eksplorator rozwiązań a następnie wybierz polecenie **Właściwości** z menu skrótów.

2. W węźle **wspólne właściwości** wybierz pozycję **Debuguj pliki źródłowe**.

3. Kliknij przycisk ![narzędzia&#47; folderów opcje&#47; debugowania&#47;ikona folderu symboli](../debugger/media/dbg-tools-options-foldersicon.png "DBG_Tools_Options_FoldersIcon") . Tekst edytowalny pojawia się na liście **katalogi zawierające kod źródłowy** .

4. Dodaj ścieżkę, którą chcesz przeszukać.

   Należy zauważyć, że przeszukiwany jest tylko określony katalog. Musisz dodać wpisy do wszystkich podkatalogów, które chcesz przeszukać.

### <a name="BKMK_Use_source_servers"></a>Użyj serwerów źródłowych
 Gdy na komputerze lokalnym nie ma kodu źródłowego lub plik .pdb nie pasuje do kodu źródłowego, możesz użyć Serwera źródłowego, aby pomóc w debugowaniu aplikacji. Serwer źródłowy przyjmuje żądania dotyczące plików i zwraca rzeczywiste pliki. Serwer źródłowy jest uruchamiany za pomocą pliku DLL, o nazwie srcsrv.dll. Serwer źródłowy odczytuje plik .pdb aplikacji, który zawiera wskazówki do repozytorium kodu źródłowego, a także polecenia używane do pobierania kodu źródłowego z repozytorium. Możesz ograniczyć, jakie polecenia mogą być wykonywane z pliku .pdb aplikacji, poprzez wymienienie dozwolonych poleceń wewnątrz pliku o nazwie srcsrv.ini, który musi być umieszczony w tym samym katalogu, co srcsrv.dll i devenv.exe.

> [!IMPORTANT]
> Dowolne polecenia mogą być osadzone w pliku .pdb aplikacji, więc upewnij się, że można umieścić tylko te, które chcesz wykonać w pliku srcsrv.ini. Każda próba wykonania polecenia nie w pliku srcsvr.ini spowoduje pojawienie się okna dialogowego potwierdzenia. Aby uzyskać więcej informacji, zobacz [Ostrzeżenie o zabezpieczeniach: debuger musi wykonać polecenie niezaufane](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Nie jest sprawdzana poprawność parametrów poleceń, więc należy być ostrożnym z poleceniami zaufanymi. Na przykład, jeśli użytkownik zaufał narzędziu cmd.exe, złośliwy użytkownik może określić parametry, które czyniłyby polecenie niebezpiecznym.

 **Aby umożliwić korzystanie z serwera źródłowego**

1. Upewnij się, że postępujesz zgodnie ze środkami bezpieczeństwa opisanymi w poprzedniej sekcji.

2. W menu **Narzędzia** wybierz polecenie **Opcje**.

     Zostanie wyświetlone okno dialogowe **Opcje** .

3. W węźle **debugowanie** wybierz pozycję **Ogólne**.

4. Zaznacz pole wyboru **Włącz obsługę serwera źródłowego** .

     ![Włącz opcje serwera źródłowego](../debugger/media/dbg-options-general-enablesrcsrvr-checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")

5. (Opcjonalnie) Wybierz żądane opcje podrzędne.

     Należy zauważyć, że zarówno serwer źródłowy, jak i **zestawy częściowego zaufania (tylko zarządzane)** i **zawsze uruchamiają niezaufane polecenia serwera źródłowego bez monitowania** mogą zwiększyć zagrożenia bezpieczeństwa omówione powyżej.

## <a name="see-also"></a>Zobacz też
 [Zdalne ładowanie symboli .NET w programie Visual Studio 2012 i 2013](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)
