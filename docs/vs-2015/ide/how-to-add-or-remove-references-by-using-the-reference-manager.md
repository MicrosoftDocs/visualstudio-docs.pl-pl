---
title: 'Instrukcje: Dodawanie lub usuwanie odwołań za pomocą Menedżera odwołań | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ReferenceManager
helpviewer_keywords:
- Visual C# projects, references
- references [Visual Studio], adding
- assemblies [Visual Studio], references
- Visual Basic projects, references
- project references, adding
- referencing components, adding references
- project references, removing
- referencing assemblies
- referencing components, removing references
- references [Visual Studio], removing
- referencing components, assemblies not listed
ms.assetid: 1aabb520-99b0-46c6-9368-21b4d84793eb
caps.latest.revision: 48
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d0763f2cf86d94f96f6f9c907ee306c731994f22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852089"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Porady: dodawanie i usuwanie odwołań za pomocą Menedżera odwołań
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą okna dialogowego **Menedżer odwołań** można dodawać odwołania do składników, które zostały opracowane przez firmę Microsoft lub inną firmę, oraz zarządzać nimi. Jeśli tworzysz aplikację uniwersalną systemu Windows, projekt automatycznie odwołuje się do wszystkich poprawnych Windows SDK bibliotek DLL. Jeśli tworzysz aplikację platformy .NET, projekt automatycznie odwołuje się mscorlib.dll. Niektóre interfejsy API platformy .NET są udostępniane w składnikach, które trzeba dodać ręcznie. Odwołania do składników COM lub składników niestandardowych należy dodać ręcznie.

## <a name="adding-and-removing-a-reference"></a>Dodawanie i usuwanie odwołań

#### <a name="to-add-a-reference"></a>Aby dodać odwołanie

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł odwołania i wybierz polecenie **Dodaj odwołanie**.

2. Określ odwołania do dodania, a następnie wybierz przycisk **OK** .

   Zostanie otwarty **Menedżer odwołań** i zostanie wyświetlona lista dostępnych odwołań według grupy. Typ projektu określa, które z następujących grup się pojawiają:

- Zestawy z podgrupami Framework i Rozszerzenia.

- Rozwiązanie z podgrupą Projekty.

- Okna z podgrupami Podstawowe i Rozszerzenia. Odwołania do zestawów SDK Windows SDK lub rozszerzeń można eksplorować przy użyciu **Przeglądarka obiektów**.

- Przeglądaj z podgrupą Ostatnie.

## <a name="assemblies-tab"></a>Karta Zestawy
 Na karcie **zestawy** są wyświetlane wszystkie zestawy .NET Framework, które są dostępne do odwołania. Karta **zestawy** nie wyświetla żadnych zestawów z globalnej pamięci podręcznej zestawów (GAC), ponieważ zestawy w pamięci GAC są częścią środowiska wykonawczego. W przypadku wdrażania lub kopiowania aplikacji zawierającej odwołanie do zestawu, który jest zarejestrowany w GAC, zestaw nie zostanie wdrożony ani skopiowany z aplikacją, bez względu na wartość ustawienia Kopiuj lokalnie. Aby uzyskać więcej informacji, zobacz [odwołania do projektu](https://msdn.microsoft.com/library/ez524kew.aspx).

 Podczas ręcznego dodawania odwołania do dowolnych przestrzeni nazw EnvDTE (EnvDTE, EnvDTE80, EnvDTE90, EnvDTE90a lub EnvDTE100), ustaw właściwość Osadź typy współdziałania na wartość False w oknie dialogowym Właściwości. Ustawienie tej właściwości na True może spowodować problemy z kompilacją ze względu na pewne właściwości EnvDTE, które nie mogą być osadzone.

 Wszystkie projekty pulpitu zawierają niejawne odwołanie do mscorlib. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] projekty zawierają niejawne odwołanie do elementu Microsoft. VisualBasic. W programie [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] wszystkie projekty zawierają niejawne odwołanie do System. Core, nawet jeśli zostanie usunięte z listy odwołań.

 Jeśli typ projektu nie obsługuje zestawów, karta nie pojawi się w oknie dialogowym **Menadżer odwołań** .

 Karta Zestawy zawiera dwie karty podrzędne:

