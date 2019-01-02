---
title: Dodaj odwołania w Menedżerze odwołań
ms.date: 04/11/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- VS.ReferenceManager
helpviewer_keywords:
- C# projects, references
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
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4e3e21f38f8b4f60678aa4bb767368393c666cab
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53856283"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Instrukcje: Dodawanie lub usuwanie odwołań za pomocą Menedżera odwołań

Możesz użyć **Menadżer odwołań** okno dialogowe, aby dodać i zarządzać odwołaniami do składników przez użytkownika, Microsoft, lub dostosowywania innej firmy. Jeśli tworzysz aplikację Windows Universal projekt automatycznie odwołuje się do wszystkich poprawne dll Windows SDK. Jeśli tworzysz aplikację .NET, projekt automatycznie odwołuje się do *mscorlib.dll*. Niektóre interfejsy API platformy .NET są widoczne w składnikach, które trzeba dodać ręcznie. Odwołania do składników modelu COM lub niestandardowe składniki trzeba dodać ręcznie.

## <a name="reference-manager-dialog-box"></a>Okno dialogowe menedżera odwołań

**Menadżer odwołań** wyświetlane okno dialogowe różnych kategorii po lewej stronie, w zależności od typu projektu:

- **Zestawy**, za pomocą **Framework** i **rozszerzenia** podgrupy.

- **COM**, wyświetla listę wszystkich składników COM, które są dostępne dla odwołań.

- **Rozwiązanie**, za pomocą **projektów** podgrupy.

- **Windows**, za pomocą **Core** i **rozszerzenia** podgrupy. Odwołania w Windows SDK lub SDK rozszerzeń można eksplorować przy użyciu **przeglądarki obiektów**.

- **Przeglądaj**, za pomocą **ostatnie** podgrupy.

## <a name="add-and-remove-a-reference"></a>Dodawanie i usuwanie odwołań

### <a name="to-add-a-reference"></a>Aby dodać odwołanie

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** lub **zależności** węzeł i wybierz polecenie **Dodaj odwołanie**. Możesz również kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Dodaj** > **odwołania**.

   **Menadżer odwołań** otwiera się i wyświetla dostępne odwołania wg grupy.

2. Określ odwołania, aby dodać, a następnie wybierz pozycję **OK**.

## <a name="assemblies-tab"></a>Karta Zestawy

**Zestawy** karta zawiera listę wszystkich zestawów .NET Framework, które są dostępne dla odwołań. **Zestawy** karty nie ma żadnych zestawów z globalnej pamięci podręcznej zestawów (GAC), ponieważ zestawy w pamięci podręcznej GAC są częścią środowiska czasu wykonywania. Wdrażania lub kopiowania aplikacji zawierającej odwołanie do zestawu, który jest zarejestrowany w GAC, zestaw nie będzie można wdrażać i skopiowany z aplikacją, bez względu na to **Kopiuj lokalnie** ustawienie. Aby uzyskać więcej informacji, zobacz [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md).

Podczas ręcznego dodawania odniesienia do dowolnych przestrzeni nazw EnvDTE (<xref:EnvDTE>, <xref:EnvDTE80>, <xref:EnvDTE90>, <xref:EnvDTE90a>, lub <xref:EnvDTE100>) ustaw **Osadź typy współdziałania** właściwości odwołania do **False** w **właściwości** okna. Ustawienie tej właściwości na **True** Przyczyna tworzyć problemy ze względu na pewne właściwości EnvDTE, które nie mogą być osadzone.

Wszystkie projekty pulpitu zawierają niejawne odwołanie do **mscorlib**. [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] projekty zawierają niejawne odwołanie do <xref:Microsoft.VisualBasic>. Wszystkie projekty zawierają niejawne odwołanie do **System.Core**nawet wtedy, gdy zostanie ono usunięte z listy odwołań.

Jeśli typ projektu nie obsługuje zestawów, karta nie pojawi się w **Menadżer odwołań** okno dialogowe.

