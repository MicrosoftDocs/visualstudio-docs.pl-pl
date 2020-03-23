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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595313"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Jak: Dodawanie lub usuwanie odwołań za pomocą Menedżera odwołań

Za pomocą okna dialogowego Menedżer odwołań można dodawać odwołania do składników opracowanych przez użytkownika, firmę Microsoft lub inną firmę oraz zarządzać nimi. Jeśli tworzysz uniwersalną aplikację systemu Windows, projekt automatycznie odwołuje się do wszystkich prawidłowych bibliotek DLL SDK systemu Windows. W przypadku tworzenia aplikacji .NET projekt automatycznie odwołuje się do *pliku mscorlib.dll*. Niektóre interfejsy API platformy .NET są widoczne w składnikach, które należy dodać ręcznie. Odwołania do składników COM lub komponentów niestandardowych należy dodać ręcznie.

## <a name="reference-manager-dialog-box"></a>Okno dialogowe Menedżer odwołań

Okno dialogowe Menedżer odwołań zawiera różne kategorie po lewej stronie, w zależności od typu projektu:

- **Zestawy**, z **podgrupami Framework** i **Extensions**

- **COM** wyświetla listę wszystkich składników COM, które są dostępne do odwoływania się

- **Projekty**

- **Projekty współdzielone**

- **Windows**, z podgrupami **Core** i **Extensions.** Odwołania w sdk windows SDK lub rozszerzenia SDK można eksplorować za pomocą **przeglądarki obiektów**.

- **Przeglądaj**, z **podgrupą Ostatnie**

## <a name="add-a-reference"></a>Dodawanie odwołania

1. W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł **Odwołania** lub **zależności** i wybierz polecenie **Dodaj odwołanie**. Można również kliknąć prawym przyciskiem myszy węzeł projektu i wybrać pozycję **Dodaj** > **odwołanie**.

   **Menedżer odwołań** otwiera i wyświetla dostępne odwołania według grupy.

2. Określ odwołania do dodania, a następnie wybierz **przycisk OK**.

## <a name="assemblies-tab"></a>Karta Zestawy

Karta **Zestawy** zawiera listę wszystkich zestawów .NET, które są dostępne do odwoływania się. Na karcie **Zestawy** nie ma listy żadnych zestawów z globalnej pamięci podręcznej zestawów (GAC), ponieważ zestawy w pamięci podręcznej GAC są częścią środowiska wykonywania. Jeśli wdrożysz lub skopiujesz aplikację, która zawiera odwołanie do zestawu, który jest zarejestrowany w pliku GAC, zestaw nie zostanie wdrożony ani skopiowany z aplikacją, niezależnie od ustawienia **Kopiuj lokalnie.** Aby uzyskać więcej informacji, zobacz [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md).

Podczas ręcznego dodawania odwołania do dowolnego obszaru nazw<xref:EnvDTE>EnvDTE <xref:EnvDTE80>( , , <xref:EnvDTE90>, <xref:EnvDTE90a>, , lub <xref:EnvDTE100>), ustaw właściwość **Osadzanie typów międzyop** odwołania do **false** w oknie **Właściwości.** Ustawienie tej właściwości na **True** może spowodować problemy z kompilacją z powodu niektórych właściwości EnvDTE, których nie można osadzać.

Wszystkie projekty pulpitu zawierają niejawne odwołanie do **mscorlib**. Projekty języka Visual Basic <xref:Microsoft.VisualBasic>zawierają niejawne odwołanie do . Wszystkie projekty zawierają niejawne odwołanie do **System.Core,** nawet jeśli jest on usunięty z listy odwołań.

Jeśli typ projektu nie obsługuje zestawów, karta nie pojawi się w oknie dialogowym Menedżer odwołań.

Karta **Zestawy** składa się z dwóch podmaszcz:

1. **Framework** zawiera listę wszystkich zestawów, które stanowią docelową strukturę.

   W przypadku projektów, które nie są przeznaczone dla platformy .NET Core lub platformy systemu Windows uniwersalnej, karta **Framework** wylicza zestawy z docelowej struktury. Użytkownik musi dodać wszelkie odwołania, które wymaga aplikacji.

   Uniwersalne projekty systemu Windows zawierają odwołania do wszystkich zestawów w ramach docelowej domyślnie. W projektach zarządzanych węzeł tylko do odczytu w folderze **Odwołania** w **Eksploratorze rozwiązań** wskazuje odwołanie do całej struktury. W związku z tym **framework** kartę nie wylicza żadnych zestawów z platformy i zamiast tego wyświetla następujący komunikat: "Wszystkie zestawy Framework są już odwołuje. Użyj przeglądarki obiektów, aby eksplorować odwołania w ramach".