1. Framework zawiera listę wszystkich zestawów, które stanowią docelową platformę Framework.

   - Zestawy anonsowane znajdują się liście Pełna platforma Framework i są wyliczone na liście Framework, gdy projekt jest ukierunkowany na Profil docelowej platformy Framework. Zestawy anonsowane są szare, aby odróżnić je od zestawów, które istnieją w profilu docelowej platformy Framework projektu. Na przykład, jeśli projekt jest ukierunkowany na klienta .NET Framework 4, lista zawiera zestawy anonsowane z .NET Framework 4. Gdy użytkownik dodaje anonsowany zestaw, użytkownik zostanie powiadomiony, że po zamknięciu okna dialogowego **Menedżera odwołań** projekt zostanie przekierowani do .NET Framework 4 i zostanie dodany ogłoszony zestaw.

   - Projekty dla [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] aplikacji zawierają odwołania do wszystkich zestawów, które są domyślnie przeznaczone do [!INCLUDE[net_win8_profile](../includes/net-win8-profile-md.md)] tworzenia projektu. W projektach zarządzanych, węzeł tylko do odczytu w folderze References w **Eksplorator rozwiązań** wskazuje odwołanie do całej struktury. W związku z tym na karcie Framework nie będzie wyliczony żaden zestaw z Framework. Zamiast tego wyświetli się następujący komunikat: „Do wszystkich zestawów Framework istnieją już odwołania. Użyj Przeglądarka obiektów, aby poznać odwołania w strukturze ". W przypadku projektów klasycznych na karcie struktura są wyliczane zestawy z platformy dostosowanej, a użytkownik musi dodać odwołania wymagane przez aplikację.

2. Rozszerzenia wyświetla listę wszystkich zestawów, które opracowali zewnętrzni dostawcy składników i formantów, aby rozszerzyć docelową platformę Framework. W zależności od celu aplikacji użytkownika, może być konieczne użycie tych zestawów.

   - Rozszerzenia jest wypełniane przez wyliczanie zestawów, które są zarejestrowane w następujących lokalizacjach:

       ```
       32-bit machine:
       HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]
       HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]
       64-bit machine:
       HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]
       HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]
       And older versions of the [Target Framework Identifier]
       ```

        Na przykład, jeśli projekt jest przeznaczony dla .NET Framework 4 na komputerze 32-bitowym, rozszerzenia będą wyliczać zestawy, które są zarejestrowane w witrynie \Microsoft \\ . NETFramework\v4.0\AssemblyFoldersEx \\ , \Microsoft \\ . NETFramework\v3.5\AssemblyFoldersEx \\ , \Microsoft \\ . NETFramework\v3.0\AssemblyFoldersEx \\ i \Microsoft \\ . NETFramework\v2.0\AssemblyFoldersEx \\ .

   Niektóre składniki na liście mogą nie być wyświetlane, w zależności od [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] wersji projektu. Może się to zdarzyć w następujących warunkach:

- Składnik, który używa najnowszej wersji .NET Framework jest niezgodny z projektem, który jest przeznaczony dla starszej wersji .NET Framework.

     Aby uzyskać informacje na temat sposobu zmiany docelowej wersji .NET Framework dla projektu, zobacz [How to: Target a Version of the .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

- Składnik, który używa [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] jest niezgodny z projektem, który jest przeznaczony dla [!INCLUDE[net_v45](../includes/net-v45-md.md)] .

     Podczas tworzenia nowej aplikacji niektóre projekty są [!INCLUDE[net_v45](../includes/net-v45-md.md)] Domyślnie docelowe. Aby uzyskać więcej informacji, zobacz [.NET Framework profilu klienta](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1).

- Należy unikać dodawania odwołań do plików do danych wyjściowych innego projektu w tym samym rozwiązaniu, ponieważ może to spowodować błędy kompilacji. Zamiast tego należy użyć karty **projekty** okna dialogowego **Dodaj odwołanie** , aby utworzyć odwołania między projektami. Ułatwia to programowanie zespołowe dzięki umożliwieniu lepszego zarządzania bibliotekami klas tworzonymi w projektach. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z uszkodzonymi odwołaniami](../ide/troubleshooting-broken-references.md).

