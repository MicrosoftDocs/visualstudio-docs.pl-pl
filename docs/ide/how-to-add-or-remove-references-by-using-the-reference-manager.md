---
title: Dodawanie odwołań w Menedżerze odwołań
ms.date: 08/02/2019
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dfad622a7587246836161cd79bb5b759151df1ef
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595313"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Instrukcje: Dodawanie lub usuwanie odwołań za pomocą Menedżera odwołań

Za pomocą okna dialogowego Menedżer odwołań można dodawać odwołania do składników, które zostały opracowane przez firmę Microsoft lub inną firmę, oraz zarządzać nimi. Jeśli tworzysz aplikację uniwersalną systemu Windows, projekt automatycznie odwołuje się do wszystkich poprawnych Windows SDK bibliotek DLL. Jeśli tworzysz aplikację platformy .NET, projekt automatycznie odwołuje się do *biblioteki mscorlib. dll*. Niektóre interfejsy API platformy .NET są udostępniane w składnikach, które trzeba dodać ręcznie. Odwołania do składników COM lub składników niestandardowych należy dodać ręcznie.

## <a name="reference-manager-dialog-box"></a>Menedżer odwołań — okno dialogowe

W oknie dialogowym Menedżer odwołań są wyświetlane różne kategorie po lewej stronie, w zależności od typu projektu:

- **Zestawy**z podgrupami **platformy** i **rozszerzeń**

- **Com** wyświetla listę wszystkich składników com dostępnych do odwołania

- **Projekty**

- **Projekty udostępnione**

- **System Windows**z podgrupami **Core** i **Extensions** . Odwołania do zestawów SDK Windows SDK lub rozszerzeń można eksplorować przy użyciu **Przeglądarka obiektów**.

- **Przeglądaj**z **ostatnią** podgrupą

## <a name="add-a-reference"></a>Dodaj odwołanie

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **odwołania** lub **zależności** i wybierz polecenie **Dodaj odwołanie**. Możesz również kliknąć prawym przyciskiem myszy węzeł projektu i wybrać polecenie **dodaj** > **odwołanie**.

   Zostanie otwarty **Menedżer odwołań** i zostanie wyświetlona lista dostępnych odwołań według grupy.

2. Określ odwołania do dodania, a następnie wybierz przycisk **OK**.

## <a name="assemblies-tab"></a>Karta Zestawy

Na karcie **zestawy** są wyświetlane wszystkie zestawy .NET, które są dostępne do odwołania. Karta **zestawy** nie wyświetla żadnych zestawów z globalnej pamięci podręcznej zestawów (GAC), ponieważ zestawy w pamięci GAC są częścią środowiska wykonawczego. W przypadku wdrażania lub kopiowania aplikacji zawierającej odwołanie do zestawu, który jest zarejestrowany w pamięci podręcznej GAC, zestaw nie zostanie wdrożony ani skopiowany z aplikacją, niezależnie od ustawienia **kopiowania lokalnego** . Aby uzyskać więcej informacji, zobacz [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md).

Po ręcznym dodaniu odwołania do dowolnych przestrzeni nazw EnvDTE (<xref:EnvDTE>, <xref:EnvDTE80>, <xref:EnvDTE90>, <xref:EnvDTE90a>lub <xref:EnvDTE100>) ustaw właściwość **Osadź typy** współdziałania z odwołaniem na **wartość false** w oknie **Właściwości** . Ustawienie tej właściwości na **wartość true** może spowodować problemy z kompilacją ze względu na pewne właściwości EnvDTE, które nie mogą być osadzone.

Wszystkie projekty pulpitu zawierają niejawne odwołanie do **biblioteki mscorlib**. Projekty Visual Basic zawierają niejawne odwołanie do <xref:Microsoft.VisualBasic>. Wszystkie projekty zawierają niejawne odwołanie do **System. Core**, nawet jeśli zostanie usunięte z listy odwołań.

Jeśli typ projektu nie obsługuje zestawów, karta nie pojawi się w oknie dialogowym Menadżer odwołań.

Karta **zestawy** składa się z dwóch podkart:

1. **Struktura** zawiera listę wszystkich zestawów, które stanowią platformę dodaną.

   W przypadku projektów, które nie są ukierunkowane na platformę .NET Core lub platforma uniwersalna systemu Windows, na karcie **Framework** są wyliczane zestawy z platformy docelowej. Użytkownik musi dodać wszystkie odwołania wymagane przez aplikację.

   Projekty uniwersalne systemu Windows domyślnie zawierają odwołania do wszystkich zestawów w środowisku strategicznym. W projektach zarządzanych, węzeł tylko do odczytu w folderze **References** w **Eksplorator rozwiązań** wskazuje odwołanie do całej struktury. W związku z tym na karcie **Struktura** nie są wyliczane żadne zestawy z struktury i zamiast tego jest wyświetlany następujący komunikat: "wszystkie zestawy Framework są już przywoływane. Użyj Przeglądarka obiektów, aby poznać odwołania w strukturze ".

