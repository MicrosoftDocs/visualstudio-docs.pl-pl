---
title: Aktualizowanie Visual Studio rozszerzenia
description: Dowiedz się, jak zaktualizować rozszerzenie Visual Studio do pracy z Visual Studio 2022.
ms.date: 06/08/2021
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: 512e9a71cde5ca29c737c1623aa0c8f9c37dd60d
ms.sourcegitcommit: 0499d813d5c24052c970ca15373d556a69507250
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2021
ms.locfileid: "113046134"
---
# <a name="update-a-visual-studio-extension-for-visual-studio-2022"></a>Aktualizacja rozszerzenia Visual Studio dla programu Visual Studio 2022

> [!IMPORTANT]
> Porady w tym przewodniku mają pomóc deweloperom w migrowaniu rozszerzeń, które wymagają istotnych zmian do pracy zarówno w programie Visual Studio 2019, jak i 2022. W takich przypadkach zaleca się użycie dwóch projektów VSIX i kompilacji warunkowej.
> Wiele rozszerzeń będzie w stanie działać zarówno w programie Visual Studio 2019, jak i 2022 z niewielkimi zmianami, które nie będą wymagały zaleceń dotyczących modernizacji rozszerzenia w tym przewodniku.
> Wypróbuj rozszerzenie w programie Visual Studio 2022 i oceń, która opcja jest najlepsza dla Twojego rozszerzenia.

Możesz zaktualizować rozszerzenie do pracy z programem Visual Studio 2022 (wersja zapoznawcza), korzystając z tego przewodnika. Visual Studio 2022 (wersja zapoznawcza) jest aplikacją 64-bitową i wprowadza pewne istotne zmiany w zestawie VS SDK. Ten przewodnik zawiera instrukcje dotyczące kroków wymaganych do pracy rozszerzenia z bieżącą wersji zapoznawczą programu Visual Studio 2022, dzięki czemu rozszerzenie może być gotowe do zainstalowania przez użytkowników przed Visual Studio 2022 r. osiągnie wersji gachodniej.

## <a name="installing"></a>Instalowanie

