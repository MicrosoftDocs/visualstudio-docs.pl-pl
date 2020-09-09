---
title: Ustawianie symboli (. pdb) i plików źródłowych w debugerze
description: Dowiedz się, jak konfigurować symbole i pliki źródłowe w programie Visual Studio oraz zarządzać nimi
ms.custom: ''
ms.date: 10/31/2019
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
ms.openlocfilehash: eceffab5b8c179734b1abb5f1005c240912115f1
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2020
ms.locfileid: "89599584"
---
# <a name="specify-symbol-pdb-and-source-files-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Określanie symboli (. pdb) i plików źródłowych w debugerze programu Visual Studio (C#, C++, Visual Basic, F #)

Pliki bazy danych programu (*. pdb*), nazywane również plikami symboli, identyfikatory map i instrukcje w kodzie źródłowym projektu do odpowiednich identyfikatorów i instrukcje w skompilowanych aplikacjach. Te pliki mapowania łączą debuger z kodem źródłowym, co umożliwia debugowanie.

Podczas kompilowania projektu z programu Visual Studio IDE przy użyciu standardowej konfiguracji kompilacji debugowania kompilator tworzy odpowiednie pliki symboli. W tym artykule opisano sposób zarządzania plikami symboli w środowisku IDE, na przykład [określania lokalizacji symboli w opcjach debugera](#BKMK_Specify_symbol_locations_and_loading_behavior), [sprawdzania stanu ładowania symboli](#work-with-symbols-in-the-modules-window) podczas debugowania oraz [ustawiania opcji symboli w kodzie](#compiler-symbol-options).

Szczegółowe wyjaśnienie plików symboli można znaleźć w następujących tematach:

- [Omówienie plików symboli i ustawień symboli programu Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)

- [Dlaczego program Visual Studio wymaga, aby pliki symboli debugera były dokładnie zgodne z plikami binarnymi, z których zostały skompilowane?](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with)

## <a name="how-symbol-files-work"></a>Jak działają pliki symboli

Plik *. pdb* przechowuje informacje o debugowaniu i stanie projektu, które umożliwiają łączenie przyrostowe konfiguracji debugowania aplikacji. Debuger programu Visual Studio używa plików *. pdb* , aby określić dwa kluczowe fragmenty informacji podczas debugowania:

* Nazwa pliku źródłowego i numer wiersza do wyświetlenia w środowisku IDE programu Visual Studio.
* Miejsce, w którym aplikacja ma zostać zatrzymana dla punktu przerwania.

Pliki symboli zawierają również lokalizację plików źródłowych i opcjonalnie serwer, z którego można je pobrać.

Debuger *ładuje tylko pliki. pdb* , które dokładnie pasują do plików *. pdb* utworzonych podczas kompilowania aplikacji (czyli oryginalnych plików *. pdb* lub kopii). To [dokładne duplikowanie](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with) jest konieczne, ponieważ układ aplikacji może się zmieniać, nawet jeśli sam kod nie został zmieniony.

> [!TIP]
> Aby debugować kod poza kodem źródłowym projektu, taki jak kod systemu Windows lub kod innej firmy, należy określić lokalizację plików *. pdb* kodu zewnętrznego (i opcjonalnie pliki źródłowe), które muszą być dokładnie zgodne z kompilacjami w aplikacji.

## <a name="symbol-file-locations-and-loading-behavior"></a>Lokalizacje plików symboli i zachowanie ładowania

Podczas debugowania projektu w programie Visual Studio IDE debuger automatycznie ładuje pliki symboli, które znajdują się w folderze projektu.

> [!NOTE]
> Podczas debugowania kodu zarządzanego na urządzeniu zdalnym wszystkie pliki symboli muszą znajdować się na komputerze lokalnym lub w lokalizacji [określonej w opcjach debugera](#BKMK_Specify_symbol_locations_and_loading_behavior).

Debuger szuka również plików symboli w następujących lokalizacjach:

1. Lokalizacja określona w pliku DLL lub plik wykonywalny (*. exe*).

   Domyślnie, jeśli na komputerze została skompilowana Biblioteka DLL lub plik *. exe* , konsolidator umieści pełną ścieżkę i nazwę pliku *. pdb* w pliku DLL lub *exe* . Debuger sprawdza, czy plik symboli istnieje w tej lokalizacji.

2. Ten sam folder, w którym znajduje się plik DLL lub *exe* .

3. Wszystkie lokalizacje określone w opcjach debugera dla plików symboli. Aby dodać i włączyć lokalizacje symboli, zobacz [Konfigurowanie lokalizacji symboli i opcji ładowania](#BKMK_Specify_symbol_locations_and_loading_behavior).

   - Każdy lokalny folder pamięci podręcznej symboli.

   - Określona sieć, Internet lub lokalne serwery symboli i lokalizacje, takie jak serwery symboli firmy Microsoft, jeśli zostały wybrane. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] może pobierać pliki symboli debugowania z serwerów symboli, które implementują `symsrv` protokół. [Program Visual Studio Team Foundation Server](/azure/devops/pipelines/tasks/build/index-sources-publish-symbols) i [narzędzia debugowania dla systemu Windows](/windows-hardware/drivers/debugger/index) to dwa narzędzia, które mogą korzystać z serwerów symboli.

     Serwery symboli, których można użyć, to m.in.:

     **Publiczne serwery symboli Microsoft**: Aby debugować awarię, która występuje podczas wywoływania biblioteki DLL systemu lub innej biblioteki, często potrzebujesz plików system *. pdb* . Pliki system *. pdb* zawierają symbole dla bibliotek DLL systemu Windows, plików *exe* i sterowników urządzeń. Możesz uzyskać symbole dla systemów operacyjnych Windows, MDAC, IIS, ISA i .NET z publicznych serwerów symboli firmy Microsoft.

     **Serwery symboli w sieci wewnętrznej lub na komputerze lokalnym**: zespół lub firma mogą tworzyć serwery symboli dla własnych produktów i jako pamięć podręczną dla symboli ze źródeł zewnętrznych. Możesz mieć serwer symboli na własnym komputerze.

     **Serwery symboli innych firm**: dostawcy zewnętrznych aplikacji i bibliotek systemu Windows mogą zapewnić dostęp do serwera symboli w Internecie.

     > [!WARNING]
     > Jeśli używasz serwera symboli innego niż publiczne serwery symboli Microsoft, upewnij się, że serwer symboli i jego ścieżka są godne zaufania. Ponieważ pliki symboli mogą zawierać dowolny kod wykonywalny, może być narażony na zagrożenia bezpieczeństwa.

<a name="BKMK_Specify_symbol_locations_and_loading_behavior"></a>
### <a name="configure-symbol-locations-and-loading-options"></a>Konfigurowanie lokalizacji symboli i opcji ładowania

Na stronie **Tools**  >  **Opcje**narzędzi  >  **debugowania**  >  **symboli** można wykonać następujące instrukcje:

- Określ i wybierz ścieżki wyszukiwania i serwery symboli dla Microsoft, Windows lub składników innych firm.
- Określ moduły, które możesz wykonać lub nie chcesz, aby debuger automatycznie ładował symbole dla programu.
- Zmień te ustawienia podczas aktywnego debugowania. Zobacz [Zarządzanie symbolami podczas debugowania](#manage-symbols-while-debugging).

**Aby określić lokalizacje symboli i opcje ładowania:**

1. W programie Visual Studio Otwórz pozycję **Narzędzia**  >  **Opcje**  >  **debugowania**  >  **symbole** (lub opcje **debugowania**  >  **Options**  >  **symbole**).

2. W obszarze **lokalizacji pliku symboli (. pdb)**
   - Aby korzystać z **serwerów symboli firmy Microsoft** lub **serwera symboli NuGet.org**, zaznacz pole wyboru.

   - Aby dodać nową lokalizację serwera symboli,
     1. Wybierz **+** symbol na pasku narzędzi.
     1. Wpisz adres URL (http), udział sieciowy lub ścieżkę lokalną serwera symboli lub lokalizacji symboli w polu tekstowym. Uzupełnianie instrukcji pomaga w znalezieniu właściwego formatu.

     ![Narzędzia &#45; opcje &#45; debugowanie &#45; symbole](media/dbg-options-symbols.gif "Narzędzia &#45; opcje &#45; debugowanie &#45; symbole")

     >[!NOTE]
     >Przeszukiwany jest tylko określony folder. Musisz dodać wpisy do wszystkich podfolderów, które chcesz przeszukać.

   - Aby dodać nową lokalizację serwera symboli VSTS,
     1. Wybierz ![opcje&#47; narzędzia&#47; debuguj&#47;symbole ikona nowy serwer](media/dbg_tools_options_foldersicon.png "Narzędzia &#45; opcje &#45; debugowania &#45; symbole nowy serwer") na pasku narzędzi.
     1. W oknie dialogowym **łączenie z serwerem symboli VSTS** wybierz jeden z dostępnych serwerów symboli, a następnie wybierz pozycję **Połącz**.

   - Aby zmienić kolejność ładowania dla lokalizacji symboli, użyj **klawiszy CTRL** + **up** i **Ctrl** + **Down**albo ikon strzałek w **górę** i **w dół** .
   - Aby edytować adres URL lub ścieżkę, kliknij dwukrotnie wpis lub wybierz go, a następnie naciśnij klawisz **F2**.
   - Aby usunąć wpis, zaznacz go, a następnie wybierz **-** ikonę.

3. Obowiązkowe Aby poprawić wydajność ładowania symboli, w obszarze **symbole pamięci podręcznej w tym katalogu**wpisz ścieżkę do folderu lokalnego, do której serwery symboli mogą kopiować symbole.

   > [!NOTE]
   > Nie umieszczaj lokalnej pamięci podręcznej symboli w chronionym folderze, takim jak C:\Windows lub podfolder. Zamiast tego użyj folderu przeznaczonego do odczytu i zapisu.

   > [!NOTE]
   > W przypadku projektów języka C++, jeśli istnieje `_NT_SYMBOL_PATH` zmienna środowiskowa, spowoduje to zastąpienie wartości ustawionej w obszarze **symbole pamięci podręcznej w tym katalogu**.

4. Określ moduły, które mają być ładowane przez debuger z **lokalizacji pliku symboli (. pdb)** podczas uruchamiania.

   - Wybierz pozycję **Załaduj wszystkie moduły, chyba że zostanie wykluczona** (domyślnie), aby załadować wszystkie symbole dla wszystkich modułów w lokalizacji pliku symboli, z wyjątkiem modułów, które zostały wykluczane. Aby wykluczyć niektóre moduły, wybierz pozycję **Określ wykluczone moduły**, wybierz **+** ikonę, wpisz nazwy modułów do wykluczenia, a następnie wybierz **przycisk OK**.

   - Aby załadować tylko moduły określone z lokalizacji pliku symboli, wybierz opcję **Załaduj tylko określone moduły**. Wybierz pozycję **Określ uwzględnione moduły**, wybierz **+** ikonę, wpisz nazwy modułów do uwzględnienia, a następnie wybierz przycisk **OK**. Pliki symboli dla innych modułów nie są ładowane.

5. Wybierz pozycję **OK**.

## <a name="other-symbol-options-for-debugging"></a>Inne opcje symboli na potrzeby debugowania

Możesz wybrać dodatkowe opcje symboli w opcji **Narzędzia**  >  **Options**  >  **debugowanie**  >  **Ogólne** (lub opcje **debugowania**  >  **Options**  >  **Ogólne**):

- **Załaduj eksporty biblioteki DLL (tylko kod natywny)**

  Ładuje tabele eksportu DLL dla C/C++. Aby uzyskać szczegółowe informacje, zobacz [tabele eksportu biblioteki DLL](#use-dumpbin-exports). Odczytywanie informacji o eksporcie z biblioteki DLL obejmuje pewne obciążenie, więc ładowanie tabel eksportu jest domyślnie wyłączone. Można również użyć `dumpbin /exports` w wierszu polecenia kompilacji C/C++.

- **Włącz debugowanie na poziomie adresu** i **Pokaż demontaż, jeśli źródło jest niedostępne**

  Zawsze pokazuje demontaż, gdy nie znaleziono plików źródłowych lub symboli.

  ![Opcje &#47; debugowanie &#47; ogólne opcje demontażu](../debugger/media/dbg_options_general_disassembly_checkbox.png "Opcje &#47; debugowanie &#47; ogólne opcje demontażu")
  <a name="BKMK_Use_symbol_servers_to_find_symbol_files_not_on_your_local_machine"></a>
- **Włącz obsługę serwera źródłowego**

  Używa serwera źródłowego do debugowania aplikacji, gdy na komputerze lokalnym nie ma kodu źródłowego lub plik *. pdb* nie pasuje do kodu źródłowego. Serwer źródłowy przyjmuje żądania dotyczące plików i zwraca rzeczywiste pliki z kontroli źródła. Serwer źródłowy jest uruchamiany przy użyciu biblioteki DLL o nazwie *srcsrv.dll* , aby odczytać plik *. pdb* aplikacji. Plik *. pdb* zawiera wskaźniki do repozytorium kodu źródłowego, a także polecenia używane do pobierania kodu źródłowego z repozytorium.

  Można ograniczyć polecenia, które *srcsrv.dll* mogą być wykonywane z pliku *. pdb* aplikacji, wyświetlając listę dozwolonych poleceń w pliku o nazwie *srcsrv.ini*. Umieść plik *srcsrv.ini* w tym samym folderze co *srcsrv.dll* i *devenv.exe*.

  >[!IMPORTANT]
  >Dowolne polecenia mogą być osadzone w pliku *. pdb* aplikacji, więc upewnij się, że umieścisz tylko te polecenia, które chcesz wykonać w pliku *srcsrv.ini* . Każda próba wykonania polecenia, które nie znajduje się w pliku *srcsvr.ini* , spowoduje wyświetlenie okna dialogowego potwierdzenia. Aby uzyskać więcej informacji, zobacz [Ostrzeżenie o zabezpieczeniach: debuger musi wykonać polecenie niezaufane](../debugger/security-warning-debugger-must-execute-untrusted-command.md).
  >
  >Nie jest sprawdzana poprawność parametrów poleceń, więc należy być ostrożnym z poleceniami zaufanymi. Na przykład jeśli na liście *srcsrv.ini*wymieniono *cmd.exe* , złośliwy użytkownik może określić parametry *cmd.exe* , które byłyby niebezpieczne.

  Wybierz ten element i elementy podrzędne, które chcesz. **Zezwalaj na serwer źródłowy dla zestawów częściowej relacji zaufania (tylko zarządzany)** i **Zawsze uruchamiaj niezaufane polecenia serwera źródłowego bez monitowania** mogą zwiększyć zagrożenia bezpieczeństwa.

  ![Włącz opcje serwera źródłowego](../debugger/media/dbg_options_general_enablesrcsrvr_checkbox.png "DBG_Options_General_EnableSrcSrvr_checkbox")

## <a name="compiler-symbol-options"></a>Opcje symboli kompilatora

Podczas kompilowania projektu z poziomu środowiska IDE programu Visual Studio przy użyciu standardowej konfiguracji kompilacji do **debugowania** , kompilatory C++ i konstruktory zarządzane tworzą odpowiednie pliki symboli dla kodu. Możesz również ustawić opcje kompilatora w kodzie.

### <a name="net-options"></a>Opcje .NET

Kompiluj z opcją **/Debug** , aby utworzyć plik *. pdb* . Możesz tworzyć aplikacje za pomocą **przełącznika/Debug: Full** lub **/Debug: pdbonly**. Kompilowanie za pomocą **/Debug: Full** generuje kod możliwością debugowania. Kompilowanie za pomocą **/Debug: pdbonly** generuje pliki *. pdb* , ale nie generuje tego, `DebuggableAttribute` który informuje kompilator JIT, że dostępne są informacje debugowania. Użyj **/Debug: pdbonly** , jeśli chcesz wygenerować pliki *. pdb* dla kompilacji wydania, której nie chcesz możliwością debugowania. Aby uzyskać więcej informacji, zobacz [/debug (opcje kompilatora C#)](/dotnet/csharp/language-reference/compiler-options/debug-compiler-option) lub [/debug (Visual Basic)](/dotnet/visual-basic/reference/command-line-compiler/debug).

### <a name="cc-options"></a>Opcje C/C++

- Pliki *VC \<x> . pdb* i * \<project> . pdb*

  Plik *. pdb* dla C/C++ jest tworzony podczas kompilowania z [/Zi lub/Zi](/cpp/build/reference/z7-zi-zi-debug-information-format). W programie [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] opcja [/FD](/cpp/build/reference/fd-program-database-file-name) nazywa plik *. pdb* tworzony przez kompilator. Podczas tworzenia projektu w programie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] przy użyciu środowiska IDE opcja **/FD** jest ustawiona na tworzenie pliku *. pdb* o nazwie * \<project> . pdb*.

  W przypadku kompilowania aplikacji C/C++ przy użyciu pliku reguł programu make i określenia **/Zi** lub **/Zi** bez użycia **/FD**, kompilator tworzy dwa pliki *. pdb* :

  - *VC \<x> . pdb*, gdzie *\<x>* reprezentuje wersję kompilatora języka Microsoft C++, na przykład *VC11. pdb*

    Plik *VC \<x> . pdb* przechowuje wszystkie informacje o debugowaniu dla poszczególnych plików obiektów i znajduje się w tym samym katalogu, w którym znajduje się projekt reguł programu make. Za każdym razem, gdy tworzy plik obiektu, kompilator C/C++ scala informacje debugowania do pliku *VC \<x> . pdb*. Nawet jeśli każdy plik źródłowy zawiera wspólne pliki nagłówkowe, takie jak *\<windows.h>* , definicje TypeDef z tych nagłówków są przechowywane tylko raz, a nie w każdym pliku obiektu. Wstawione informacje zawierają informacje o typie, ale nie zawierają informacji o symbolach, takich jak definicje funkcji.

  - *\<project>. pdb*

    Plik * \<project> . pdb* przechowuje wszystkie informacje debugowania dla pliku *. exe* projektu i znajduje się w podkatalogu *\debug.* . Plik * \<project> . pdb* zawiera pełne informacje o debugowaniu, w tym prototypy funkcji, a nie tylko informacje o typie Znalezione w pliku *VC \<x> . pdb*.

  Pliki *VC \<x> . pdb* i * \<project> . pdb* zezwalają na aktualizacje przyrostowe. Konsolidator osadza także ścieżkę do plików *. pdb* w pliku *. exe* lub *. dll* , który tworzy.

- <a name="use-dumpbin-exports"></a>Tabele eksportu biblioteki DLL

  Użyj, `dumpbin /exports` Aby zobaczyć symbole dostępne w tabeli eksportu biblioteki DLL. Informacje symboliczne z tabel eksportu bibliotek DLL mogą być przydatne podczas pracy z komunikatami systemu Windows, procedurami systemu Windows (WindowProcs), obiektami COM, kierowaniem lub dowolną biblioteką DLL, dla których nie masz symboli. Symbole są dostępne dla dowolnej 32-bitowej systemowej biblioteki DLL. Wywołania są wymienione w kolejności wywołań, z bieżącą funkcją (najgłębiej zagnieżdżoną) na początku.

  Odczytując `dumpbin /exports` dane wyjściowe, można zobaczyć dokładną nazwę funkcji, w tym znaki inne niż alfanumeryczne. Oglądanie dokładnych nazw funkcji jest przydatne do ustawiania punktu przerwania w funkcji, ponieważ nazwy funkcji mogą być obcinane w innym miejscu w debugerze. Aby uzyskać więcej informacji, zobacz [polecenia DUMPBIN/exports](/cpp/build/reference/dash-exports).

### <a name="web-applications"></a>Aplikacje internetowe

Ustaw *web.config* plik aplikacji ASP.NET na tryb debugowania. Tryb debugowania powoduje, że ASP.NET generuje symbole dla dynamicznie generowanych plików i umożliwia debugerowi dołączenie do aplikacji ASP.NET. Program Visual Studio automatycznie ustawia to podczas uruchamiania debugowania, jeśli projekt został utworzony z szablonu projektów sieci Web.

## <a name="manage-symbols-while-debugging"></a>Zarządzaj symbolami podczas debugowania

Można użyć **modułów**, **stos wywołań**, **zmiennych lokalnych**, **autostarts**lub dowolnego okna **czujki** do ładowania symboli lub zmiany opcji symboli podczas debugowania. Aby uzyskać więcej informacji, zobacz artykuł [Uzyskaj więcej znajomości, jak debuger dołącza do aplikacji](../debugger/debugger-tips-and-tricks.md#modules_window).

### <a name="work-with-symbols-in-the-modules-window"></a>Pracuj z symbolami w oknie modułów

Podczas debugowania w oknie **moduły** są wyświetlane moduły kodu, które debuger jest traktowany jako kod użytkownika lub mój kod oraz stan ładowania symboli. Możesz również monitorować stan ładowania symboli, Załaduj symbole i zmienić opcje symboli w oknie **moduły** .

**Aby monitorować lub zmieniać lokalizacje lub opcje symboli podczas debugowania:**

1. Aby otworzyć okno **moduły** , podczas debugowania wybierz kolejno opcje **Debuguj**  >  moduły**systemu Windows**  >  **Modules**.
1. W oknie **moduły** kliknij prawym przyciskiem myszy pozycję **symbole** lub nagłówki **pliku symboli** lub dowolnego modułu.
1. W menu kontekstowym wybierz jedną z następujących opcji:

|Opcja|Opis|
|------------|-----------------|
|**Załaduj symbole**|Pojawia się dla modułów z pominiętymi, nieznalezionymi lub nie załadowanymi symbolami. Próbuje załadować symbole z lokalizacji określonych na stronie **Opcje**  >  **debugowania**  >  **symboli** . Jeśli plik symboli nie zostanie znaleziony lub nie został załadowany, program uruchamia **Eksploratora plików** , aby można było określić nową lokalizację do przeszukania.|
|**Informacje dotyczące załadowania symboli**|Pokazuje lokalizację załadowanego pliku symboli lub lokalizacje, które były przeszukiwane, Jeśli debuger nie może znaleźć pliku.|
|**Ustawienia symboli**|Otwiera stronę **Opcje**  >  **debugowania**  >  **symboli** , w której można edytować i dodawać lokalizacje symboli.|
|**Zawsze ładuj automatycznie**|Dodaje wybrany plik symbolu do listy plików, które są automatycznie ładowane przez debuger.|

### <a name="use-the-no-symbols-loadedno-source-loaded-pages"></a>Użyj stron nie załadowanych symboli/nie załadowano źródła

Istnieje kilka sposobów, aby debuger mógł przerwać do kodu, który nie ma dostępnych plików symboli lub źródłowych:

- Wkrocz do kodu.
- Przerwij do kodu z punktu przerwania lub wyjątku.
- Przejdź do innego wątku.
- Zmień ramkę stosu przez dwukrotne kliknięcie ramki w oknie **stosu wywołań** .

W takim przypadku debuger wyświetli **nie załadowane symbole** lub **nie załadowano źródłowych** stron, aby znaleźć i załadować niezbędne symbole lub źródło.

 ![Nie załadowano żadnych symboli na stronie](../debugger/media/dbg-nosymbolsloaded.png "DBG_NoSymbolsLoaded")

**Aby użyć strony "Brak załadowanych symboli", aby pomóc znaleźć i załadować brakujące symbole:**

- Aby zmienić ścieżkę wyszukiwania, wybierz niewybraną ścieżkę lub wybierz opcję **Nowa ścieżka** lub Nowa ścieżka **VSTS** i wprowadź lub wybierz nową ścieżkę. Wybierz pozycję **Załaduj** , aby ponownie przeszukać ścieżki i załadować plik symboli, jeśli zostanie znaleziony.
- Aby zastąpić wszelkie opcje symboli i ponowić próbę ścieżki wyszukiwania, wybierz pozycję **Przeglądaj \<executable-name> i Znajdź **. Plik symboli jest ładowany, jeśli zostanie odnaleziony, lub otwiera się **Eksplorator plików** , aby można było ręcznie wybrać plik symboli.
- Aby otworzyć stronę **Opcje**  >  **debugowania**  >  **symboli** , wybierz pozycję **Zmień ustawienia symboli**.
- Aby wyświetlić demontaż w nowym oknie jeden raz, wybierz pozycję **Wyświetl demontaż**lub wybierz opcję **okno dialogowe Opcje** , aby ustawić opcję Zawsze wyświetlaj demontaż, gdy pliki źródłowe lub symboliczne nie zostaną znalezione.
- Aby wyświetlić przeszukiwane lokalizacje i wyniki, rozwiń pozycję **Informacje o ładowaniu symboli**.

Jeśli debuger odnajdzie plik *. pdb* po wykonaniu jednej z opcji i może pobrać plik źródłowy przy użyciu informacji w pliku *. pdb* , wyświetla źródło. W przeciwnym razie wyświetlana jest strona **nie załadowana ze źródłem** , która opisuje problem, z linkami do akcji, które mogą rozwiązać problem.

**Aby dodać ścieżki wyszukiwania plików źródłowych do rozwiązania:**

Możesz określić lokalizacje, w których debuger wyszukuje pliki źródłowe, i wykluczać określone pliki z wyszukiwania.

1. Wybierz rozwiązanie w **Eksplorator rozwiązań**, a następnie wybierz ikonę **Właściwości** , naciśnij klawisz **Alt** + **Enter**lub kliknij prawym przyciskiem myszy i wybierz pozycję **Właściwości**.

1. Wybierz pozycję **Debuguj pliki źródłowe**.

1. W obszarze **katalogi zawierające kod źródłowy**wpisz lub Wybierz lokalizacje kodu źródłowego do wyszukania. Użyj ikony **nowy wiersz** , aby dodać więcej lokalizacji, ikon strzałek w **górę** i **w dół** , aby zmienić ich kolejność, lub ikonę **X** , aby je usunąć.

   >[!NOTE]
   >Debuger przeszukuje tylko określony katalog. Musisz dodać wpisy do wszystkich podkatalogów, które chcesz przeszukać.

1. W obszarze nie **wyszukuj tych plików źródłowych**wpisz nazwy plików źródłowych do wykluczenia z wyszukiwania.

1. Wybierz **przycisk OK** lub **Zastosuj**.

## <a name="see-also"></a>Zobacz też
- [Omówienie plików symboli i ustawień symboli programu Visual Studio](https://devblogs.microsoft.com/devops/understanding-symbol-files-and-visual-studios-symbol-settings/)

- [Zdalne ładowanie symboli .NET w programie Visual Studio 2012 i 2013](https://devblogs.microsoft.com/devops/net-remote-symbol-loading-changes-in-visual-studio-2012-and-2013/)