- > [!NOTE]
    > W programie Visual Studio 2015 odwołanie do pliku zamiast odwołania projektu jest tworzone, jeśli docelowa wersja .NET Framework jednego projektu jest w wersji 4,5, a docelowa wersja innego projektu to wersja 2, 3, 3,5 lub 4,0.

#### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Aby wyświetlić zestaw w oknie dialogowym Dodaj odwołanie

- Przenieś lub Skopiuj zestaw do jednej z następujących lokalizacji:

  - Bieżący katalog projektu. (Zestawy te można znaleźć za pomocą karty **Przeglądaj** ).

  - Inne katalogi projektu w tym samym rozwiązaniu. (Zestawy te można znaleźć za pomocą karty **projekty** ).

    \- oraz

- Ustaw klucz rejestru określający lokalizację zestawów do wyświetlenia:

   W przypadku 32-bitowego systemu operacyjnego należy dodać jeden z następujących kluczy rejestru.

  - [HKEY_CURRENT_USER \SOFTWARE\Microsoft \\ . NETFramework \\ *VersionMinimum*\AssemblyFoldersEx\MyAssemblies] @ = "*AssemblyLocation*"

  - [HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft \\ . NETFramework \\ *VersionMinimum*\AssemblyFoldersEx\MyAssemblies] @ = "*AssemblyLocation*"

    W przypadku 64-bitowego systemu operacyjnego należy dodać jeden z następujących kluczy rejestru w gałęzi rejestru 32-bitowego.

  - [HKEY_CURRENT_USER \SOFTWARE\Wow6432Node\Microsoft \\ . NETFramework \\ *VersionMinimum*\AssemblyFoldersEx\MyAssemblies] @ = "*AssemblyLocation*"

  - [HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft \\ . NETFramework \\ *VersionMinimum*\AssemblyFoldersEx\MyAssemblies] @ = "*AssemblyLocation*"

    *VersionMinimum* to najniższa wersja .NET Framework, która ma zastosowanie. Jeśli *VersionMinimum* to v 3.0, foldery określone w AssemblyFoldersEx mają zastosowanie do projektów, które są przeznaczone dla .NET Framework 3,0 i nowszych.

    *AssemblyLocation* jest katalogiem zestawów, które mają być wyświetlane w oknie dialogowym **Dodaj odwołanie** , na przykład C:\MyAssemblies \\ .

    Utworzenie klucza rejestru w węźle HKEY_LOCAL_MACHINE umożliwia wszystkim użytkownikom wyświetlanie zestawów w określonej lokalizacji w oknie dialogowym **Dodawanie odwołania** . Tworzenie klucza rejestru w węźle HKEY_CURRENT_USER ma wpływ tylko na ustawienie bieżącego użytkownika.

    Otwórz ponownie okno dialogowe **Dodawanie odwołania** . Zestawy powinny znajdować się na karcie **.NET** . Jeśli tak nie jest, upewnij się, że zestawy znajdują się w określonym katalogu *AssemblyLocation* , uruchom ponownie program Visual Studio i spróbuj ponownie.

## <a name="com-tab"></a>Karta COM
 Na karcie COM znajduje się lista wszystkich składników COM, które są dostępne dla odwołań. Jeśli chcesz dodać odwołanie do zarejestrowanej DLL modelu COM, zawierającej manifest wewnętrzny, najpierw wyrejestruj bibliotekę DLL. W przeciwnym razie Visual Studio dodaje odwołanie do zestawu jako formant ActiveX, a nie jako natywną DLL.

 Jeśli typ projektu nie obsługuje modelu COM, karta nie pojawi się w oknie dialogowym **Menadżer odwołań** .