2. **Rozszerzenia** zawiera listę wszystkich zestawów, które zewnętrzni dostawcy składników i formantów opracowali w celu rozszerzenia struktury docelowej. W zależności od celu aplikacji użytkownika, może być konieczne użycie tych zestawów.

   Rozszerzenia są wypełniane przez **wyliczenie** zestawów, które są zarejestrowane w następujących lokalizacjach:

   Maszyna 32-bitowa:
   - `HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   64-bitowa maszyna:
   - `HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   I starsze wersje [Identyfikatora docelowej struktury]

   Na przykład, jeśli projekt jest przeznaczony dla platformy .NET Framework 4 na komputerze 32-bitowym, **rozszerzenia wyliczają** zestawy zarejestrowane w obszarze *\Microsoft\.NETFramework\v4.0\AssemblyFoldersEx*, *\Microsoft\.NETFramework\v3.5\AssemblyFoldersEx*, *\Microsoft\.NETFramework\v3.0\AssemblyFoldersEx*, i *\Microsoft\.NETFramework\v2.0\AssemblyFoldersEx*.

Niektóre składniki na liście mogą nie być wyświetlane, w zależności od wersji struktury projektu. Może to nastąpić w następujących warunkach:

- Składnik, który używa najnowszej wersji framework jest niezgodny z projektem, który jest przeznaczony dla wcześniejszej wersji.

   Aby uzyskać informacje dotyczące zmieniania docelowej wersji struktury dla projektu, zobacz [omówienie kierowania na platformę.](visual-studio-multi-targeting-overview.md)

- Składnik, który używa programu .NET Framework 4 jest niezgodny z projektem przeznaczonym dla programu .NET Framework 4.5.

Należy unikać dodawania odwołań do plików do danych wyjściowych innego projektu w tym samym rozwiązaniu, ponieważ w ten sposób może to spowodować błędy kompilacji. Zamiast tego użyj karty **Projekty** w oknie dialogowym **Dodawanie odwołania** do tworzenia odwołań do projektu. Ułatwia to tworzenie zespołu, umożliwiając lepsze zarządzanie bibliotekami klas utworzonymi w projektach. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z uszkodzonymi odwołaniami](../ide/troubleshooting-broken-references.md).

> [!NOTE]
> W programie Visual Studio 2015 lub nowszym odwołanie do pliku zamiast odwołania do projektu jest tworzone, jeśli docelową wersją struktury jednego projektu jest .NET Framework 4.5 lub nowsza, a docelową wersją innego projektu jest .NET Framework 2, 3, 3.5 lub 4.0.

### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Aby wyświetlić złożenie w oknie dialogowym Dodawanie odwołania

- Przenieś lub skopiuj zespół do jednej z następujących lokalizacji:

  - Bieżący katalog projektów. (Te zestawy można znaleźć za pomocą karty **Przeglądaj).**

  - Inne katalogi projektów w tym samym rozwiązaniu. (Te zestawy można znaleźć za pomocą karty **Projekty).**

  \-lub -