**Zestawy** karty składają się dwie karty podrzędne:

1. **Framework** Wyświetla listę wszystkich zestawów, które stanowią docelową platformę framework.

    Projekty dla systemu Windows 8.x Store aplikacji zawierają odwołania do wszystkich zestawów w docelowym [!INCLUDE[net_win8_profile](../ide/includes/net_win8_profile_md.md)] domyślnie przy tworzeniu projektu. W projektach zarządzanych, węzeł tylko do odczytu w ramach **odwołania** folderu w **Eksploratora rozwiązań** wskazuje odwołanie do całej struktury framework. W związku z tym **Framework** karta nie będzie wyliczony żaden zestaw z framework i zamiast tego wyświetli się następujący komunikat: "Wszystkich zestawów Framework istnieją już odwołania. Użyj przeglądarki obiektów do zbadania odwołań w ramach." Dla projektów pulpitu **Framework** kartę wylicza zestawy z docelowej platformy framework i użytkownik musi dodać odwołania wymagane przez tę aplikację.

2. **Rozszerzenia** Wyświetla listę wszystkich zestawów, które opracowali zewnętrzni dostawcy składników i formantów rozszerzyć docelową platformę framework. W zależności od celu aplikacji użytkownika, może być konieczne użycie tych zestawów.

   **Rozszerzenia** jest wypełniane przez wyliczanie zestawów, które są zarejestrowane w następujących lokalizacjach:

   komputer 32-bitowe:
   - `HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   komputer 64-bitowych:
   - `HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   I starsze wersje [identyfikatora struktury docelowej]

   Na przykład, jeśli projekt jest przeznaczony dla .NET Framework 4 na komputerze 32-bitowym **rozszerzenia** wyliczą zestawy, które są zarejestrowane w ramach *\Microsoft\.NETFramework\v4.0\AssemblyFoldersEx*, *\Microsoft\.NETFramework\v3.5\AssemblyFoldersEx*, *\Microsoft\.NETFramework\v3.0\AssemblyFoldersEx*, i  *\Microsoft\.NETFramework\v2.0\AssemblyFoldersEx*.

Niektóre składniki na liście mogą nie być wyświetlane, w zależności od wersji .NET Framework projektu. Taka sytuacja może wystąpić w następujących warunkach:

- Składnik, który korzysta z najnowszej wersji programu .NET Framework jest niezgodny z projektem, który jest przeznaczony dla starszej wersji programu .NET Framework.

    Aby uzyskać informacje o zmienianiu docelowej wersji .NET Framework dla projektu, zobacz [jak: Docelowa wersja systemu .NET Framework](../ide/how-to-target-a-version-of-the-dotnet-framework.md).

- Składnik, który używa [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] jest niezgodny z projektem, który jest przeznaczony dla [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)].

    Podczas tworzenia nowej aplikacji docelowej niektóre projekty kierują [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] domyślnie.

Dodawanie odwołań do pliku do danych wyjściowych innego projektu w tym samym rozwiązaniu, należy unikać, ponieważ w ten sposób może spowodować błędy kompilacji. Zamiast tego należy użyć **projektów** karcie **Dodaj odwołanie** okno dialogowe, aby utworzyć odwołania projekt projekt. Ułatwia to Projektowanie zespołowe poprzez umożliwienie lepszego zarządzania bibliotekami klas, utworzone w projekcie. Aby uzyskać więcej informacji, zobacz [rozwiązywanie uszkodzenie odwołań](../ide/troubleshooting-broken-references.md).

> [!NOTE]
> W programie Visual Studio 2015 lub nowszym odwołanie pliku zamiast odwołania projektu jest tworzony, jeśli wersji docelowej programu .NET Framework jednego projektu jest w wersji 4.5 lub nowszej, a wersję docelową innego projektu jest w wersji 2, 3, 3.5 lub 4.0.

### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Aby wyświetlić zestaw w oknie dialogowym Dodawanie odwołania