2. **Rozszerzenia** wyświetla listę wszystkich zestawów, które zostały opracowane przez zewnętrznych dostawców składników i formantów w celu rozszerzenia platformy dostosowanej. W zależności od celu aplikacji użytkownika, może być konieczne użycie tych zestawów.

   **Rozszerzenia** są wypełniane przez Wyliczenie zestawów, które są zarejestrowane w następujących lokalizacjach:

   32-bitowa maszyna:
   - `HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   64-bitowa maszyna:
   - `HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   I starsze wersje [docelowego identyfikatora platformy]

   Na przykład jeśli projekt jest ukierunkowany na .NET Framework 4 na komputerze 32-bitowym, **rozszerzenia** wyliczają zestawy, które są zarejestrowane w obszarze *\Microsoft\.NETFramework\v4.0\AssemblyFoldersEx*, *\microsoft\.NETFramework\v3.5\AssemblyFoldersEx*, *\Microsoft\.NETFramework\v3.0\AssemblyFoldersEx*i *\Microsoft\.NETFramework\v2.0\AssemblyFoldersEx*.

Niektóre składniki na liście mogą nie być wyświetlane, w zależności od wersji platformy projektu. Może się to zdarzyć w następujących warunkach:

- Składnik, który używa najnowszej wersji struktury, jest niezgodny z projektem, który jest przeznaczony dla starszej wersji.

   Aby uzyskać informacje o sposobie zmiany wersji platformy docelowej dla projektu, zobacz temat [Omówienie określania](visual-studio-multi-targeting-overview.md)celu.

- Składnik używający .NET Framework 4 jest niezgodny z projektem, który jest przeznaczony dla .NET Framework 4,5.

Należy unikać dodawania odwołań do plików do danych wyjściowych innego projektu w tym samym rozwiązaniu, ponieważ może to spowodować błędy kompilacji. Zamiast tego należy użyć karty **projekty** okna dialogowego **Dodaj odwołanie** , aby utworzyć odwołania między projektami. Ułatwia to programowanie zespołowe dzięki umożliwieniu lepszego zarządzania bibliotekami klas tworzonymi w projektach. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z uszkodzonymi odwołaniami](../ide/troubleshooting-broken-references.md).

> [!NOTE]
> W programie Visual Studio 2015 lub nowszym, odwołanie do pliku zamiast odwołania projektu jest tworzone, jeśli docelowa wersja struktury jednego projektu to .NET Framework 4,5 lub nowsza, a docelowa wersja innego projektu to .NET Framework 2, 3, 3,5 lub 4,0.

### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Aby wyświetlić zestaw w oknie dialogowym Dodaj odwołanie

- Przenieś lub Skopiuj zestaw do jednej z następujących lokalizacji:

  - Bieżący katalog projektu. (Zestawy te można znaleźć za pomocą karty **Przeglądaj** ).

  - Inne katalogi projektu w tym samym rozwiązaniu. (Zestawy te można znaleźć za pomocą karty **projekty** ).

  \- lub —