- Ustaw klucz rejestru określający lokalizację zestawów do wyświetlenia:

  W przypadku 32-bitowego systemu operacyjnego dodaj jeden z następujących kluczy rejestru.

  - `[HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  W przypadku 64-bitowego systemu operacyjnego dodaj jeden z następujących kluczy rejestru w gałęzi rejestru 32-bitowego.

  - `[HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  *VersionMinimum\> jest najniższą wersją framework, która ma zastosowanie. \<* Jeśli * \<VersionMinimum\> * jest w wersji 3.0, foldery określone w *AssemblyFoldersEx* stosuje się do projektów, które są przeznaczone dla platformy .NET Framework 3.0 i nowsze.

  *AssemblyLocation\> jest katalogiem zestawów, które mają być wyświetlane w oknie dialogowym Dodawanie odwołania, na przykład C:\MyAssemblies . \<* **Add Reference** *C:\MyAssemblies*

  Utworzenie klucza rejestru `HKEY_LOCAL_MACHINE` w węźle umożliwia wszystkim użytkownikom wyświetlanie zestawów w określonej lokalizacji w oknie dialogowym **Dodawanie odwołania.** Utworzenie klucza rejestru `HKEY_CURRENT_USER` w węźle ma wpływ tylko na ustawienie dla bieżącego użytkownika.

  Ponownie otwórz okno dialogowe **Dodawanie odwołania.** Zestawy powinny pojawić się na karcie **.NET.** Jeśli tak nie jest, upewnij się, że zestawy znajdują się w określonym katalogu *AssemblyLocation,* uruchom ponownie program Visual Studio i spróbuj ponownie.

## <a name="projects-tab"></a>Karta Projekty

Karta **Projekty** zawiera listę wszystkich zgodnych projektów w ramach bieżącego rozwiązania na podkobacie **Rozwiązanie.**

Projekt może odwoływać się do innego projektu, który jest przeznaczony dla innej wersji framework. Na przykład można utworzyć projekt, który jest przeznaczony dla programu .NET Framework 4, ale odwołuje się do zestawu, który został zbudowany dla programu .NET Framework 2. Jednak projekt .NET Framework 2 nie może odwoływać się do projektu .NET Framework 4. Aby uzyskać więcej informacji, zobacz [omówienie kierowania na ramy](../ide/visual-studio-multi-targeting-overview.md).

> [!NOTE]
> Projekt przeznaczony dla programu .NET Framework 4 jest niezgodny z projektem przeznaczonym dla profilu klienta programu .NET Framework 4.

## <a name="shared-projects-tab"></a>Karta Projekty udostępnione

Dodaj odwołanie do udostępnionego projektu na karcie **Projekty udostępnione** w oknie dialogowym Menedżer odwołań. [Udostępnione projekty](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) umożliwiają pisanie wspólnego kodu, do którego odwołuje się wiele różnych projektów aplikacji.

## <a name="universal-windows-tab"></a>Karta Uniwersalny system Windows

Karta **Uniwersalny system Windows** zawiera listę wszystkich zestawów SDK specyficznych dla platform, na których działają systemy operacyjne Windows.
Ta karta ma dwie podgrupy: **Core** i **Extensions**.

### <a name="core-subgroup"></a>Podgrupa podstawowa

Uniwersalne projekty aplikacji systemu Windows mają domyślnie odwołanie do uniwersalnego zestawu SDK systemu Windows. W związku z tym **Core** podgrupy w **Menedżerze odwołań** nie wylicza żadnego z zestawów z uniwersalnego zestawu SDK systemu Windows.

### <a name="extensions-subgroup"></a>Podgrupa rozszerzeń

**Rozszerzenia** zawierają listę sdk użytkowników, które rozszerzają docelową platformę systemu Windows.

Zestaw SDK jest zbiorem plików, który program Visual Studio traktuje jako samodzielny składnik. Na karcie **Rozszerzenia** skuszone skuszki SDK, które mają zastosowanie do projektu, z którego wywoływano okno dialogowe Menedżer odwołań, są wyświetlane jako pojedyncze wpisy. Po dodaniu do projektu cała zawartość zestawu SDK jest zużywana przez program Visual Studio w taki sposób, że użytkownik nie musi podejmować żadnych dalszych działań w celu wykorzystania zawartości zestawu SDK w programie IntelliSense, przyborniku, projektanci, przeglądarka obiektów, kompilacja, wdrożenie, debugowanie i pakowanie.

Aby uzyskać informacje dotyczące wyświetlania zestawu SDK na karcie **Rozszerzenia,** zobacz [Tworzenie zestawu programistycznego](../extensibility/creating-a-software-development-kit.md).

> [!NOTE]
> Jeśli projekt odwołuje się do SDK, który zależy od innego SDK, Visual Studio nie będzie używać drugiego SDK, chyba że ręcznie dodać odwołanie do drugiego SDK. Gdy użytkownik wybierze pakiet SDK na karcie Rozszerzenia, okno dialogowe Menedżer **odwołań** ułatwia identyfikowanie zależności SDK przez wyświetlenie wszystkich zależności w okienku szczegółów.

Jeśli typ projektu nie obsługuje rozszerzeń, ta karta nie jest wyświetlana w oknie dialogowym Menedżer odwołań.

## <a name="com-tab"></a>Karta COM

Karta **COM** zawiera listę wszystkich składników COM, które są dostępne do odwoływania się. Jeśli chcesz dodać odwołanie do zarejestrowanej DLL modelu COM, zawierającej manifest wewnętrzny, najpierw wyrejestruj bibliotekę DLL. W przeciwnym razie visual studio dodaje odwołanie do zestawu jako formant ActiveX, a nie jako natywnej biblioteki DLL.

Jeśli typ projektu nie obsługuje usługi COM, karta nie jest wyświetlana w oknie dialogowym Menedżer odwołań.

## <a name="browse"></a>Browse

Za pomocą przycisku **Przeglądaj** można wyszukać składnik w systemie plików.

Projekt może odwoływać się do składnika, który jest przeznaczony dla innej wersji framework. Na przykład można utworzyć aplikację, która jest przeznaczona dla platformy .NET Framework 4.7, ale odwołuje się do składnika przeznaczonego dla platformy .NET Framework 4. Aby uzyskać więcej informacji, zobacz [omówienie kierowania na ramy](../ide/visual-studio-multi-targeting-overview.md).

Należy unikać dodawania odwołań do plików do danych wyjściowych innego projektu w tym samym rozwiązaniu, ponieważ ta taktyka może powodować błędy kompilacji. Zamiast tego użyj karty **Rozwiązanie** w oknie dialogowym Menedżer odwołań do tworzenia odwołań do projektu. Ułatwia to tworzenie zespołu, umożliwiając lepsze zarządzanie bibliotekami klas, które można utworzyć w projektach. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z uszkodzonymi odwołaniami](../ide/troubleshooting-broken-references.md).

