---
title: Dodawanie odwołań w Menedżerze odwołań
description: Dowiedz się, jak za pomocą okna dialogowego Menedżer odwołań dodawać odwołania do opracowanych składników i zarządzać nimi.
ms.custom: SEO-VS-2020
ms.date: 08/02/2019
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 552ec8364bb58b72199bacecca99283303eb174c
ms.sourcegitcommit: d3658667e768d7516cbf4461ec47bf24c8fcb7e6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112924919"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>Jak dodać lub usunąć odwołania za pomocą Menedżera odwołań

Okno dialogowe Menedżer odwołań umożliwia dodawanie odwołań do składników opracowanych przez ciebie, firmę Microsoft lub inną firmę oraz zarządzanie nimi. Jeśli tworzysz aplikację uniwersalną systemu Windows, projekt automatycznie odwołuje się do wszystkich poprawnych bibliotek WINDOWS SDK DLL. Jeśli tworzysz aplikację .NET, projekt automatycznie odwołuje się do *mscorlib.dll*. Niektóre interfejsy API .NET są udostępniane w składnikach, które należy dodać ręcznie. Odwołania do składników COM lub składników niestandardowych należy dodać ręcznie.

## <a name="reference-manager-dialog-box"></a>Okno dialogowe Menedżer odwoływać

Okno dialogowe Menedżer odwoływać zawiera różne kategorie po lewej stronie, w zależności od typu projektu:

- **Zestawy** z **podgrupami Framework** **i Extensions**

- **Com** wyświetla listę wszystkich składników COM, które są dostępne do odwoływania się

- **Projekty**

- **Projekty udostępnione**

- **Windows** z **podgrupami Core** **i** Extensions. Odwołania można eksplorować w zestawach SDK Windows SDK rozszerzenia przy użyciu **przeglądarki obiektów**.

- **Przeglądanie** za pomocą **podgrupy** Ostatnie
 
    > [!NOTE]
    > Podczas tworzenia **projektów** w języku C++ w oknie dialogowym Menedżer odwoływać się może nie być widać przycisku Przeglądaj.

## <a name="add-a-reference"></a>Dodawanie odwołania

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł **Odwołania** **lub** zależności i wybierz polecenie **Dodaj odwołanie**. Możesz również kliknąć prawym przyciskiem myszy węzeł projektu i wybrać polecenie **Dodaj**  >  **odwołanie**.

   **Otwiera Menedżera** odwołań i wyświetla listę dostępnych odwołań według grupy.

2. Określ odwołania do dodania, a następnie wybierz przycisk **OK.**

## <a name="assemblies-tab"></a>Karta Zestawy

Karta **Zestawy zawiera** listę wszystkich zestawów .NET, które są dostępne do odwoływania się. Karta **Zestawy** nie zawiera listy zestawów z globalnej pamięci podręcznej zestawów (GAC), ponieważ zestawy w pamięci GAC są częścią środowiska uruchomieniowego. Jeśli wdrożysz lub skopiujesz aplikację zawierającą odwołanie do zestawu zarejestrowanego w gałęce GAC, zestaw nie zostanie wdrożony ani skopiowany razem z aplikacją, niezależnie od ustawienia Kopiuj **lokalnie.** Aby uzyskać więcej informacji, zobacz [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md).

W przypadku ręcznego dodawania odwołania do dowolnej przestrzeni nazw EnvDTE (, , , lub ) ustaw właściwość Embed Interop Types (Osadzanie typów międzyoptykowych) odwołania na wartość False w <xref:EnvDTE> <xref:EnvDTE80> <xref:EnvDTE90> <xref:EnvDTE90a> <xref:EnvDTE100> **oknie Właściwości.**   Ustawienie tej właściwości na **wartość True może** spowodować problemy z kompilacją z powodu niektórych właściwości EnvDTE, których nie można osadzić.

Wszystkie projekty pulpitu zawierają niejawne odwołanie **do mscorlib**. Visual Basic projektów zawierają niejawne odwołanie do <xref:Microsoft.VisualBasic> . Wszystkie projekty zawierają niejawne odwołanie do **system.Core,** nawet jeśli zostanie ono usunięte z listy odwołań.

Jeśli typ projektu nie obsługuje zestawów, karta nie będzie wyświetlana w oknie dialogowym Menedżer odwoływać.

Karta **Zestawy** składa się z dwóch podkart:

1. **Framework** wyświetla listę wszystkich zestawów, które stanowią docelową platformę.

   W przypadku projektów, które nie są kierowane do programu .NET Core ani platforma uniwersalna systemu Windows, karta **Framework** wylicza zestawy z docelowej struktury. Użytkownik musi dodać wszelkie odwołania wymagane przez aplikację.

   Projekty uniwersalne systemu Windows domyślnie zawierają odwołania do wszystkich zestawów w docelowej platformie. W projektach zarządzanych węzeł tylko do odczytu w folderze **Odwołania** Eksplorator rozwiązań **wskazuje** odwołanie do całej struktury. W związku z tym karta **Framework** nie wylicza żadnych zestawów z tej struktury, a zamiast tego wyświetla następujący komunikat: "Wszystkie zestawy framework są już przywołyne. Użyj przeglądarki obiektów, aby eksplorować odwołania na platformie".

2. **Rozszerzenia wyświetla** listę wszystkich zestawów opracowanych przez zewnętrznych dostawców składników i kontrolek w celu rozszerzenia docelowej struktury. W zależności od celu aplikacji użytkownika, może być konieczne użycie tych zestawów.

   **Rozszerzenia są** wypełniane przez wyliczanie zestawów, które są zarejestrowane w następujących lokalizacjach:

   Maszyna 32-bitowa:
   - `HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   Maszyna 64-bitowa:
   - `HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`
   - `HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]`

   I starsze wersje [Identyfikator struktury docelowej]

   Jeśli na przykład projekt jest przeznaczony dla wersji .NET Framework 4  na maszynie 32-bitowej, rozszerzenia wylicza zestawy zarejestrowane w katalogu *\Microsoft \. NETFramework\v4.0\AssemblyFoldersEx*, *\Microsoft \. NETFramework\v3.5\AssemblyFoldersEx*, *\Microsoft \. NETFramework\v3.0\AssemblyFoldersEx* i *\Microsoft \. NETFramework\v2.0\AssemblyFoldersEx*.

Niektóre składniki na liście mogą nie być wyświetlane, w zależności od wersji struktury projektu. Może się to zdarzyć w następujących warunkach:

- Składnik, który używa najnowszej wersji struktury, jest niezgodny z projektem przeznaczonym dla starszej wersji.

   Aby uzyskać informacje o tym, jak zmienić wersję struktury docelowej dla projektu, zobacz [Omówienie określania](visual-studio-multi-targeting-overview.md)wartości docelowej struktury .

- Składnik, który używa .NET Framework 4, jest niezgodny z projektem przeznaczonym dla .NET Framework 4.5.

Należy unikać dodawania odwołań do plików do danych wyjściowych innego projektu w tym samym rozwiązaniu, ponieważ może to spowodować błędy kompilacji. Zamiast tego użyj karty **Projekty** w oknie **dialogowym Dodawanie** odwołania, aby utworzyć odwołania projekt-projekt. Ułatwia to opracowywanie zespołowe przez umożliwienie lepszego zarządzania bibliotekami klas tworzyć w projektach. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z uszkodzonymi odwołaniami](../ide/troubleshooting-broken-references.md).

> [!NOTE]
> W Visual Studio 2015 r. lub nowszym odwołanie do pliku zamiast odwołania do projektu jest tworzone, jeśli docelowa wersja struktury jednego projektu to .NET Framework 4.5 lub nowsza, a docelowa wersja innego projektu to .NET Framework 2, 3, 3.5 lub 4.0.

### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>Aby wyświetlić zestaw w oknie dialogowym Dodawanie odwołania

- Przenieś lub skopiuj zestaw do jednej z następujących lokalizacji:

  - Bieżący katalog projektu. (Te zestawy można znaleźć przy użyciu **karty Przeglądaj).**

  - Inne katalogi projektów w tym samym rozwiązaniu. (Te zestawy można znaleźć przy użyciu karty **Projekty).**

  \- lub —

- Ustaw klucz rejestru określający lokalizację zestawów do wyświetlenia:

  W przypadku 32-bitowego systemu operacyjnego dodaj jeden z następujących kluczy rejestru.

  - `[HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  W przypadku 64-bitowego systemu operacyjnego dodaj jeden z następujących kluczy rejestru w gałęzi rejestru 32-bitowego.

  - `[HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  - `[HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\<VersionMinimum>\AssemblyFoldersEx\MyAssemblies]@="<AssemblyLocation>"`

  *\<VersionMinimum\>* to najniższa wersja struktury, która ma zastosowanie. Jeśli *\<VersionMinimum\>* jest w wersji 3.0, foldery określone w *AssemblyFoldersEx* mają zastosowanie do projektów docelowych .NET Framework 3.0 i nowszych.

  *\<AssemblyLocation\>* to katalog zestawów, które mają być wyświetlane  w oknie dialogowym Dodawanie odwołania, na przykład *C:\MyAssemblies*.

  Utworzenie klucza rejestru w węźle umożliwia wszystkim użytkownikom wyświetlanie zestawów w określonej lokalizacji w `HKEY_LOCAL_MACHINE` **oknie dialogowym Dodawanie** odwołania. Utworzenie klucza rejestru w węźle ma `HKEY_CURRENT_USER` wpływ tylko na ustawienie dla bieżącego użytkownika.

  Otwórz ponownie **okno dialogowe Dodawanie** odwołania. Zestawy powinny zostać wyświetlone na karcie **.NET.** Jeśli tak nie jest, upewnij się, że zestawy znajdują się w określonym katalogu *AssemblyLocation,* uruchom ponownie Visual Studio i spróbuj ponownie.

## <a name="projects-tab"></a>Karta Projekty

Karta **Projekty** zawiera listę wszystkich zgodnych projektów w ramach bieżącego rozwiązania na karcie **podrzędnej** Rozwiązanie.

Projekt może odwoływać się do innego projektu, który jest przeznaczony dla innej wersji struktury. Można na przykład utworzyć projekt przeznaczony dla .NET Framework 4, ale który odwołuje się do zestawu, który został sbudowaną dla .NET Framework 2. Jednak projekt .NET Framework 2 nie może odwoływać się do .NET Framework 4. Aby uzyskać więcej informacji, zobacz [Framework targeting overview (Omówienie określania celu struktury).](../ide/visual-studio-multi-targeting-overview.md)

> [!NOTE]
> Projekt przeznaczony dla .NET Framework 4 jest niezgodny z projektem przeznaczonym dla profilu .NET Framework 4.

## <a name="shared-projects-tab"></a>Karta Projekty udostępnione

Dodaj odwołanie do projektu udostępnionego na karcie **Projekty udostępnione** okna dialogowego Menedżer odwoływać. [Projekty udostępnione](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) umożliwiają pisanie wspólnego kodu, do których odwołuje się wiele różnych projektów aplikacji.

## <a name="universal-windows-tab"></a>Karta uniwersalnego systemu Windows

Karta **Uniwersalny system Windows** zawiera listę wszystkich zestawów SDK specyficznych dla platform, na których działają systemy operacyjne Windows.
Ta karta ma dwie podgrupy: **Core** i **Extensions**.

### <a name="core-subgroup"></a>Podgrupa podstawowa

Projekty aplikacji uniwersalnych systemu Windows mają domyślnie odwołanie do Windows SDK uniwersalnej. W związku z tym podgrupa **Core** w Menedżerze odwoływać się nie wylicza żadnych zestawów z zestawu universal Windows SDK. 

### <a name="extensions-subgroup"></a>Podgrupa rozszerzeń

**Rozszerzenia wyświetla** zestawy SDK użytkownika, które rozszerzają docelową platformę systemu Windows.

Zestaw SDK jest zbiorem plików, który program Visual Studio traktuje jako samodzielny składnik. Na karcie **Rozszerzenia** zestawy SDK, które mają zastosowanie do projektu, z którego zostało wywołane okno dialogowe Menedżer odwoływać się, są wyświetlane jako pojedyncze wpisy. Po dodaniu do projektu cała zawartość zestawu SDK jest zużywana przez usługę Visual Studio w taki sposób, że użytkownik nie musi podjąć żadnych dalszych działań w celu wykorzystania zawartości zestawu SDK w funkcji IntelliSense, przyborniku, projektantach, przeglądarce obiektów, kompilacji, wdrażaniu, debugowaniu i pakowaniu.

Aby uzyskać informacje na temat sposobu wyświetlania zestawu SDK na **karcie Rozszerzenia,** zobacz [Tworzenie zestawu Software Development Kit.](../extensibility/creating-a-software-development-kit.md)

> [!NOTE]
> Jeśli projekt odwołuje się do zestawu SDK, który zależy od innego zestawu SDK, Visual Studio nie będzie korzystać z drugiego zestawu SDK, chyba że ręcznie dodasz odwołanie do drugiego zestawu SDK. Gdy użytkownik wybierze zestaw  SDK na karcie Rozszerzenia, okno dialogowe Menedżer odwoływać ułatwia identyfikowanie zależności zestawu SDK przez wyświetlanie wszystkich zależności w okienku szczegółów.

Jeśli typ projektu nie obsługuje rozszerzeń, ta karta nie jest wyświetlana w oknie dialogowym Menedżer odwoływać.

## <a name="com-tab"></a>Karta COM

Karta **COM** zawiera listę wszystkich składników COM, które są dostępne do odwoływania się. Jeśli chcesz dodać odwołanie do zarejestrowanej DLL modelu COM, zawierającej manifest wewnętrzny, najpierw wyrejestruj bibliotekę DLL. W przeciwnym Visual Studio dodaje odwołanie do zestawu jako kontrolkę ActiveX, a nie jako natywną bibliotekę DLL.

Jeśli typ projektu nie obsługuje com, karta nie jest wyświetlana w oknie dialogowym Menedżer odwoływać.

## <a name="browse"></a>Przeglądaj

Możesz użyć przycisku **Przeglądaj,** aby wyszukać składnik w systemie plików.

Projekt może odwoływać się do składnika, który jest przeznaczony dla innej wersji struktury. Na przykład można utworzyć aplikację, która jest przeznaczony dla .NET Framework 4.7, ale odwołuje się do składnika, który jest przeznaczony dla .NET Framework 4. Aby uzyskać więcej informacji, zobacz [Framework targeting overview (Omówienie określania celu struktury).](../ide/visual-studio-multi-targeting-overview.md)

Unikaj dodawania odwołań do plików do danych wyjściowych innego projektu w tym samym rozwiązaniu, ponieważ ta taktyka może powodować błędy kompilacji. Zamiast tego należy użyć karty **Rozwiązanie** okna dialogowego Menedżer odwołań, aby utworzyć odwołania projekt-projekt. Ułatwia to opracowywanie zespołowe, umożliwiając lepsze zarządzanie bibliotekami klas, które tworzysz w projektach. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z uszkodzonymi odwołaniami](../ide/troubleshooting-broken-references.md).

Nie można przejść do zestawu SDK i dodać go do projektu. Możesz przejść tylko do pliku (na przykład zestawu lub *winmd)* i dodać go do projektu.

W przypadku odwołania do pliku WinMD oczekiwany układ jest taki, że pliki *\<FileName> winmd,* *\<FileName>.dll* i *\<FileName> pri* są umieszczane obok siebie. Jeśli odwołujesz się do WinMD w następujących scenariuszach, niepełny zestaw plików zostanie skopiowany do katalogu wyjściowego projektu i, w związku z tym, wystąpią błędy kompilacji i czasu wykonywania.

- **Składnik natywny:** projekt natywny utworzy po jednym winmd dla każdego rozłącznych zestawu przestrzeni nazw i jednej biblioteki DLL, która składa się z implementacji. Pliki WinMD będą miały odmienne nazwy. Podczas odwoływania się do tego pliku składnika macierzystego program MSBuild nie rozpozna, że niepowiązana nazwa WinMD jest jednym składnikiem. W związku z tym zostaną skopiowane tylko nazwy *\<FileName>.dll* i *\<FileName> winmd,* a wystąpią błędy środowiska uruchomieniowego. Aby omiń ten problem, utwórz zestaw SDK rozszerzenia. Aby uzyskać więcej informacji, [zobacz Tworzenie zestawu Software Development Kit.](../extensibility/creating-a-software-development-kit.md)

- **Korzystanie z** kontrolek: kontrolka XAML składa się co najmniej z elementów *\<FileName> winmd,* *\<FileName>.dll,* *\<FileName> pri,* *\<XamlName> xaml* *\<ImageName> i.jpg*. Podczas budowana projektu pliki zasobów, które są skojarzone z odwołaniem do pliku, nie zostaną skopiowane do katalogu wyjściowego projektu, a kopiowane będą tylko pliki *\<FileName> winmd*, *\<FileName>.dll* i *\<FileName> pri.* Jest rejestrowany błąd kompilacji informujący użytkownika, że brakuje zasobów *\<XamlName> xaml* *\<ImageName>.jpg* plików. Aby kompilacja się powiodła, trzeba ręcznie skopiować te pliki zasobów do katalogu wyjściowego projektu dla kompilacji i debugowania/czasu wykonywania. Aby ominąć ten problem, utwórz zestaw SDK rozszerzenia, korzystając z procedury opisanej w te tematu Create a Software Development Kit (Tworzenie zestawu [Software Development Kit)](../extensibility/creating-a-software-development-kit.md) lub edytuj plik projektu, aby dodać następującą właściwość:

    ```xml
    <PropertyGroup>
       <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > Jeśli dodasz właściwość, kompilacja może być wolniejsza.

## <a name="recent"></a>Ostatnie

**Zestawy**, **COM,** **Windows** i **Przeglądaj** obsługują **kartę** Ostatnie, która wylicza listę składników, które zostały ostatnio dodane do projektów.

## <a name="search"></a>Wyszukaj

Pasek wyszukiwania w oknie dialogowym Menedżer odwoływczy działa na karcie fokusu. Jeśli na przykład użytkownik na pasku wyszukiwania wcięciem "System", gdy karta Rozwiązanie jest w centrum uwagi, wyszukiwanie nie zwróci żadnych wyników, chyba że rozwiązanie składa się z nazwy projektu zawierającej "System". 

## <a name="see-also"></a>Zobacz też

- [Zarządzanie odwołaniami w projekcie](../ide/managing-references-in-a-project.md)