## <a name="solution-tab"></a>Karta Rozwiązanie
 Na karcie Rozwiązanie znajduje się lista wszystkich zgodnych projektów w obrębie bieżącego rozwiązania, na karcie podrzędnej Projekty.

 Projekt może się odwoływać do innego projektu, który jest przeznaczony dla innej wersji platformy .NET Framework. Na przykład można utworzyć projekt, który jest przeznaczony dla elementu, który [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] odwołuje się do zestawu, który został skompilowany dla .NET Framework 2. Jednak projekt .NET Framework 2 nie może odwoływać się do [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] projektu. Aby uzyskać więcej informacji, zobacz [Określanie konkretnej wersji .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).

 Projekt, który jest przeznaczony dla elementu [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] jest niezgodny z projektem, który odwołuje się do [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)] .

 W programie [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] odwołanie do pliku zamiast odwołania projektu jest tworzone, jeśli jeden projekt jest przeznaczony dla .NET Framework 4 i inny projekt jest przeznaczony dla starszej wersji.

 Projekt, do którego odwołuje się [!INCLUDE[net_win8_profile](../includes/net-win8-profile-md.md)] nie można dodać odwołania projektu do projektu, który jest przeznaczony dla .NET Framework i na odwrót.

## <a name="windows-tab"></a>Karta Windows
 Na karcie Windows są wymienione wszystkie zestawy SDK specyficzne dla platform, na których jest uruchamiany system operacyjny Windows.

 Można wygenerować plik WinMD w Visual Studio na dwa sposoby:

- ** [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] projekty zarządzane przez aplikacje**: [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] projekty aplikacji mogą wyprowadzać dane binarne winmd przez ustawienie właściwości projektu &#124; typ danych wyjściowych = plik WinMD. Nazwa pliku WinMD musi być nadzbiorem przestrzeni nazw wszystkich przestrzeni nazw, które w nim istnieją. Na przykład, jeżeli projekt składa się z przestrzeni nazw A.B i A.B.C, możliwe nazwy dla wygenerowanego WinMD to A.winmd i A.B.winmd. Jeśli użytkownik wprowadzi właściwości projektu &#124; nazwę zestawu lub właściwości projektu &#124; wartość przestrzeni nazw, która jest rozłączna z zestawu przestrzeni nazw w projekcie lub nie ma obszaru nazw nadzbiórka w projekcie, zostanie wygenerowane ostrzeżenie kompilacji: "A. winmd" nie jest prawidłową nazwą pliku winmd dla tego zestawu. Wszystkie typy w pliku metadanych systemu Windows musi istnieć w podrzędnej przestrzeni nazw nazwy pliku. Typy, które nie istnieją w podrzędnej przestrzeni nazw nazwy pliku, nie mogą być zlokalizowane w czasie wykonywania. W tym zestawie najmniejszą wspólną przestrzenią nazw jest „CSWSClassLibrary1”. Projekt programu Desktop Visual Basic lub Visual C# może zużywać tylko WinMD, które są generowane przy użyciu [!INCLUDE[win8](../includes/win8-md.md)] zestawów SDK, które są znane jako WinMD w pierwszej kolejności, i nie mogą generować metadanych WinMD.

- ** [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] natywne projekty aplikacji**: natywny plik WinMD składa się tylko z metadanych. Jego realizacja istnieje w oddzielnym pliku DLL. Jeden może generować natywne dane binarne przez wybranie szablonu projektu składnika środowisko wykonawcze systemu Windows w oknie dialogowym **Nowy projekt** lub przez rozpoczęcie od pustego projektu i zmodyfikowanie właściwości projektu w celu wygenerowania pliku winmd. Jeżeli projekt zawiera rozłączne przestrzenie nazw, błąd kompilacji poinformuje użytkownika, że należy połączyć ich przestrzenie nazw lub uruchomić narzędzie MSMerge.

  Karta Windows składa się z dwóch podgrup.

### <a name="core-subgroup"></a>Podgrupa podstawowa (Core)
 Podgrupa podstawowa zawiera listę wszystkich WinMD (dla elementów wykonawczych Windows) w zestawie SDK dla docelowej wersji systemu Windows.

 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] projekty aplikacji zawierają domyślnie odwołania do wszystkich WinMD w [!INCLUDE[win8](../includes/win8-md.md)] zestawie SDK podczas tworzenia projektu. W projektach zarządzanych, węzeł tylko do odczytu w folderze References w **Eksplorator rozwiązań** wskazuje odwołanie do całego [!INCLUDE[win8](../includes/win8-md.md)] zestawu SDK. W związku z tym podgrupa podstawowa w Menedżerze odwołań nie będzie wyliczać żadnych zestawów z [!INCLUDE[win8](../includes/win8-md.md)] zestawu SDK, a zamiast tego zostanie wyświetlony komunikat: "Windows SDK istnieje już odwołanie. Użyj przeglądarki obiektów do zbadania odwołań w zestawie SDK systemu Windows”.

 W projektach pulpitu. podgrupa Podstawowa nie jest wyświetlana domyślnie. Możesz dodać środowisko wykonawcze systemu Windows, otwierając menu skrótów dla węzła projektu, wybierając polecenie **Zwolnij projekt**, dodając następujący fragment kodu i ponownie otwierając projekt (w węźle projektu wybierz polecenie **Załaduj ponownie projekt**). Po wywołaniu okna dialogowego **Menedżer odwołań** zostanie wyświetlona podgrupa podstawowa.

