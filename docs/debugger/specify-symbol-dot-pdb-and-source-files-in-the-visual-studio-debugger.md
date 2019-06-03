---
title: Ustaw symboli (.pdb) i plików źródłowych w debugerze
ms.custom: seodec18
ms.date: 10/08/2018
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Debugger.Native
- VS.ToolsOptionsPages.Debugger.Symbols
- vs.debug.options.Native
- vs.debug.nosymbols
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5d7d5fa0a53ead2f49f89df37943d734a1b73fb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045345"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Określanie plików symboli (.pdb) i plików źródłowych w debugerze programu Visual Studio (C#, C++, Visual Basic F#)

Baza danych programu ( *.pdb*) plików, nazywany również pliki symboli mapowania identyfikatorów i instrukcje w kodzie źródłowym projektu do odpowiednich identyfikatorów i zgodnie z instrukcjami w skompilowanych aplikacji.

Podczas kompilowania projektu z programu Visual Studio IDE, za pomocą standardowej konfiguracji kompilacji debugowania, kompilator utworzy odpowiednie pliki symboli. Możesz również [ustawić opcje symboli w kodzie](#compiler-symbol-options).

*.Pdb* plik zawiera informacje o stanie debugowania i projekt, który pozwala na łączenie przyrostowe konfiguracji debugowania aplikacji. Debuger programu Visual Studio używa *.pdb* plików w celu określenia dwóch kluczowych informacji podczas debugowania:

* Źródła pliku nazwa i numer wiersza do wyświetlenia w programie Visual Studio IDE.
* Gdzie w aplikacji, aby zatrzymać punktu przerwania.

Pliki symboli również wskazują lokalizację plików źródłowych i opcjonalnie serwera pobierać je z.

Debuger tylko ładuje *.pdb* pliki, które dokładnie pasują *.pdb* pliki tworzone podczas kompilowania aplikacji (oznacza to, oryginalnym *.pdb* plików lub kopii). Ta duplikacja dokładnie jest konieczne, ponieważ układ aplikacji można zmienić, nawet jeśli nie zmienił się sam kod. Aby uzyskać więcej informacji, zobacz [Dlaczego Visual Studio wymaga, aby debuger symbol dokładnej zgodności plików plików binarnych, które zostały skompilowane?](https://blogs.msdn.microsoft.com/jimgries/2007/07/06/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with/)

> [!TIP]
> Aby debugować kod poza kodem źródłowym projektu, takich jak Windows kodu lub innych firm kodu aplikacji wywoływanych w projekcie, należy określić lokalizację kodu zewnętrznego *.pdb* plików (i opcjonalnie plików źródłowych), które muszą dokładnie odpowiadać kompilacje w swojej aplikacji.

## <a name="symbol-file-locations-and-loading-behavior"></a>Lokalizacje plików symboli i zachowanie ładowania

> [!NOTE]
> Podczas debugowania kodu zarządzanego na urządzeniu zdalnym, wszystkie pliki symboli muszą znajdować się na komputerze lokalnym lub w lokalizacji [określona w opcjach debugera](#BKMK_Specify_symbol_locations_and_loading_behavior).

Podczas debugowania projektu w programie Visual Studio IDE, debuger automatycznie ładuje pliki symboli, które znajdują się w folderze projektu.

Ponadto debuger wyszukuje pliki symboli w następujących lokalizacjach:

1. W lokalizacji określonej w pliku DLL lub pliku wykonywalnego ( *.exe*) pliku.

   Domyślnie jeśli skompilowałeś bibliotekę DLL lub *.exe* pliku na komputerze, konsolidator umieszcza pełną ścieżkę i nazwę skojarzonego *.pdb* pliku w bibliotece DLL lub *.exe* pliku. Debuger sprawdza, czy plik symboli znajduje się w tej lokalizacji.

2. W tym samym folderze, co biblioteki DLL lub *.exe* pliku.

3. Wszystkie lokalizacje określone w opcjach debugera dla plików symboli. Aby dodać i włączyć lokalizacje symboli, zobacz [skonfigurować lokalizacje symboli i ładowania opcji](#BKMK_Specify_symbol_locations_and_loading_behavior).

   - Dowolnego folderu pamięci podręcznej symboli.

   - Określonej sieci internet, lub lokalne serwery symboli i lokalizacje, takie jak serwery symboli firmy Microsoft, w przypadku wybrania. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] można pobierać pliki symboli debugowania z serwerów symboli, które implementują `symsrv` protokołu. [Visual Studio Team Foundation Server](/azure/devops/pipelines/tasks/build/index-sources-publish-symbols) i [Debugging Tools for Windows](/windows-hardware/drivers/debugger/index) to dwa narzędzia, które mogą korzystać z serwerów symboli.

     Serwery symboli, które mogą obejmować:

     **Serwery publiczne symboli firmy Microsoft**: Aby debugować awarię, która występuje podczas wywoływania biblioteki DLL systemu lub do biblioteki innych firm, często muszą system *.pdb* plików. System *.pdb* pliki zawierają symbole dla Windows dll, *.exe* plików i sterowników urządzeń. Możesz uzyskać symbole dla systemów operacyjnych Windows, MDAC, IIS i ISA i [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] z publicznych serwerów symboli firmy Microsoft.

     **Serwery w sieci wewnętrznej lub na komputerze lokalnym symboli**: Twój zespół lub firmy można tworzyć serwery symboli dla własnych produktów i jako pamięci podręcznej dla symboli ze źródeł zewnętrznych. Możesz mieć serwer symboli na własnym komputerze.

     **Serwery symboli firm**: Inni dostawcy aplikacji systemu Windows i bibliotek mogą zapewnić dostęp do serwera symboli w Internecie.

     > [!WARNING]
     > Jeśli używasz serwera symboli innego niż publiczne serwery symboli firmy Microsoft, upewnij się, że serwer symboli i jego ścieżka są godne zaufania. Ponieważ pliki symboli mogą zawierać dowolny kod wykonywalny, może być narażony na zagrożenia bezpieczeństwa.

<a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a>
### <a name="configure-symbol-locations-and-loading-options"></a>Konfiguruj lokalizacje symboli i opcje ładowania

Na **narzędzia** > **opcje** > **debugowanie** > **symbole** strony, możesz:

- Określ, a następnie wybierz ścieżki wyszukiwania i serwery symboli dla Microsoft, Windows lub składników innych firm.
- Określ moduły lub nie chcesz, aby debuger ma automatycznie załadować symbole dla.
- Te ustawienia można zmienić podczas aktywnego debugowania. Zobacz [Zarządzanie symbole podczas debugowania](#manage-symbols-while-debugging).

**Aby określić lokalizacje symboli i opcje ładowania:**

1. W programie Visual Studio, otwórz **narzędzia** > **opcje** > **debugowanie** > **symbole** (lub **Debugowania** > **opcje** > **symbole**).

   ![Narzędzia &#45; opcje &#45; debugowanie &#45; strony symbole](media/dbg-options-symbols.png "narzędzia &#45; opcje &#45; debugowanie &#45; strony symboli")

2. W obszarze **symboli (.pdb) lokalizacji**,
   - Aby użyć **serwery symboli firmy Microsoft**, zaznacz pole wyboru.

   - Aby dodać nowe lokalizacja serwera symboli
     1. Wybierz **+** symboli na pasku narzędzi.
     1. W polu tekstowym, wpisz adres URL lub folder ścieżkę serwera symboli lub lokalizację symboli. Uzupełnianie instrukcji pomaga w znalezieniu właściwego formatu.

     >[!NOTE]
     >Przeszukiwany jest tylko określonego folderu. Należy dodać wpisy dla wszystkich podfolderów, które chcesz przeszukać.

   - Aby dodać nową lokalizację serwera symboli usługi VSTS
     1. Wybierz ![narzędzia&#47; opcje&#47; debugowanie&#47;nową ikonę serwera symboli](media/dbg_tools_options_foldersicon.png "narzędzia &#45; opcje &#45; debugowanie &#45; nową ikonę serwera symboli") ikonę na pasku narzędzi.
     1. W **nawiązywanie połączenia z serwera symboli usługi VSTS** okno dialogowe, wybierz jeden z serwerów symboli dostępne, a następnie wybierz pozycję **Connect**.

   - Aby zmienić kolejność ładowania lokalizacje symboli, użyj **Ctrl**+**się** i **Ctrl**+**dół**, lub **się** i **dół** ikony strzałek.
   - Aby edytować adres URL lub ścieżkę, kliknij dwukrotnie wpis, lub zaznacz ją i naciśnij klawisz **F2**.
   - Aby usunąć wpis, zaznacz go, a następnie wybierz **-** ikony.

3. (Opcjonalnie) Aby zwiększyć wydajność ładowania symboli, w obszarze **pamięci podręcznej symboli w tym katalogu**, wpisz ścieżkę folderu lokalnego, która może kopiować serwery symboli symbole.

   > [!NOTE]
   > Nie należy umieszczać w folderze chronionym, na przykład C:\Windows lub podfolder folderu pamięci podręcznej symboli. Zamiast tego użyj folderu przeznaczonego do odczytu i zapisu.

   > [!NOTE]
   > Dla projektów języka C++, jeśli masz `_NT_SYMBOL_PATH` środowiska zmienna jest ustawiona, jej spowoduje zastąpienie wartości ustawionych w obszarze **pamięci podręcznej symboli w tym katalogu**.

4. Określ moduły, które chcesz, aby debuger można załadować z **symboli (.pdb) lokalizacji** podczas uruchamiania.

   - Wybierz **Załaduj wszystkie moduły, chyba że wykluczone** (ustawienie domyślne), aby załadować wszystkie symbole dla wszystkich modułów w lokalizacji pliku symboli, z wyjątkiem wykluczania określonych modułów. Aby wykluczyć niektóre moduły, wybierz **Określ wyłączone moduły**, wybierz opcję **+** ikony, wpisz nazwy modułów, które chcesz wykluczyć i wybierz **OK**.

   - Aby załadować tylko te moduły, które określisz z lokalizacji plików symboli, wybierz **ładowania tylko określonych modułów**. Wybierz **Określ uwzględnione moduły**, wybierz opcję **+** ikony, wpisz nazwy modułów do uwzględnienia, a następnie wybierz pozycję **OK**. Pliki symboli dla innych modułów nie są ładowane.

5. Wybierz **OK**.

## <a name="other-symbol-options-for-debugging"></a>Inne opcje symboli debugowania

Można wybrać opcje dodatkowe symboli w **narzędzia** > **opcje** > **debugowanie** > **ogólne** (lub **debugowania** > **opcje** > **ogólne**):

- **Ładuj eksporty DLL (tylko natywne)**

  Ładowania biblioteki DLL Eksportowanie tabel dla języka C/C++. Aby uzyskać więcej informacji, zobacz [tabele eksportu bibliotek DLL](#use-dumpbin-exports). DLL odczytu informacji o eksportowaniu pewien narzut, dlatego ładowanie tabel eksportu jest domyślnie wyłączona. Można również użyć `dumpbin /exports` w wierszu polecenia kompilacji C/C++.

- **Włącz debugowanie na poziomie adresów** i **Pokaż deasemblację, jeśli źródło jest niedostępne**

  Zawsze wyświetli deasemblację, gdy nie znaleziono plików źródłowych lub symboli.

  ![Opcje &#47; debugowanie &#47; Opcje ogólne dezasemblacji](../debugger/media/dbg_options_general_disassembly_checkbox.png "opcje &#47; debugowanie &#47; Opcje ogólne dezasemblacji")
  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a>
- **Włącz obsługę serwera źródłowego**

  Aby pomóc w debugowaniu aplikacji, gdy brak kodu źródłowego na komputerze lokalnym, korzysta z serwera źródłowego lub *.pdb* pliku nie pasuje do kodu źródłowego. Serwer źródłowy przyjmuje żądania dotyczące plików i zwraca rzeczywiste pliki z kontroli źródła. Serwer źródłowy jest uruchamiany przy użyciu biblioteki DLL o nazwie *srcsrv.dll* odczytać aplikacji *.pdb* pliku. *.Pdb* plik zawiera wskaźniki do repozytorium kodu źródłowego, a także polecenia używane do pobierania kodu źródłowego z repozytorium.

  Można ograniczyć poleceń, *srcsrv.dll* można wykonać z poziomu aplikacji *.pdb* pliku przez wymienienie dozwolonych poleceń w pliku o nazwie *srcsrv.ini*. Miejsce *srcsrv.ini* pliku w tym samym folderze co *srcsrv.dll* i *devenv.exe*.

  >[!IMPORTANT]
  >Dowolne polecenia mogą być osadzone w aplikacji *.pdb* plików, więc Pamiętaj umieścić tylko te polecenia, które chcesz wykonać do *srcsrv.ini* pliku. Dowolne próba wykonania polecenia nie *srcsvr.ini* pliku spowoduje wyświetlenie okna dialogowego potwierdzenia. Aby uzyskać więcej informacji, zobacz [ostrzeżenie o zabezpieczeniach: Debuger musi wykonać polecenie niezaufane](../debugger/security-warning-debugger-must-execute-untrusted-command.md).
  >
  >Nie jest sprawdzana poprawność parametrów poleceń, więc należy być ostrożnym z poleceniami zaufanymi. Na przykład, jeśli zostanie wyświetlone *cmd.exe* w swojej *srcsrv.ini*, złośliwy użytkownik może określić parametry na *cmd.exe* , spowodowałoby, że niebezpieczne.

  Wybierz ten element i elementy podrzędne, które mają. **Zezwalaj serwerowi źródłowemu na częściowo zaufane zestawy (tylko kod zarządzany)** i **zawsze uruchamiaj niezaufane polecenia serwera źródłowego bez monitowania użytkownika o** mogą zwiększyć zagrożenia dla bezpieczeństwa.

  ![Włącz opcje serwera źródłowego](../debugger/media/dbg_options_general_enablesrcsrvr_checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")

## <a name="compiler-symbol-options"></a>Opcje kompilatora w symbolu

Podczas budowania projektu z programu Visual Studio IDE ze standardem **debugowania** konfigurację kompilacji, C++ i zarządzane kompilatory tworzyć pliki odpowiednich symboli dla kodu. Można również ustawić opcje kompilatora w kodzie.

### <a name="cc-options"></a>Opcje C/C++

- *VC\<x > .pdb* i  *\<Projekt > .pdb* plików

  A *.pdb* plik języka C/C++ jest tworzony podczas kompilowania przy użyciu [/zi lub/zi](/cpp/build/reference/z7-zi-zi-debug-information-format). W [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)], [/Fd](/cpp/build/reference/fd-program-database-file-name) opcji nazw *.pdb* kompilator tworzy plik. Podczas tworzenia projektu w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] przy użyciu IDE, **/Fd** opcji jest ustawiona na tworzenie *.pdb* plik o nazwie  *\<Projekt > .pdb*.

  Jeśli kompilujesz aplikację C/C++ za pomocą pliku reguł programu make i określisz **/zi** lub **/zi** bez użycia **/Fd**, kompilator tworzy dwa *.pdb*plików:

  - *VC\<x > .pdb*, gdzie  *\<x >* oznacza wersję Visual C++, na przykład *VC11.pdb*

    *VC\<x > .pdb* plik przechowuje wszystkie informacje o debugowaniu dla plików poszczególnych obiektów i znajduje się w tym samym katalogu co plik makefile projektu. Zawsze tworzy plik obiektu, kompilator C/C++ scala informacje debugowania do *VC\<x > .pdb*. Tak, nawet jeśli każdy plik źródłowy zawiera wspólne pliki nagłówkowe  *\<windows.h >* , definicje TypeDef z tych nagłówków są zapisywane tylko raz, a nie w każdym pliku obiektu. Informacje wstawione zawierają informacje o typie, ale nie zawiera informacji o symbolach, takich jak definicje funkcji.

  - *\<Projekt > .pdb*

    *\<Projekt > .pdb* plik przechowuje wszystkie informacje debugowania dla projektu *.exe* pliku i znajduje się w *\debug* podkatalogu. *\<Projekt > .pdb* plik zawiera pełne informacje o debugowaniu, w tym prototypy funkcji, nie tylko informacje o typie znalezione w *VC\<x > .pdb*.

  Zarówno *VC\<x > .pdb* i  *\<Projekt > .pdb* pliki zezwalają na aktualizacje przyrostowe. Konsolidator osadza także ścieżkę do *.pdb* pliki *.exe* lub *.dll* utworzonych plików.

- <a name="use-dumpbin-exports"></a>Tabel eksportu bibliotek DLL

  Użyj `dumpbin /exports` Aby wyświetlić dostępne w tabeli eksportu biblioteki DLL symbole. Informacje symboliczne z tabel eksportu bibliotek DLL może być przydatne do pracy z Windows wiadomości, procedur Windows (WindowProcs), COM obiektów, organizowanie lub dowolną biblioteką DLL, nie masz symboli dla. Symbole są dostępne dla dowolnej 32-bitowej systemowej biblioteki DLL. Wywołania są wymienione w kolejności wywołań, z bieżącą funkcją (najgłębiej zagnieżdżoną) na początku.

  Czytając `dumpbin /exports` danych wyjściowych widać nazwy funkcji Porównaj, w tym znaki inne niż alfanumeryczne. Wyświetlanie nazwy funkcji Porównaj przydaje się do Ustawianie punktu przerwania funkcji, ponieważ nazwy funkcji mogą być obcięte gdzie indziej w debugerze. Aby uzyskać więcej informacji, zobacz [dumpbin/EXPORTS](/cpp/build/reference/dash-exports).

### <a name="net-framework-options"></a>Opcje .NET Framework

Tworzenie za pomocą **/debug** utworzyć *.pdb* pliku. Możesz tworzyć aplikacje przy użyciu **/Debug: full** lub **/debug:pdbonly**. Kompilowanie z użyciem **/Debug: full** generuje kod do debugowania. Kompilowanie z użyciem **/debug:pdbonly** generuje *.pdb* plików, ale nie generuje `DebuggableAttribute` który informuje kompilator JIT, dostępne są informacje debugowania. Użyj **/debug:pdbonly** Jeśli chcesz wygenerować *.pdb* plików w wersji kompilacji, że nie chcesz żeby były debugowalne. Aby uzyskać więcej informacji, zobacz [/Debug (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) lub [/Debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug).

### <a name="web-applications"></a>Aplikacje internetowe

Ustaw *web.config* pliku tryb debugowania aplikacji ASP.NET. Tryb debugowania powoduje, że ASP.NET generuje symbole dla dynamicznie generowanych plików i umożliwia debugerowi dołączenie do aplikacji ASP.NET. Program Visual Studio automatycznie ustawia to podczas uruchamiania debugowania, jeśli projekt jest utworzony z szablonu projektów sieci web.

## <a name="manage-symbols-while-debugging"></a>Zarządzanie symbole podczas debugowania

Możesz użyć **modułów**, **stos wywołań**, **lokalne**, **Autos**, lub dowolnego **Obejrzyj** okna, aby załadować symbole lub zmień opcje symboli podczas debugowania. Aby uzyskać więcej informacji, zobacz [zapoznać się z jak dołącza debuger do swojej aplikacji](../debugger/debugger-tips-and-tricks.md#modules_window).

### <a name="use-the-modules-window"></a>Korzystanie z okna modułów

Podczas debugowania, **modułów** okno zawiera moduły kodu, Debuger jest traktowanie jako kod użytkownika lub Mój kod i ich symboli podczas ładowania stanu. Również monitorować stan ładowania symboli, załaduj symbole i zmień opcje symboli w **modułów** okna.

**Do monitorowania lub zmienić opcje lub lokalizacje symboli podczas debugowania:**

1. Aby otworzyć **modułów** oknie podczas debugowania, wybierz opcję **debugowania** > **Windows** > **modułów**.
1. W **modułów** okna, kliknij prawym przyciskiem myszy **stan symboli** lub **pliku symboli** nagłówków lub dowolny moduł.
1. W menu kontekstowym wybierz jedną z następujących opcji:

|Opcja|Opis|
|------------|-----------------|
|**Załaduj symbole**|Pojawia się dla modułów przy użyciu pominięto, nie został odnaleziony lub nie załadowano symboli. Próbuje załadować symbole z lokalizacji określonej na **opcje** > **debugowanie** > **symbole** strony. Jeśli nie znaleziono lub nie załadowano pliku symboli, uruchamia **Eksploratora plików** , dzięki czemu można określić nową lokalizację do wyszukiwania.|
|**Informacje o ładowaniu symboli**|Wskazuje lokalizację załadowanego pliku symboli lub lokalizacje, które były przeszukiwane, jeśli debuger nie może odnaleźć pliku.|
|**Ustawienia symboli**|Otwiera **opcje** > **debugowanie** > **symbole** strony, w którym można edytować i dodawać lokalizacje symboli.|
|**Zawsze ładuj automatycznie**|Dodaje plik wybrany symbol do listy plików, które są ładowane automatycznie przez debuger.|

### <a name="use-the-no-symbols-loadedno-source-loaded-pages"></a>Korzystanie ze stron nie Loaded/No źródła załadowano symboli

Istnieje kilka sposobów, aby debuger wszedł do kodu, który nie ma dostępnych plików symboli lub źródłowych:

- Wejdź do kodu.
- Podziel na kod z punktu przerwania lub wyjątku.
- Przełącz do innego wątku.
- Zmiana ramek stosu przez dwukrotne kliknięcie ramki w **stos wywołań** okna.

Gdy tak się stanie, debuger wyświetla **Brak załadowanych symboli** lub **Brak załadowanego źródła** strony, aby pomóc Ci znaleźć i załadować niezbędne symbole lub źródła.

 ![Strona nie załadowano symboli](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")

**Na potrzeby pomocy Znajdź i załaduj symbole Brak strony dokumentu nie załadowano symboli:**

- Aby zmienić ścieżki wyszukiwania, wybierz niezaznaczoną ścieżkę lub wybierz **nową ścieżkę** lub **Nowa ścieżka usługi VSTS** i wprowadź lub wybierz nową ścieżkę. Wybierz **obciążenia** wyszukać ponownie ścieżki i załadować plik symbolu, jeśli zostanie znaleziony.
- Aby zastąpić wszelkie opcje symbolu i ponów próbę ścieżki wyszukiwania, wybierz **Przeglądaj i Przeszukuj \<nazwę pliku wykonywalnego >** . Plik symboli jest ładowany, jeśli zostanie znaleziony, lub **Eksploratora plików** zostanie otwarty, można ręcznie wybrać plik symboli.
- Aby otworzyć **opcje** > **debugowanie** > **symbole** wybierz opcję **Zmień ustawienia symboli**.
- Aby pokazać demontaż w nowym oknie jeden raz, wybierz pozycję **wyświetlić dezasemblację**, lub wybierz **okna dialogowego Opcje** ustawić opcję, aby zawsze pokazywać deasemblację, gdy nie znaleziono plików źródłowych lub symboli.
- Aby wyświetlić lokalizacje przeszukiwane i wynik, rozwiń **informacje o ładowaniu symboli**.

Jeśli narzędzie debugger znajdzie *.pdb* pliku po wykonaj jedną z opcji, a można pobrać pliku źródłowego, korzystając z informacji podanych w *.pdb* pliku, wyświetlane źródło. W przeciwnym razie wyświetla **Brak załadowanego źródła** strona, która opisuje problem, wraz z łączami do akcji, które mogą rozwiązać problem.

**Aby dodać ścieżki wyszukiwania pliku źródłowego do rozwiązania:**

Określ lokalizacje, debuger wyszukuje pliki źródłowe i wykluczenie określonych plików w wyniku wyszukiwania.

1. Wybierz rozwiązanie w **Eksploratora rozwiązań**, a następnie wybierz pozycję **właściwości** ikonę, naciśnij klawisz **Alt**+**Enter**, lub Kliknij prawym przyciskiem myszy i wybierz **właściwości**.

1. Wybierz **pliki źródłowe debugowania**.

1. W obszarze **katalogi zawierające kod źródłowy**, wpisz lub wybierz lokalizacji kodu źródłowego do przeszukania. Użyj **nowy wiersz** ikonę, aby dodać więcej lokalizacji **się** i **dół** ikony strzałek, aby zmienić ich kolejność lub **X** ikonę, aby je usunąć.

   >[!NOTE]
   >Debuger przeszukuje tylko określony katalog. Musisz dodać wpisy do wszystkich podkatalogów, które chcesz przeszukać.

1. W obszarze **nie wyszukuj tych plików źródłowych**, wpisz nazwy plików źródłowych, które mają zostać wykluczone z wyszukiwania.

1. Wybierz **OK** lub **zastosować**.

## <a name="see-also"></a>Zobacz także
- [Pliki symboli i ustawienia symboli programu Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)

- [Zdalnym zmiany w programie Visual Studio 2012 i 2013 ładowaniu symboli .NET](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)