Zainstaluj Visual Studio 2022 (wersja zapoznawcza) z plików [do pobrania Visual Studio 2022 Preview.](https://visualstudio.microsoft.com/vs/preview/vs2022)

### <a name="extensions-written-in-a-net-language"></a>Rozszerzenia napisane w języku .NET

Zestaw VS SDK przeznaczony Visual Studio 2022 dla rozszerzeń zarządzanych jest dostępny *wyłącznie w* pniu NuGet:

- [Metapakiet Microsoft.VisualStudio.Sdk](https://www.nuget.org/packages/Microsoft.VisualStudio.Sdk/) (wersje 17.x) zawiera większość lub wszystkie potrzebne zestawy referencyjne.
- Pakiet [Microsoft.VSSDK.BuildTools](https://www.nuget.org/packages/Microsoft.VSSDK.BuildTools/) (wersje 17.x) powinien być przywoływyny z projektu VSIX, aby można było utworzyć zgodny z programem VSIX Visual Studio 2022 r.

Rozszerzenia muszą *być* kompilowane przy użyciu platformy "Dowolny procesor CPU" lub "x64". Platforma "x86" jest niezgodna Visual Studio 64-bitowym procesem w wersji 2022.

### <a name="extensions-written-in-c"></a>Rozszerzenia napisane w języku C++

Zestaw VS SDK dla rozszerzeń skompilowanych przy użyciu języka C++ jest dostępny z zainstalowanym zestawem SDK Visual Studio, jak zwykle.

Rozszerzenia muszą *być skompilowane* specjalnie dla zestawu SDK Visual Studio 2022 i dla amd64.

### <a name="update-your-extension-to-visual-studio-2022"></a>Zaktualizuj rozszerzenie do wersji Visual Studio 2022

#### <a name="extensions-with-running-code"></a>Rozszerzenia z uruchomionym kodem

Rozszerzenia z uruchomionym kodem *muszą być* kompilowane specjalnie dla Visual Studio 2022. Visual Studio 2022 nie będzie ładować żadnych rozszerzeń, które nie są przeznaczone Visual Studio 2022.

Dowiedz się, jak przeprowadzić migrację rozszerzeń przed Visual Studio 2022 r. do Visual Studio 2022 r.:

1. [Modernizuj projekty.](#modernize-your-vsix-project)
1. [Refaktoryzowanie kodu źródłowego w udostępniony projekt,](#use-shared-projects-for-multi-targeting) aby umożliwić ukierunkowanie Visual Studio 2022 r. i starszych wersji.
1. [Dodaj docelowy Visual Studio VSIX z 2022](#add-a-visual-studio-2022-target)r. i naszą tabelę ponownego mapowania [pakietów/zestawu](migrated-assemblies.md).
1. [Wprowadzenie niezbędnych dostosowań kodu](#handle-breaking-api-changes).
1. [Testowanie rozszerzenia Visual Studio 2022.](#test-your-extension)
1. [Publikowanie rozszerzenia Visual Studio 2022.](#publish-your-extension)

#### <a name="extensions-without-running-code"></a>Rozszerzenia bez uruchamiania kodu

Rozszerzenia, które nie zawierają żadnego uruchomionego kodu (na  przykład szablony projektów/elementów), nie muszą być zgodne z powyższymi krokami, w tym do produkcji dwóch odrębnych plików VSIX.

Zamiast tego jeden VSIX powinien zostać zmodyfikowany tak, aby jego `source.extension.vsixmanifest` plik deklarował dwa obiekty docelowe instalacji, w ten sposób:

```xml
<Installation>
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0,17.0)">
      <ProductArchitecture>x86</ProductArchitecture>
   </InstallationTarget>
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
      <ProductArchitecture>amd64</ProductArchitecture>
   </InstallationTarget>
</Installation>
```

Możesz pominąć kroki opisane w tym artykule dotyczące korzystania z udostępnionych projektów i wielu plików VSIX. Możesz kontynuować [testowanie!](#test-your-extension)

> [!NOTE]
> Jeśli podczas tworzenia nowego rozszerzenia *usługi* Visual Studio używasz programu Visual Studio 2022 (wersja zapoznawcza) i chcesz (również) korzystać z wersji docelowej Visual Studio 2019 lub starszej, zapoznaj się z tym przewodnikiem [.](target-previous-versions.md)

### <a name="msbuild-tasks"></a>zadania programu MSBuild

Jeśli tworzyć zadania programu MSBuild, należy pamiętać, że w programie Visual Studio 2022 jest znacznie bardziej prawdopodobne, że zostaną one załadowane w 64-bitowym MSBuild.exe procesie. Jeśli zadanie wymaga uruchomienia procesu 32-bitowego, zapoznaj się z tą dokumentacją programu [MSBuild,](../../msbuild/how-to-configure-targets-and-tasks.md#usingtask-attributes-and-task-parameters) aby upewnić się, że program MSBuild wie, że załaduje zadanie w procesie 32-bitowym.

## <a name="modernize-your-vsix-project"></a>Modernizuj projekt VSIX

Przed dodaniem Visual Studio 2022 r. do rozszerzenia zdecydowanie zalecamy poświęć ten czas na oczyszczenie i zmodernizowanie istniejącego projektu, a następnie jego dalsze rozszerzenie, w tym:

1. [Migracja z packages.config `PackageReference` do . ](/nuget/consume-packages/migrate-packages-config-to-package-reference)

1. Zastąp wszelkie odwołania do zestawu ZESTAWU VS SDK elementami PackageReference.

   ```diff
   -<Reference Include="Microsoft.VisualStudio.OLE.Interop" />
   +<PackageReference Include="Microsoft.VisualStudio.OLE.Interop" Version="..." />
   ```

   > [!TIP]
   > Można zastąpić wiele *odwołań* do zestawu tylko jednym *packageReference* do naszego metapakiet:
   >
   >```diff
   >-<Reference Include="Microsoft.VisualStudio.OLE.Interop" />
   >-<Reference Include="Microsoft.VisualStudio.Interop" />
   >-<Reference Include="Microsoft.VisualStudio.Interop.8.0" />
   >+<PackageReference Include="Microsoft.VisualStudio.Sdk" Version="..." />
   >```

   Pamiętaj, aby wybrać wersje pakietów, które pasują do minimalnej Visual Studio docelowego pakietu.

   Niektóre zestawy, które nie są unikatowe dla zestawu VS SDK (na przykład Newtonsoft.Json.dll), mogą być wykrywalne za pomocą prostego odwołania przed programem Visual Studio 2022, ale w programie Visual Studio 2022 wymagają odwołania do pakietu, ponieważ w programie Visual Studio 2022 usuwamy niektóre katalogi środowiska uruchomieniowego i zestawu SDK programu Visual Studio z domyślnej ścieżki wyszukiwania zestawów w programie `<Reference Include="Newtonsoft.Json" />` MSBuild.

   Podczas przełączania z bezpośrednich odwołań do zestawów na odwołania do pakietów NuGet można uzyskać dodatkowe odwołania do zestawów i pakiety analizatora, ponieważ program NuGet automatycznie instaluje przechodnie zamknięcie zależności. Zwykle jest to prawidłowe, ale może spowodować oflagowane dodatkowe ostrzeżenia podczas kompilacji. Przećlij te ostrzeżenia i rozwiąż jak najwięcej problemów. Rozważ pominięcie tych ostrzeżeń, których nie można rozwiązać przy użyciu regionów w `#pragma warning disable <id>` kodzie.

## <a name="use-shared-projects-for-multi-targeting"></a>Use shared projects for multi-targeting (Korzystanie z udostępnionych projektów dla wieloadyscyjnych projektów)

[Projekty udostępnione](/xamarin/cross-platform/app-fundamentals/shared-projects?tabs=windows) to typ projektu, który został wprowadzony w Visual Studio 2015 r. Projekty udostępnione w Visual Studio umożliwiają współużytkować pliki kodu źródłowego między wieloma projektami i tworzyć je inaczej przy użyciu symboli kompilacji warunkowej i unikatowych zestawów odwołań.

Ponieważ program Visual Studio 2022 wymaga oddzielnego zestawu zestawów odwołań ze wszystkich poprzednich wersji programu VS, nasze wskazówki dotyczące korzystania z udostępnionych projektów w celu wygodnego wielokierunkowego kierowania rozszerzenia do wersji starszych niż Visual Studio 2022 i Visual Studio 2022 (i nowszych), zapewniając udostępnianie kodu, ale odrębne odwołania.

W kontekście rozszerzeń Visual Studio można mieć jeden projekt VSIX dla wersji Visual Studio 2022 i nowszej oraz jeden projekt VSIX dla wersji Visual Studio 2019 i starszych. Każdy z tych projektów zawierałby tylko odwołania do pakietu i do zestawu `source.extension.vsixmanifest` SDK 16.x lub zestawu SDK 17.x. Te projekty VSIX będą również miały udostępnione odwołanie do nowego projektu udostępnionego, który będzie hostować cały kod źródłowy, który można udostępnić w dwóch wersjach programu VS.

Na początek w tym dokumencie przyjęto założenie, że masz już projekt VSIX przeznaczony dla programu Visual Studio 2019 i że chcesz, aby twoje rozszerzenie działało w programie Visual Studio 2022.

Wszystkie te kroki można wykonać od Visual Studio 2019 r.

1. Jeśli jeszcze tego nie zrobiono, [z modernizuj](#modernize-your-vsix-project) projekty, aby ułatwić kroki opisane w dalszej części tego procesu aktualizacji.

1. Dodaj nowy projekt udostępniony do rozwiązania dla każdego istniejącego projektu, który odwołuje się do zestawu VS SDK.
   ![Polecenie Dodaj nowy projekt ](media/update-visual-studio-extension/add-new-project.png)
    ![ Szablon nowego projektu](media/update-visual-studio-extension/new-shared-project-template.png)

1. Dodaj odwołanie z każdego projektu odwołującego się do zestawu SDK programu VS do jego udostępnionego odpowiednika projektu.
   :::image type="content" source="media/update-visual-studio-extension/add-shared-project-reference.png" alt-text="Dodawanie udostępnionego odwołania do projektu" lightbox="media/update-visual-studio-extension/add-shared-project-reference.png":::

1. Przenieś cały kod źródłowy (w tym cs, resx) z każdego projektu odwołującego się do zestawu SDK programu VS do jego udostępnionego odpowiednika projektu.
Pozostaw `source.extension.vsixmanifest` plik w projekcie VSIX.
   ![Udostępniony projekt zawiera wszystkie pliki źródłowe](media/update-visual-studio-extension/source-files-in-shared-project.png)

1. Pliki metadanych (informacje o wersji, licencja, ikony itp.) i pliki VSCT powinny zostać przeniesione do katalogu udostępnionego i dodane jako pliki połączone do projektu VSIX.
   ![Dodawanie metadanych i plików VSCT jako połączonych plików](media/update-visual-studio-extension/add-linked-items-to-vsix.png)
    - W przypadku plików metadanych ustaw wartość buildAction na i `Content` ustaw wartość Include w VSIX na `true` .

      ![Uwzględnianie plików metadanych w VSIX](./media/update-visual-studio-extension/include-metadata-files-in-vsix.png)
    - W przypadku plików VSCT ustaw wartość buildAction na i `VSCTCompile` nie dołączaj do vsix.
      Visual Studio może narzekać, że to ustawienie nie jest obsługiwane, ale można ręcznie zmienić akcję kompilacji, zwalniając projekt i `Content` zmieniając na `VSCTCompile`

    ```diff
    -<Content Include="..\SharedFiles\VSIXProject1Package.vsct">
    -  <Link>VSIXProject1Package.vsct</Link>
    -</Content>
    +<VSCTCompile Include="..\SharedFiles\VSIXProject1Package.vsct">
    +  <Link>VSIXProject1Package.vsct</Link>
    +  <ResourceName>Menus.ctmenu</ResourceName>
    +</VSCTCompile>
    ```

      ![Ustawianie plików VSCT jako VSCTCompile](media/update-visual-studio-extension/build-linked-vsct-files.png)

1. Skompilowanie projektów w celu potwierdzenia, że nie wprowadzono żadnych nowych błędów.

Projekt jest teraz gotowy do dodania obsługi Visual Studio 2022 r.

## <a name="add-a-visual-studio-2022-target"></a>Dodawanie obiektu docelowego Visual Studio 2022

W tym dokumencie przyjęto założenie, że zostały wykonane kroki mające na celu Visual Studio [rozszerzenia do udostępnionych projektów.](#use-shared-projects-for-multi-targeting)

Aby dodać obsługę Visual Studio 2022 do rozszerzenia, należy wykonać następujące kroki, które można wykonać Visual Studio 2019 r.:

1. Dodaj nowy projekt VSIX do rozwiązania. Będzie to projekt przeznaczony dla Visual Studio 2022 r. Usuń kod źródłowy, który został do tego szablonu, ale *zachowaj `source.extension.vsixmanifest` plik*.

1. W nowym projekcie VSIX dodaj odwołanie do projektu udostępnionego do tego samego projektu udostępnionego, do Visual Studio VSIX przeznaczonego dla programu Visual Studio 2019.

   ![Rozwiązanie z jednym projektem udostępnionym i dwoma projektami VSIX](media/update-visual-studio-extension/shared-project-with-two-heads.png)

1. Sprawdź, czy nowy projekt VSIX jest poprawnie skompilowany. Aby usunąć błędy kompilatora, może być konieczne dodanie odwołań, aby dopasować je do oryginalnego projektu VSIX.

1. W przypadku zarządzanych rozszerzeń programu VS zaktualizuj odwołania do pakietu z wersji 16.x (lub starszej) do wersji pakietu 17.x w pliku projektu docelowego programu Visual Studio 2022 przy użyciu narzędzia NuGet Menedżer pakietów lub bezpośrednio edytując plik projektu:

    ```diff
    -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
    +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview.1" />
    -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
    +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-preview.1" />
    ```

   Użyjesz wersji, które są faktycznie dostępne z nuget.org. Te, które były używane wcześniej, służą wyłącznie do celów demonstracyjnych.

   W wielu przypadkach identyfikatory pakietów uległy zmianie. Zapoznaj się z [tabelą mapowania pakietów/zestawu,](migrated-assemblies.md) aby uzyskać listę zmian w Visual Studio 2022 r.

   Rozszerzenia napisane w języku C++ nie mają jeszcze dostępnego zestawu SDK do skompilowania.

1. W przypadku projektów w języku C++ muszą one być skompilowane dla amd64. W przypadku rozszerzeń zarządzanych rozważ zmianę projektu z tworzenia dowolnego procesora CPU na obiekt docelowy , aby odzwierciedlić, że w programie Visual Studio 2022 Twoje rozszerzenie zawsze ładuje się w procesie `x64` 64-bitowym. `Any CPU` jest również w porządku, ale może dawać ostrzeżenia, jeśli odwołujesz się do jakichkolwiek natywnych plików binarnych tylko dla x64.

   Wszelkie zależności, które rozszerzenie może mieć w module macierzystym, trzeba będzie zaktualizować z obrazu x86 do obrazu amd64.

1. Edytuj `source.extension.vsixmanifest` plik, aby odzwierciedlał wartości Visual Studio 2022 r. Ustaw `<InstallationTarget>` tag w celu odzwierciedlenia Visual Studio 2022 r. i wskazania ładunku amd64:

   ```xml
   <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
      <ProductArchitecture>amd64</ProductArchitecture>
   </InstallationTarget>
   ```

   W Visual Studio 2019 r. projektant tego pliku nie uwidacznia nowego elementu, więc tę zmianę należy wykonać za pomocą edytora XML, do którego dostęp można uzyskać za pośrednictwem polecenia Otwórz za pomocą w Eksplorator rozwiązań `ProductArchitecture` .  

   Ten `ProductArchitecture` element jest krytyczny. Visual Studio 2022 nie *zainstaluje* rozszerzenia bez niego.

   | Element | Wartość | Opis |
   | - | - | - |
   | ProductArchitecture | X86, AMD64 | Platformy obsługiwane przez ten vsix. Wielkość liter nie jest zróżnicowa. Jedna platforma na element i jeden element na element InstallTarget. W przypadku wersji produktu mniejszej niż 17.0 wartość domyślna to x86 i można ją pominąć.  W przypadku produktów w wersji 17.0 i większej ten element jest wymagany i nie ma wartości domyślnej. W Visual Studio 2022 r. jedyną prawidłową zawartością dla tego elementu jest "amd64". |

1. W pliku source.extension.vsixmanifest należy wprowadzić inne zmiany, aby dopasować je do tego, które jest Visual Studio 2019 r. (jeśli takie są). Bardzo ważne jest, aby identyfikator VSIX w `Identity` elemencie manifestu był identyczny dla obu rozszerzeń.

W tym momencie masz rozszerzenie VSIX Visual Studio 2022. Należy skompilować projekt VSIX Visual Studio 2022 i przechodzić przez wszelkie podziały [kompilacji, które są wyświetlane.](#handle-breaking-api-changes) Jeśli nie masz przerw w kompilacji w docelowym projekcie VSIX Visual Studio 2022, gratulacje: wszystko jest gotowe do testowania!

## <a name="handle-breaking-api-changes"></a>Obsługa zmian interfejsu API, które są istotne

W wersji [20222](breaking-api-list.md) w wersji 2022 Visual Studio zmiany interfejsu API, które mogą wymagać zmian w kodzie, od kiedy był on już w poprzednich wersjach. Zapoznaj się z tym dokumentem, aby uzyskać porady dotyczące aktualizowania kodu dla każdego z nich.

Podczas dostosowywania kodu zalecamy korzystanie [](#use-conditional-compilation-symbols) z kompilacji warunkowej, aby kod nadal obsługi Visual Studio 2022 r. był kontynuowany, dodając obsługę Visual Studio 2022 r.

Gdy otrzymasz rozszerzenie Visual Studio 2022, przejdź do [testowania](#test-your-extension).

## <a name="use-conditional-compilation-symbols"></a>Używanie symboli kompilacji warunkowej

Jeśli chcesz użyć tego samego kodu źródłowego, nawet tego samego pliku, dla programu Visual Studio 2022 i wcześniejszych wersji, może być konieczne użycie kompilacji warunkowej, aby można było utworzyć fordy kodu w celu dostosowania się do zmian przerywania. Kompilacja warunkowa to funkcja języków C#, Visual Basic i C++, których można używać do współużytkowania większości kodu przy jednoczesnym dostępie do rozbieżnych interfejsów API w określonych miejscach.

Więcej informacji na temat użycia dyrektyw preprocesora i symboli kompilacji warunkowej można znaleźć w dyrektywie [preprocesora](/dotnet/csharp/language-reference/preprocessor-directives#conditional-compilation)microsoft docs #if .

W projektach, które są Visual Studio wcześniejszych wersjach, będzie potrzebny symbol kompilacji warunkowej, który następnie może służyć do forkowania kodu w celu używania różnych interfejsów API. Symbol kompilacji warunkowej można ustawić na stronie właściwości projektu, jak pokazano na poniższej ilustracji:

![Ustawianie symboli kompilacji warunkowej](media/update-visual-studio-extension/conditional-compilation-symbols.png)

Pamiętaj, aby ustawić symbol kompilacji dla *wszystkich* konfiguracji, ponieważ domyślnie wprowadzany symbol może dotyczyć tylko jednej konfiguracji.

### <a name="c-techniques"></a>Techniki języka C \#

Następnie można użyć tego symbolu jako dyrektywy przedprocesowej ( `#if` ), jak pokazano w poniższym kodzie. Następnie możesz utworzyć widelec kodu, aby poradzić sobie ze zmianą przerywaną między różnymi Visual Studio wersjami.

```cs
    Guid myGuid = new Guid("{633FBA02-719B-40E7-96BF-0899767CD104}");
    uint myFlags = 0;
    IVsShell shell = await AsyncServiceProvider.GlobalProvider.GetServiceAsync<SVsShell, IVsShell>();
#if Visual Studio 2019
    shell.LoadUILibrary(myGuid, myFlags, out uint ptrLib);
#else
    shell.LoadUILibrary(myGuid, myFlags, out IntPtr ptrLib);
#endif
```

W niektórych przypadkach można po prostu użyć funkcji , aby uniknąć nazewnictwa typu, co pozwala `var` uniknąć konieczności stosowania `#if` regionów. Powyższy fragment kodu można również zapisywać w następujący sposób:

```cs
    Guid myGuid = new Guid("{633FBA02-719B-40E7-96BF-0899767CD104}");
    uint myFlags = 0;
    IVsShell shell = await AsyncServiceProvider.GlobalProvider.GetServiceAsync<SVsShell, IVsShell>();
    shell.LoadUILibrary(myGuid, myFlags, out var ptrLib);
```

Korzystając ze składni, zwróć uwagę, jak można użyć listy rozwijanej kontekstu usługi językowej w dokumencie przedstawionym poniżej, aby zmienić wyróżnianie składni, a druga pomaga usłudze językowej skupić uwagę na jednej docelowej wersji Visual Studio dla naszego rozszerzenia a `#if` innej.

![Kompilacja warunkowa w udostępnionym projekcie](media/update-visual-studio-extension/conditional-compilation-if-region.png)

### <a name="xaml-sharing-techniques"></a>Techniki udostępniania XAML

Język XAML nie ma preprocesora umożliwiającego dostosowywanie zawartości na podstawie symboli preprocesora. Może być wymagane kopiowanie i obsługa dwóch stron XAML, gdzie ich zawartość Visual Studio 2022 i wcześniejszych wersjach.

Jednak w niektórych przypadkach odwołanie do typu, który istnieje w odrębnych zestawach w programie Visual Studio 2022 i wcześniejszych wersjach, może być nadal reprezentowane w jednym pliku XAML przez usunięcie przestrzeni nazw odwołującej się do zestawu:

```diff
-xmlns:vsui="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.14.0"
-Value="{DynamicResource {x:Static vsui:TreeViewColors.SelectedItemActiveBrushKey}}"
+Value="{DynamicResource TreeViewColors.SelectedItemActiveBrushKey}"
```

## <a name="test-your-extension"></a>Testowanie rozszerzenia

Aby przetestować rozszerzenie dla wersji Visual Studio 2022, należy zainstalować Visual Studio 2022 (wersja zapoznawcza).
Nie będzie można uruchamiać rozszerzeń 64-bitowych w wersjach programu Visual Studio starszych niż Visual Studio 2022 (wersja zapoznawcza).

Za pomocą programu Visual Studio 2022 (wersja zapoznawcza) można kompilować i testować rozszerzenia niezależnie od tego, czy są one Visual Studio 2022 r., czy starszej wersji. Podczas uruchamiania projektu VSIX od Visual Studio 2022 r. zostanie uruchomione eksperymentalne Visual Studio projektu.

Zdecydowanie zalecamy przetestowanie z każdą wersją Visual Studio, która ma być wspierana przez rozszerzenie.

Teraz możesz opublikować [rozszerzenie](#publish-your-extension).

## <a name="publish-your-extension"></a>Publikowanie rozszerzenia

Świetnie, więc dodano element docelowy Visual Studio 2022 do rozszerzenia i przetestowano go. Teraz możesz opublikować rozszerzenie dla całego świata.

### <a name="visual-studio-marketplace"></a>Witryna Visual Studio Marketplace

Opublikowanie rozszerzenia w [Visual Studio Marketplace](https://marketplace.visualstudio.com/) to doskonały sposób na znalezienie i zainstalowanie rozszerzenia przez nowych użytkowników. Niezależnie od tego, czy rozszerzenie jest przeznaczone Visual Studio 2022 r., czy też dotyczy starszych wersji programu VS, w witrynie Marketplace będzie dostępna pomoc techniczna.

W przyszłości w witrynie Marketplace będzie można przekazać wiele plików VSIX tylko do jednej oferty w witrynie Marketplace, co umożliwi przekazanie pliku VSIX docelowego dla programu Visual Studio 2022 i produktu VSIX z wersji Visual Studio 2022. Podczas korzystania z menedżera rozszerzeń programu VS użytkownicy automatycznie uzyskają właściwy vsix dla zainstalowanej przez nich wersji programu VS.

W przypadku wersji zapoznawczych Visual Studio 2022 r. platforma Marketplace będzie obsługiwać tylko jeden plik VSIX na ofertę w witrynie Marketplace. Chociaż Visual Studio 2022 r. jest w wersji zapoznawczej, zachęcamy do korzystania z oddzielnej oferty witryny Marketplace Visual Studio 2022 dla rozszerzenia. Dzięki temu możesz w razie potrzeby iterować rozszerzenie Visual Studio 2022 bez wpływu na wcześniejsze wersje Visual Studio. Możesz również oznaczyć rozszerzenie jako "wersja zapoznawcza", aby ustawić oczekiwanie, że będzie prawdopodobnie mniej niezawodne, nawet jeśli źródłem tej zawodności jest Visual Studio 2022 r., niż rozszerzenie główne.

### <a name="custom-installer"></a>Instalator niestandardowy

W przypadku kompilowania pliku MSI/EXE w celu zainstalowania rozszerzenia i vsixinstaller.exe do zainstalowania (części) rozszerzenia należy pamiętać, że instalator VSIX w programie Visual Studio 2022 został zaktualizowany. Deweloperzy będą musieli zainstalować rozszerzenia programu Visual Studio 2022 w wersji instalatora VSIX Visual Studio 2022. Instalator VSIX w wersji Visual Studio 2022 zainstaluje również odpowiednie rozszerzenia przeznaczone dla poprzednich wersji systemu Visual Studio, które są instalowane obok programu Visual Studio 2022 na tej samej maszynie.

### <a name="network-share"></a>Udział sieciowy

Możesz udostępnić rozszerzenie za pośrednictwem sieci LAN lub w inny sposób. W przypadku docelowych wersji Visual Studio 2022 i 2022 w wersjach 2022 i Visual Studio 2022 konieczne będzie udostępnienie wielu plików VSIX i nadaj im nazwy plików (lub umieść je w unikatowych folderach), które ułatwiają użytkownikom informacje o tym, który vsix zainstalować na podstawie zainstalowanej wersji systemu Visual Studio.

### <a name="other-considerations"></a>Inne zagadnienia

#### <a name="dependencies"></a>Zależności

Jeśli vsix określa inny VSIX jako zależność za pośrednictwem elementu, każdy z nich, do których się odwołuje, musi zostać zainstalowany w tych samych elementach docelowych i architekturach produktów, co `<dependency>` vsix. Jeśli zależny vsix nie obsługuje docelowej instalacji Visual Studio, vsix nie powiedzie się. Zależny vsix może obsługiwać więcej obiektów docelowych i architektur niż Twoje, a nie mniej. To ograniczenie oznacza, że podejście do wdrażania i dystrybucji w vsix z zależnościami powinno być duplikatem ich zależności.

## <a name="q--a"></a>Pytania i odpowiedzi

**Pyt.:** Moje rozszerzenie nie wymaga żadnych zmian międzyplatopowych, ponieważ udostępnia tylko dane (na przykład szablony), czy mogę utworzyć jedno rozszerzenie, które obejmuje również Visual Studio 2022?

**Odpowiedź:** Tak!  Aby [uzyskać więcej informacji na ten temat,](#extensions-without-running-code) zobacz Extensions without running code (Rozszerzenia bez uruchamiania kodu).

**Pytanie:** Zależność NuGet powoduje wprowadzenie starych zestawów międzyoptykowych i powoduje konflikt klas.

**A**: Dodaj następujący wiersz do pliku csproj, aby uniknąć duplikowania zestawów:

```xml
    <PackageReference Include="<Name of offending assembly>" ExcludeAssets="compile" PrivateAssets="all" />
```

Uniemożliwi to importowanie starej wersji zestawu z innych zależności przez odwołania do pakietu.

**Pytanie:** Moje polecenia i klawisze dostępu nie działają w Visual Studio po przełączeniu plików źródłowych na udostępniony projekt.

**A:** [Krok 2.4](samples.md#step-2---refactor-source-code-into-a-shared-project) przykładu Optymalizator obrazów pokazuje, jak dodać pliki VSCT jako połączone elementy, aby zostały skompilowane do pliku VSCT.

## <a name="next-steps"></a>Następne kroki

Wykonaj przykład krok po kroku, [ImageOptimizer,](samples.md)z linkami do projektu i zmianami kodu dla każdego kroku.