```
<PropertyGroup>
  <TargetPlatformVersion>8.0</TargetPlatformVersion>
</PropertyGroup>
```

 Upewnij się, że pole wyboru **systemu Windows** jest zaznaczone w tej podgrupie. Wówczas można używać elementów środowiska wykonawczego Windows. Jednak warto również dodać System.Runtime, w którym środowisko wykonawcze Windows definiuje kilka standardowych klas i interfejsów, takich jak IEnumerable, które są używane we wszystkich bibliotekach uruchomieniowych Windows. Aby uzyskać informacje na temat dodawania elementu System. Runtime, zobacz [zarządzane aplikacje klasyczne i środowisko wykonawcze systemu Windows](https://msdn.microsoft.com/library/windows/apps/jj856306.aspx#consuming_standard_windows_runtime_types).

### <a name="extensions-subgroup"></a>Podgrupa Rozszerzenia
 Rozszerzenia wyświetla pakiety SDK użytkownika, które rozszerzają docelową platformę Windows. Ta karta jest wyświetlana [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] tylko w przypadku projektów aplikacji. Projekty pulpitu nie będzie wyświetlały tej karty, ponieważ mogą one wykorzystywać tylko pliki .winmd pierwszego producenta.

 Zestaw SDK jest zbiorem plików, który program Visual Studio traktuje jako samodzielny składnik. Na karcie rozszerzenia zestawy SDK, które są stosowane do projektu, z którego zostało wywołane okno dialogowe **Menedżer odwołań** , są wyświetlane jako pojedyncze wpisy. Po dodaniu do projektu, cała zawartość zestawu SDK jest wykorzystywana przez program Visual Studio, aby użytkownik nie musiał podejmować dalszych działań, aby wykorzystać zawartość zestawu SDK w technologii IntelliSense, przyborniku, projektantach, przeglądarce obiektów, kompilacji, wdrażaniu, debugowaniu i pakowaniu. Informacje o sposobie wyświetlania zestawu SDK na karcie rozszerzenia można znaleźć w temacie [Creating a Software Development Kit](../extensibility/creating-a-software-development-kit.md).

> [!NOTE]
> Jeśli projekt odwołuje się do zestawu SDK, który zależy od innego zestawu SDK, Visual Studio nie wykorzystuje drugiego zestawu SDK, chyba że użytkownik ręcznie doda odwołanie do drugiego zestawu SDK. Gdy użytkownik wybierze zestaw SDK na karcie **rozszerzenia** , okno dialogowe **Menedżer odwołań** pomaga użytkownikowi identyfikować zależności zestawu SDK, wyświetlając nie tylko nazwę i wersję zestawu SDK, ale również nazwę wszystkich zależności zestawu SDK w okienku szczegółów. Jeśli użytkownik nie zauważy zależności i doda tylko zestaw SDK, program MSBuild będzie monitował użytkownika, aby dodać zależności.

 Jeśli typ projektu nie obsługuje **rozszerzeń**, karta nie jest wyświetlana w oknie dialogowym **Menadżer odwołań** .

## <a name="browse-button"></a>Przycisk Przeglądaj
 Możesz użyć przycisku **Przeglądaj** , aby wyszukać składnik w systemie plików.

 Projekt może się odwoływać do składnika, który jest przeznaczony dla innej wersji platformy .NET Framework. Na przykład, można utworzyć aplikację, która jest przeznaczona dla .NET Framework 4 Client Profile, który odwołuje się do składnika przeznaczonego dla .NET Framework 2. Aby uzyskać więcej informacji, zobacz [Określanie konkretnej wersji .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).

 Nie należy dodawać odwołań do pliku do danych wyjściowych innego projektu w tym samym rozwiązaniu, ponieważ takie rozwiązanie może spowodować błędy kompilacji. Zamiast tego należy użyć karty **rozwiązanie** okna dialogowego **Menedżer odwołań** , aby utworzyć odwołania między projektami. Takie podejście ułatwia projektowanie zespołowe poprzez umożliwienie lepszego zarządzania bibliotekami klas utworzonymi w projektach. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z uszkodzonymi odwołaniami](../ide/troubleshooting-broken-references.md).

 Nie można przejść do zestawu SDK i dodać go do projektu. Można przeglądać tylko w poszukiwaniu pliku (na przykład zestawu lub .winmd) i dodać go do projektu.

 Podczas wykonywania odwołania do pliku WinMD, oczekiwany układ polega na tym, że pliki *filename*. winmd, *filename*. dll i *filename*. pri są umieszczone obok siebie. Jeśli odwołujesz się do WinMD w następujących scenariuszach, niepełny zestaw plików zostanie skopiowany do katalogu wyjściowego projektu i, w związku z tym, wystąpią błędy kompilacji i czasu wykonywania.