- Ustaw klucz rejestru określający lokalizację zestawów do wyświetlenia:

  W przypadku 32-bitowego systemu operacyjnego należy dodać jeden z następujących kluczy rejestru.

  - `[HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  W przypadku 64-bitowego systemu operacyjnego należy dodać jeden z następujących kluczy rejestru w gałęzi rejestru 32-bitowego.

  - `[HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  *\<VersionMinimum\>* to najniższa wersja platformy, która ma zastosowanie. Jeśli *\<VersionMinimum\>* to v 3.0, foldery określone w *AssemblyFoldersEx* mają zastosowanie do projektów przeznaczonych dla .NET Framework 3,0 i nowszych.

  *\<AssemblyLocation\>* jest katalogiem zestawów, które mają być wyświetlane w oknie dialogowym **Dodaj odwołanie** , na przykład *C:\MyAssemblies*.

  Utworzenie klucza rejestru w węźle `HKEY_LOCAL_MACHINE` umożliwia wszystkim użytkownikom wyświetlanie zestawów w określonej lokalizacji w oknie dialogowym **Dodawanie odwołania** . Tworzenie klucza rejestru w węźle `HKEY_CURRENT_USER` ma wpływ tylko na ustawienie bieżącego użytkownika.

  Otwórz ponownie okno dialogowe **Dodawanie odwołania** . Zestawy powinny znajdować się na karcie **.NET** . Jeśli tak nie jest, upewnij się, że zestawy znajdują się w określonym katalogu *AssemblyLocation* , uruchom ponownie program Visual Studio i spróbuj ponownie.

## <a name="projects-tab"></a>Karta projekty

Na karcie **projekty** znajduje się lista wszystkich zgodnych projektów w ramach bieżącego rozwiązania, na karcie podkartę **rozwiązania** .

Projekt może odwoływać się do innego projektu, który jest przeznaczony dla innej wersji platformy. Na przykład można utworzyć projekt, który jest przeznaczony dla .NET Framework 4, ale odwołuje się do zestawu, który został skompilowany dla .NET Framework 2. Jednak projekt .NET Framework 2 nie może odwoływać się do projektu .NET Framework 4. Aby uzyskać więcej informacji, zobacz temat [Omówienie funkcji określania wartości docelowej](../ide/visual-studio-multi-targeting-overview.md).

> [!NOTE]
> Projekt, który jest przeznaczony dla .NET Framework 4 jest niezgodny z projektem, który jest przeznaczony dla profilu klienta .NET Framework 4.

## <a name="shared-projects-tab"></a>Karta projekty udostępnione

Dodaj odwołanie do projektu udostępnionego na karcie **projekty udostępnione** okna dialogowego Menedżer odwołań. [Projekty udostępnione](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) umożliwiają pisanie wspólnych kodów, do których odwołują się różne projekty aplikacji.

## <a name="universal-windows-tab"></a>Karta uniwersalna systemu Windows

Karta **uniwersalna systemu Windows** zawiera listę zestawów SDK, które są specyficzne dla platform, na których działają systemy operacyjne Windows.
Ta karta ma dwie podgrupy: **rdzeń** i **rozszerzenia**.

### <a name="core-subgroup"></a>Podgrupa podstawowa

Projekty uniwersalnej aplikacji systemu Windows mają domyślnie przywoływane Windows SDK uniwersalne. W związku z tym podgrupa **podstawowa** w **Menedżerze odwołań** nie wylicza żadnych zestawów z uniwersalnej Windows SDK.

### <a name="extensions-subgroup"></a>Podgrupa rozszerzeń

**Rozszerzenia** wymienia zestawy SDK użytkowników, które rozszerzają dodaną platformę systemu Windows.

Zestaw SDK jest zbiorem plików, który program Visual Studio traktuje jako samodzielny składnik. Na karcie **rozszerzenia** zestawy SDK, które są stosowane do projektu, z którego zostało wywołane okno dialogowe Menedżer odwołań, są wyświetlane jako pojedyncze wpisy. Po dodaniu do projektu cała zawartość zestawu SDK jest używana przez program Visual Studio w taki sposób, że użytkownik nie musi podejmować dalszych działań w celu użycia zawartości zestawu SDK w IntelliSense, przyborniku, projektantach, Przeglądarka obiektów, kompilacji, wdrożeniu, debugowaniu i pakowaniu.

Informacje o sposobie wyświetlania zestawu SDK na karcie **rozszerzenia** można znaleźć w temacie [Creating a Software Development Kit](../extensibility/creating-a-software-development-kit.md).

> [!NOTE]
> Jeśli projekt odwołuje się do zestawu SDK, który zależy od innego zestawu SDK, program Visual Studio nie będzie korzystał z drugiego zestawu SDK, chyba że ręcznie dodasz odwołanie do drugiego zestawu SDK. Gdy użytkownik wybierze zestaw SDK na karcie **rozszerzenia** , okno dialogowe Menedżer odwołań pomaga identyfikować zależności zestawu SDK przez wystawienie wszelkich zależności w okienku szczegółów.

Jeśli typ projektu nie obsługuje rozszerzeń, ta karta nie jest wyświetlana w oknie dialogowym Menadżer odwołań.

## <a name="com-tab"></a>Karta COM

Na karcie **com** znajduje się lista wszystkich składników com, które są dostępne do odwołania. Jeśli chcesz dodać odwołanie do zarejestrowanej DLL modelu COM, zawierającej manifest wewnętrzny, najpierw wyrejestruj bibliotekę DLL. W przeciwnym razie program Visual Studio dodaje odwołanie do zestawu jako kontrolkę ActiveX, a nie jako natywną bibliotekę DLL.

Jeśli typ projektu nie obsługuje modelu COM, karta nie jest wyświetlana w oknie dialogowym Menadżer odwołań.

## <a name="browse"></a>Przeglądaj

Możesz użyć przycisku **Przeglądaj** , aby wyszukać składnik w systemie plików.

Projekt może odwoływać się do składnika, który jest przeznaczony dla innej wersji platformy. Na przykład można utworzyć aplikację, która jest przeznaczona dla .NET Framework 4,7, ale odwołuje się do składnika, który jest przeznaczony dla .NET Framework 4. Aby uzyskać więcej informacji, zobacz temat [Omówienie funkcji określania wartości docelowej](../ide/visual-studio-multi-targeting-overview.md).

Należy unikać dodawania odwołań do plików do danych wyjściowych innego projektu w tym samym rozwiązaniu, ponieważ ten taktyką może spowodować błędy kompilacji. Zamiast tego należy użyć karty **rozwiązanie** okna dialogowego Menedżer odwołań, aby utworzyć odwołania między projektami. Ułatwia to programowanie zespołowe dzięki umożliwieniu lepszego zarządzania bibliotekami klas tworzonych w projektach. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z uszkodzonymi odwołaniami](../ide/troubleshooting-broken-references.md).