Nie można przejść do sdk i dodać go do projektu. Można tylko przejść do pliku (na przykład zestawu lub *.winmd*) i dodać go do projektu.

Podczas wykonywania odwołania do pliku WinMD, oczekiwany układ jest to, że * \<FileName>.winmd*, * \<FileName>.dll*i * \<FileName>.pri* pliki są umieszczone obok siebie. Jeśli odwołujesz się do WinMD w następujących scenariuszach, niepełny zestaw plików zostanie skopiowany do katalogu wyjściowego projektu i, w związku z tym, wystąpią błędy kompilacji i czasu wykonywania.

- **Składnik macierzysty:** projekt macierzysty utworzy jeden WinMD dla każdego rozłącznego zestawu obszarów nazw i jedną bibliotekę DLL, która składa się z implementacji. Pliki WinMD będą miały odmienne nazwy. Podczas odwoływania się do tego macierzystego pliku składnika, MSBuild nie rozpoznaje, że niepodobne nazwy WinMDs zrobić jeden składnik. W związku z tym tylko o identycznej nazwie * \<FileName>.dll* i * \<FileName>.winmd* zostaną skopiowane i wystąpią błędy środowiska uruchomieniowego. Aby obejść ten problem, należy utworzyć sdk rozszerzenia. Aby uzyskać więcej informacji, zobacz [Tworzenie zestawu programistycznego](../extensibility/creating-a-software-development-kit.md).

- **Korzystanie z formantów:** co najmniej, formant XAML składa się z * \<>.winmd FileName*, * \<FileName>.dll*, * \<FileName>.pri*, * \<XamlName>.xaml*i * \<ImageName>.jpg*. Po zbudowaniu projektu pliki zasobów skojarzone z odwołaniem do pliku nie zostaną skopiowane do katalogu wyjściowego projektu i zostaną skopiowane tylko * \<filename>.winmd*, * \<FileName>.dll* i * \<FileName>.pri.* Rejestrowany jest błąd kompilacji informujący użytkownika, że brakuje zasobów * \<XamlName>.xaml* i * \<ImageName>.jpg.* Aby kompilacja się powiodła, trzeba ręcznie skopiować te pliki zasobów do katalogu wyjściowego projektu dla kompilacji i debugowania/czasu wykonywania. Aby obejść ten problem, należy utworzyć zestaw SDK rozszerzenia, wykonując kroki opisane w [programie Tworzenie zestawu programistycznego oprogramowania](../extensibility/creating-a-software-development-kit.md) lub edytować plik projektu, aby dodać następującą właściwość:

    ```xml
    <PropertyGroup>
       <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > Jeśli dodasz właściwość, kompilacja może być wolniejsza.

## <a name="recent"></a>Ostatnie

**Zestawy**, **COM**, **Windows**i **Przeglądaj** każdy obsługuje **Ostatnie** karty, która wylicza listę składników, które zostały niedawno dodane do projektów.

## <a name="search"></a>Wyszukiwanie

Pasek wyszukiwania w oknie dialogowym Menedżer odwołań działa na karcie, która jest w centrum uwagi. Na przykład jeśli użytkownik wpisuje "System" na pasku wyszukiwania, gdy karta **Rozwiązanie** jest w centrum uwagi, wyszukiwanie nie zwróci żadnych wyników, chyba że rozwiązanie składa się z nazwy projektu, która zawiera "System".

## <a name="see-also"></a>Zobacz też

- [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)