- **Składnik macierzysty**: projekt natywny utworzy jeden winmd dla każdego rozłączonego zestawu nazw i jedną bibliotekę DLL, która składa się z implementacji. Pliki WinMD będą miały odmienne nazwy. Przy odwoływaniu się do tego pliku składnika macierzystego, MSBuild nie rozpozna, że pliki WinMD o różnych nazwach stanowią jeden składnik. W związku z tym zostaną skopiowane tylko identyczne nazwy *filename*. dll i *filename*. winmd, a błędy środowiska uruchomieniowego zostaną wykonane. Aby obejść ten problem, należy utworzyć SDK rozszerzenia. Aby uzyskać więcej informacji, zobacz [Tworzenie zestawu Software Development Kit](../extensibility/creating-a-software-development-kit.md).

- **Używanie formantów**: co najmniej kontrolka XAML składa się z *pliku filename*. winmd, *filename*. dll, *filename*. pri, *XamlName*. XAML i *ImageName*. jpg. Po skompilowaniu projektu pliki zasobów, które są skojarzone z odwołaniem do pliku, nie zostaną skopiowane do katalogu wyjściowego projektu i zostanie skopiowane tylko *Nazwa pliku*. winmd, *filename*. dll i *filename*. pri. Błąd kompilacji jest rejestrowany w celu powiadomienia użytkownika o braku zasobów *XamlName*. XAML i *ImageName*. jpg. Aby kompilacja się powiodła, trzeba ręcznie skopiować te pliki zasobów do katalogu wyjściowego projektu dla kompilacji i debugowania/czasu wykonywania. Aby obejść ten problem, Utwórz zestaw SDK rozszerzeń, wykonując kroki opisane w temacie [Tworzenie zestawu Software Development Kit](../extensibility/creating-a-software-development-kit.md) lub edytuj plik projektu, aby dodać następującą właściwość:

    ```
    <PropertyGroup>
    <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > Jeśli dodasz właściwość, kompilacja może być wolniejsza.

## <a name="recent"></a>Ostatnie
 Każda z kart Zestawy, COM, Windows i Przeglądaj obsługuje kartę Najnowsze, która wylicza listę składników ostatnio dodanych do projektów.

## <a name="search"></a>Wyszukiwanie
 Pasek wyszukiwania w oknie dialogowym **Menedżer odwołań** działa nad kartą, na której się skupia. Na przykład, jeśli użytkownik wpisze na pasku wyszukiwania przycisk "system", podczas gdy karta **rozwiązanie** jest fokusem, wyszukiwanie nie zwróci żadnych wyników, chyba że rozwiązanie składa się z nazwy projektu zawierającej "system".

## <a name="see-also"></a>Zobacz też
 [NIB: Dodawanie lub usuwanie odwołań za pomocą okna dialogowego Dodawanie odwołania](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)