- Przenoszenie lub kopiowanie zestawu do jednej z następujących lokalizacji:

   - Katalog aktualnego projektu. (Zestawy te można znaleźć przy użyciu **Przeglądaj** karty.)

   - Inne katalogi projektu w tym samym rozwiązaniu. (Zestawy te można znaleźć przy użyciu **projektów** karty.)

    \- lub —

- Ustaw klucz rejestru, który określa lokalizację zestawów do wyświetlenia:

   W przypadku 32-bitowym systemie operacyjnym należy dodać jeden z następujących kluczy rejestru.

   - `[HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

   - `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

   Dla 64-bitowym systemie operacyjnym należy dodać jeden z następujących kluczy rejestru w gałęzi rejestru 32-bitowych.

   - `[HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

   - `[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

   *\<VersionMinimum\>*  jest najniższą wersją .NET Framework, która ma zastosowanie. Jeśli *\<VersionMinimum\>* jest w wersji 3.0, foldery określone w *AssemblyFoldersEx* zastosowanie do projektów przeznaczonych dla platformy .NET Framework 3.0 lub nowszej.

   *\<AssemblyLocation\>*  to katalog zestawów, które mają być wyświetlane w **Dodaj odwołanie** okno dialogowe, na przykład *C:\MyAssemblies*.

   Tworzenie klucza rejestru w `HKEY_LOCAL_MACHINE` węzła umożliwia wszystkim użytkownikom przeglądanie zestawów w określonej lokalizacji w **Dodaj odwołanie** okno dialogowe. Tworzenie klucza rejestru w `HKEY_CURRENT_USER` węzeł ma wpływ tylko ustawienia dla bieżącego użytkownika.

   Otwórz **Dodaj odwołanie** ponownie okno dialogowe. Zestawy powinny pojawić się na **.NET** kartę. Jeśli nie, upewnij się, że zestawy znajdują się w określonym *AssemblyLocation* katalogu, uruchom ponownie program Visual Studio i spróbuj ponownie.

## <a name="projects-tab"></a>Karta projekty

**Projektów** karcie znajduje się lista wszystkich zgodnych projektów w obrębie bieżącego rozwiązania, w **rozwiązania** karcie podrzędnej.

Projekt może się odwoływać do innego projektu, który jest przeznaczony dla innej wersji platformy .NET Framework. Na przykład, można utworzyć projektu przeznaczonego [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] , ale która odwołuje się zestaw stworzonemu dla platformy .NET Framework 2. Jednak projekt .NET Framework 2 nie może odwoływać się [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] projektu. Aby uzyskać więcej informacji, zobacz [wielowersyjnością kodu – Przegląd](../ide/visual-studio-multi-targeting-overview.md).

Projekt, który jest przeznaczony dla [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] jest niezgodny z projektem, który jest przeznaczony dla [!INCLUDE[net_client_v40_long](../deployment/includes/net_client_v40_long_md.md)].

Odwołanie do pliku jest tworzony zamiast odwołania projektu, jeśli jeden projekt obiektów docelowych programu .NET Framework 4 i inny projekt jest przeznaczony dla starszej wersji.

Projekt, który jest przeznaczony dla [!INCLUDE[net_win8_profile](../ide/includes/net_win8_profile_md.md)] nie można dodać odwołania projektu do projektu, który jest przeznaczony dla programu .NET Framework i na odwrót.

## <a name="windows-tab"></a>Karta Windows

**Windows** karta zawiera listę wszystkich zestawów SDK, które są specyficzne dla platform, na które systemy operacyjne Windows, uruchom.

Można wygenerować plik WinMD w Visual Studio na dwa sposoby:

- **Projekty zarządzane Windows 8.x Store aplikacji**: Projekty aplikacji systemu Windows 8.x Store może zapewniać dane wyjściowe pliki binarne WinMD przez ustawienie **właściwości projektu** > **typ danych wyjściowych = plik WinMD**. Nazwa pliku WinMD musi być nadzbiorem przestrzeni nazw wszystkich przestrzeni nazw, które w nim istnieją. Na przykład, jeśli projekt składa się z przestrzeni nazw `A.B` i `A.B.C`, możliwe nazwy dla wygenerowanego WinMD to *A.winmd* i *A.B.winmd*. Jeśli użytkownik wprowadzi **właściwości projektu** > **nazwy zestawu** lub **właściwości projektu** > **Namespace**wartość, która jest odłączona od zestawu przestrzeni nazw w projekcie lub jest nadzbiorem przestrzeni nazw w ramach projektu, jest generowane ostrzeżenie kompilacji: "'A.winmd' nie jest prawidłową nazwą pliku .winmd dla tego zestawu." Wszystkie typy w pliku metadanych systemu Windows musi istnieć w podrzędnej przestrzeni nazw nazwy pliku. Typy, które nie istnieją w podrzędnej przestrzeni nazw nazwy pliku nie będzie mógł być zlokalizowane w czasie wykonywania. W tym zestawie najmniejszą wspólną przestrzenią nazw jest `CSWSClassLibrary1`. Pulpitu języka Visual Basic lub C# projekt może używać tylko plików Winmd, które są generowane przy użyciu Windows 8 SDK, znanych jako Winmd firmy Microsoft i nie można wygenerować plików Winmd.

- **Windows 8.x Store macierzyste projekty aplikacji**: Macierzysty plik WinMD składa się z tylko metadanych. Jego realizacja istnieje w oddzielnym pliku DLL. Można produkować, aby przez wybranie szablonu projektu składnika wykonawczego Windows w natywnych plików binarnych **nowy projekt** okno dialogowe lub zaczynając od pustego projektu i modyfikując właściwości projektu, aby wygenerować plik WinMD. Jeżeli projekt zawiera rozłączne przestrzenie nazw, błąd kompilacji poinformuje użytkownika, że należy połączyć ich przestrzenie nazw lub uruchomić narzędzie MSMerge.

**Windows** kartę składa się z dwóch podgrup.

### <a name="core-subgroup"></a>Podgrupa podstawowa

**Core** podgrupa zawiera listę wszystkich Winmd (dla elementów wykonawczych Windows) w zestawie SDK dla wersji docelowej systemu Windows.

Projekty aplikacji systemu Windows 8.x Store zawierają odwołania do wszystkich Winmd w systemie Windows 8 SDK, domyślnie przy tworzeniu projektu. W projektach zarządzanych, węzeł tylko do odczytu w ramach **odwołania** folderu w **Eksploratora rozwiązań** wskazuje odwołanie do całego systemu Windows 8 SDK. W związku z tym **Core** podgrupy w **Menadżer odwołań** nie będzie wyliczała żadnych zestawów z systemu Windows 8 SDK i zamiast tego zostanie wyświetlony komunikat: "Z zestawu Windows SDK jest już przywoływany. Użyj przeglądarki obiektów do zbadania odwołań w zestawie Windows SDK."

W projektach pulpitu **Core** podgrupy nie jest wyświetlana domyślnie. Można dodać środowisko wykonawcze Windows, otwierając menu skrótów dla węzła projektu, wybierając **Zwolnij projekt**, dodając poniższy fragment kodu i ponownie otwierając projekt (w węźle projektu wybierz **Załaduj ponownie projekt**). Gdy wywołujesz **Menadżer odwołań** okno dialogowe **Core** pojawia się podgrupa.

```xml
<PropertyGroup>
  <TargetPlatformVersion>8.0</TargetPlatformVersion>
</PropertyGroup>
```

Upewnij się, że wybrano **Windows** pole wyboru w tej podgrupie. Wówczas można używać elementów środowiska wykonawczego Windows. Jednakże, również należy dodać <xref:System.Runtime>, w której środowisko wykonawcze Windows definiuje kilka standardowych klas i interfejsów, takich jak <xref:System.Collections.IEnumerable>, które są używane w całej biblioteki środowiska uruchomieniowego Windows. Aby uzyskać informacje dotyczące sposobu dodawania <xref:System.Runtime>, zobacz [zarządzane aplikacje pulpitu i środowisko uruchomieniowe Windows](/previous-versions/windows/apps/jj856306(v=win.10)#consuming-standard-windows-runtime-types).

### <a name="extensions-subgroup"></a>Podgrupa rozszerzenia

**Rozszerzenia** zawiera listę użytkowników zestawów SDK, które rozszerzają docelowej platformy Windows. Ta karta jest wyświetlana, Windows 8.x Store aplikacji tylko dla projektów. Projekty pulpitu nie będzie wyświetlały tej karty, ponieważ mogą one wykorzystywać tylko firmy *winmd* plików.

Zestaw SDK jest zbiorem plików, który program Visual Studio traktuje jako samodzielny składnik. W **rozszerzenia** karcie zestawy SDK, które są stosowane do projektu, z których **Menadżer odwołań** zostało wywołane okno dialogowe są wymienione jako pojedyncze wpisy. Po dodaniu do projektu jest cała zawartość zestawu SDK używane przez program Visual Studio, takie, że użytkownik nie musiał podejmować dalszych działań, aby wykorzystać zawartość zestawu SDK w technologii IntelliSense, przyborniku, projektantach, przeglądarce obiektów, kompilacji, wdrażaniu, debugowaniu i pakowaniu. Aby uzyskać informacje o wyświetlaniu SDK w **rozszerzenia** kartę, zobacz [tworzenia Software Development Kit](../extensibility/creating-a-software-development-kit.md).

> [!NOTE]
> Jeśli projekt odwołuje się zestaw SDK, który jest zależny od innego zestawu SDK, Visual Studio nie wykorzystuje drugiego zestawu SDK, chyba że użytkownik ręcznie doda odwołanie do drugiego zestawu SDK. Gdy użytkownik wybierze SDK na **rozszerzenia** karcie **Menadżer odwołań** okno dialogowe pomaga użytkownikowi określić zależności zestawu SDK przez wymienienie nie tylko nazwę i wersję zestawu SDK, ale także nazwy wszelkich zestawu SDK zależności w okienku szczegółów. Jeśli użytkownik nie zauważy zależności i doda tylko, że zestaw SDK, program MSBuild będzie monitował użytkownika można dodać zależności.

Jeśli typ projektu nie obsługuje rozszerzeń, karta nie pojawi się w **Menadżer odwołań** okno dialogowe.

## <a name="com-tab"></a>Karta COM

**COM** karta zawiera listę wszystkich składników COM, które są dostępne dla odwołań. Jeśli chcesz dodać odwołanie do zarejestrowanej DLL modelu COM, zawierającej manifest wewnętrzny, najpierw wyrejestruj bibliotekę DLL. W przeciwnym razie program Visual Studio dodaje odwołanie do zestawu jako formant ActiveX, a nie jako natywny DLL.

Jeśli typ projektu nie obsługuje COM, karta nie pojawi się w **Menadżer odwołań** okno dialogowe.

## <a name="browse-button"></a>Przycisk Przeglądaj

Możesz użyć **Przeglądaj** przycisk, aby wyszukać składnik w systemie plików.

Projekt może się odwoływać do składnika, który jest przeznaczony dla innej wersji platformy .NET Framework. Na przykład można utworzysz aplikację przeznaczonego .NET Framework 4.7, który odwołuje się do składnika, który jest przeznaczony dla .NET Framework 4. Aby uzyskać więcej informacji, zobacz [wielowersyjnością kodu – Przegląd](../ide/visual-studio-multi-targeting-overview.md).

Nie należy dodawać odwołań do pliku do danych wyjściowych innego projektu w tym samym rozwiązaniu, ponieważ takie rozwiązanie może spowodować błędy kompilacji. Zamiast tego należy użyć **rozwiązania** karcie **Menadżer odwołań** okno dialogowe, aby utworzyć odwołania projekt projekt. Ułatwia to Projektowanie zespołowe poprzez umożliwienie lepszego zarządzania bibliotekami klas utworzonymi w projektach. Aby uzyskać więcej informacji, zobacz [rozwiązywanie uszkodzenie odwołań](../ide/troubleshooting-broken-references.md).

Nie można przejść do zestawu SDK i dodać go do projektu. Można przeglądać tylko w pliku (na przykład zestawu lub *winmd*) i dodaj go do projektu.

Gdy tworzysz odwołanie pliku do WinMD, oczekiwany układ jest  *<FileName>winmd*,  *<FileName>.dll*, i  *<FileName>PRI* plików wszystkie umieszczane obok siebie. Jeśli odwołujesz się do WinMD w następujących scenariuszach, niepełny zestaw plików zostanie skopiowany do katalogu wyjściowego projektu i, w związku z tym, wystąpią błędy kompilacji i czasu wykonywania.

- **Składnik macierzysty**: macierzysty projekt utworzy jeden WinMD dla każdego rozłącznego zestawu przestrzeni nazw i jedną bibliotekę DLL, która składa się z implementacji. Pliki WinMD będą miały odmienne nazwy. Podczas odwoływania się do tego pliku składnika macierzystego, MSBuild nie rozpozna, że pliki Winmd o stanowią jeden składnik. W związku z tym, tylko identycznie nazwane pliki  *<FileName>.dll* i  *<FileName>winmd* zostaną skopiowane, a wystąpią błędy czasu wykonywania. Aby obejść ten problem, Utwórz rozszerzenie SDK. Aby uzyskać więcej informacji, zobacz [Create Software Development Kit](../extensibility/creating-a-software-development-kit.md).

- **Korzystanie z kontrolek**: formant XAML składa się co najmniej z  *<FileName>winmd*,  *<FileName>.dll*,  *<FileName>PRI*,  *<XamlName>.xaml*i  *<ImageName>.jpg*. Gdy projekt jest kompilowany, pliki zasobów, które są skojarzone z odwołaniem do pliku nie będą otrzymywać skopiowany do katalogu wyjściowego projektu, a tylko  *<FileName>winmd*,  *<FileName>.dll*i  *<FileName>PRI* zostaną skopiowane. Błąd kompilacji jest rejestrowany, aby informować użytkownika, zasoby  *<XamlName>.xaml* i  *<ImageName>.jpg* brakuje. Aby kompilacja się powiodła, trzeba ręcznie skopiować te pliki zasobów do katalogu wyjściowego projektu dla kompilacji i debugowania/czasu wykonywania. Aby obejść ten problem, Utwórz rozszerzenie SDK wykonując kroki opisane w [Create Software Development Kit](../extensibility/creating-a-software-development-kit.md) lub edytowania pliku projektu, należy dodać następującą właściwość:

    ```xml
    <PropertyGroup>
       <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > Jeśli dodasz właściwość, kompilacja może być wolniejsza.

## <a name="recent"></a>Ostatnie

**Zestawy**, **COM**, **Windows**, i **Przeglądaj** każdego pomocy technicznej **ostatnie** kartę, która wylicza listę składniki, które zostały ostatnio dodanych do projektów.

## <a name="search"></a>Wyszukaj

Pasek wyszukiwania w **Menadżer odwołań** okno dialogowe działa przez kartę która jest w trybie koncentracji uwagi. Na przykład, jeśli użytkownik wpisze "System" na pasku wyszukiwania, gdy **rozwiązania** karta jest w trybie koncentracji uwagi, wyszukiwanie nie zwraca żadnych wyników, chyba że rozwiązanie składa się z nazwy projektu, który zawiera "System".

## <a name="see-also"></a>Zobacz także

- [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)