Nie można przejść do zestawu SDK i dodać go do projektu. Możesz tylko przeglądać do pliku (na przykład zestawu lub *winmd*) i dodać go do projektu.

W przypadku odwoływania się do pliku WinMD, oczekiwany układ polega na tym, że *\<filename >. winmd*, *\<filename >. dll*i *\<filename >. pliki PRI* są umieszczone obok siebie. Jeśli odwołujesz się do WinMD w następujących scenariuszach, niepełny zestaw plików zostanie skopiowany do katalogu wyjściowego projektu i, w związku z tym, wystąpią błędy kompilacji i czasu wykonywania.

- **Składnik macierzysty**: projekt natywny utworzy jeden winmd dla każdego rozłączonego zestawu nazw i jedną bibliotekę DLL, która składa się z implementacji. Pliki WinMD będą miały odmienne nazwy. W przypadku odwoływania się do tego pliku składnika macierzystego MSBuild nie rozpoznaje, że niepodobne nazwy WinMD tworzą jeden składnik. W związku z tym tylko nazwy *\<filename >. dll* i *\<filename >. winmd* zostaną skopiowane, a błędy środowiska uruchomieniowego zostaną wykonane. Aby obejść ten problem, Utwórz zestaw SDK rozszerzenia. Aby uzyskać więcej informacji, zobacz [Tworzenie zestawu Software Development Kit](../extensibility/creating-a-software-development-kit.md).

- Korzystanie z **formantów**: co najmniej kontrolka XAML składa się z *\<pliku >. winmd*, *\<filename >. dll*, *\<filename >. pri*, *\<xamlname >. XAML*i *\<ImageName >. jpg*. Po skompilowaniu projektu pliki zasobów, które są skojarzone z odwołaniem do pliku, nie zostaną skopiowane do katalogu wyjściowego projektu i tylko *\<filename >. winmd*, *\<filename >. dll* i *\<filename >. pri* zostaną skopiowane. Zarejestrowano błąd kompilacji, aby poinformować użytkownika, że brakuje zasobów *\<xamlname >. XAML* i *\<ImageName >. jpg* . Aby kompilacja się powiodła, trzeba ręcznie skopiować te pliki zasobów do katalogu wyjściowego projektu dla kompilacji i debugowania/czasu wykonywania. Aby obejść ten problem, Utwórz zestaw SDK rozszerzeń, wykonując kroki opisane w temacie [Tworzenie zestawu SDK oprogramowania](../extensibility/creating-a-software-development-kit.md) lub edytuj plik projektu, aby dodać następującą właściwość:

    ```xml
    <PropertyGroup>
       <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > Jeśli dodasz właściwość, kompilacja może być wolniejsza.

## <a name="recent"></a>Ostatnie

**Zespoły**, **com**, **Windows**i **Przeglądaj** każdy obsługują **ostatnią** kartę, która wylicza listę składników, które zostały ostatnio dodane do projektów.

## <a name="search"></a>Wyszukaj

Pasek wyszukiwania w oknie dialogowym Menedżer odwołań działa nad kartą, na której się skupia. Na przykład, jeśli użytkownik wpisze na pasku wyszukiwania przycisk "system", podczas gdy karta **rozwiązanie** jest fokusem, wyszukiwanie nie zwróci żadnych wyników, chyba że rozwiązanie składa się z nazwy projektu zawierającej "system".

## <a name="see-also"></a>Zobacz także

- [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)
