---
title: Aktualizowanie istniejącej aplikacji do programu MSBuild 15 | Microsoft Docs
description: Dowiedz się, jak upewnić się, że kompilacje programistyczne z aplikacji są gotowe do użycia w programie Visual Studio lub MSBuild.exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bd7f47466074536c9088840e726f768f62f9346b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965931"
---
# <a name="update-an-existing-application-for-msbuild-15"></a>Aktualizowanie istniejącej aplikacji dla programu MSBuild 15

W wersjach programu MSBuild wcześniejszych niż 15,0 program MSBuild został załadowany z globalnej pamięci podręcznej zestawów (GAC), a rozszerzenia programu MSBuild zostały zainstalowane w rejestrze. To gwarantuje, że wszystkie aplikacje używają tej samej wersji programu MSBuild i miały dostęp do tych samych zestawów narzędzi, ale uniemożliwiają instalacje równoległe różnych wersji programu Visual Studio.

Aby można było obsłużyć szybsze, mniejsze i równoległe instalacje, program Visual Studio 2017 i jego nowsze wersje nie umieszczają w pamięci podręcznej programu MSBuild ani nie modyfikują rejestru. Niestety, oznacza to, że aplikacje, które chcą używać interfejsu API programu MSBuild do szacowania lub kompilowania projektów, nie mogą niejawnie polegać na instalacji programu Visual Studio.

## <a name="use-msbuild-from-visual-studio"></a>Korzystanie z programu MSBuild w programie Visual Studio

Aby upewnić się, że kompilacje programistyczne z aplikacji są gotowe do użycia w programie Visual Studio lub *MSBuild.exe*, Załaduj zestawy MSBuild z programu Visual Studio i użyj zestawów SDK dostępnych w programie Visual Studio. Pakiet NuGet Microsoft. Build. Locator usprawnia ten proces.

## <a name="use-microsoftbuildlocator"></a>Korzystanie z Microsoft. Build. Locator

W przypadku ponownej dystrybucji *Microsoft.Build.Locator.dll* z aplikacją nie będzie konieczne dystrybuowanie innych zestawów programu MSBuild.

Aktualizacja projektu do korzystania z programu MSBuild 15 i interfejsu API lokalizatora wymaga kilku zmian w projekcie opisanych poniżej. Aby zobaczyć przykład zmian wymaganych do zaktualizowania projektu, zobacz [zatwierdzenia wykonane w przykładowym projekcie w repozytorium MSBuildLocator](https://github.com/Microsoft/MSBuildLocator/commits/example-updating-to-msbuild-15).

### <a name="change-msbuild-references"></a>Zmień odwołania MSBuild

Aby upewnić się, że program MSBuild ładuje się z lokalizacji centralnej, nie należy rozpowszechniać jej zestawów z aplikacją.

Mechanizm zmiany projektu, aby uniknąć ładowania MSBuild z centralnej lokalizacji, zależy od tego, w jaki sposób odwołujesz się do programu MSBuild.

#### <a name="use-nuget-packages-preferred"></a>Użyj pakietów NuGet (preferowany)

W tych instrukcjach przyjęto założenie, że używasz [odwołań NuGet w stylu PackageReference](/nuget/consume-packages/package-references-in-project-files).

Zmień pliki projektu, aby odwoływać się do zestawów MSBuild z ich pakietów NuGet. Określ `ExcludeAssets=runtime` , aby poinformować NuGet, że zestawy są konieczne tylko w czasie kompilacji, i nie powinny być kopiowane do katalogu wyjściowego.

Wersja główna i pomocnicza pakietów MSBuild musi być mniejsza lub równa minimalnej wersji programu Visual Studio, która ma być obsługiwana. Jeśli na przykład chcesz obsługiwać program Visual Studio 2017 i jego nowsze wersje, wersja pakietu referencyjnego `15.1.548` .

Na przykład można użyć tego kodu XML:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Build" Version="15.1.548" ExcludeAssets="runtime" />
  <PackageReference Include="Microsoft.Build.Utilities.Core" Version="15.1.548" ExcludeAssets="runtime" />
</ItemGroup>
```

#### <a name="use-extension-assemblies"></a>Użyj zestawów rozszerzeń

Jeśli nie można używać pakietów NuGet, można odwoływać się do zestawów programu MSBuild dystrybuowanych z programem Visual Studio. Jeśli bezpośrednio odwołujesz się do programu MSBuild, upewnij się, że nie będzie on kopiowany do katalogu wyjściowego przez ustawienie `Copy Local` `False` . W pliku projektu to ustawienie będzie wyglądać podobnie do następującego kodu:

```xml
    <Reference Include="Microsoft.Build, Version=15.1.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
      <Private>False</Private>
    </Reference>
```

#### <a name="binding-redirects"></a>Przekierowania powiązań

Odwołuje się do pakietu Microsoft. Build. Locator, aby upewnić się, że aplikacja automatycznie używa wymaganych przekierowań powiązań do wersji 15.1.0.0. Przekierowania powiązań do tej wersji obsługują zarówno program MSBuild 15, jak i program MSBuild 16.

### <a name="ensure-output-is-clean"></a>Upewnij się, że dane wyjściowe są czyste

Skompiluj projekt i Sprawdź katalog danych wyjściowych, aby upewnić się, że nie zawiera on żadnych *Microsoft. Build. \* . Zestawy dll* inne niż *Microsoft.Build.Locator.dll* dodane w następnym kroku.

### <a name="add-package-reference-for-microsoftbuildlocator"></a>Dodawanie odwołania do pakietu dla elementu Microsoft. Build. Locator

Dodaj odwołanie do pakietu NuGet dla elementu [Microsoft. Build. Locator](https://www.nuget.org/packages/Microsoft.Build.Locator/).

```xml
    <PackageReference Include="Microsoft.Build.Locator">
      <Version>1.1.2</Version>
    </PackageReference>
```

Nie należy określać `ExcludeAssets=runtime` pakietu Microsoft. Build. Locator.

### <a name="register-instance-before-calling-msbuild"></a>Zarejestruj wystąpienie przed wywołaniem MSBuild

> [!IMPORTANT]
> Nie można odwoływać się do żadnych typów MSBuild (z `Microsoft.Build` przestrzeni nazw) w metodzie wywołującej MSBuildLocator. Nie można na przykład wykonać tego czynności:
>
> ```csharp
> void ThisWillFail()
> {
>     MSBuildLocator.RegisterDefaults();
>     Project p = new Project(SomePath); // Could be any MSBuild type
>     // Code that uses the MSBuild type
> }
> ```
>
> Zamiast tego należy wykonać następujące czynności:
>
> ```csharp
> void MethodThatDoesNotDirectlyCallMSBuild()
> {
>     MSBuildLocator.RegisterDefaults();
>     MethodThatCallsMSBuild();
> }
> 
> void MethodThatCallsMSBuild()
> {
>     Project p = new Project(SomePath);
>     // Code that uses the MSBuild type
> }
> ```

Najprostszym sposobem dodania wywołania do interfejsu API lokalizatora jest dodanie wywołania do

```csharp
MSBuildLocator.RegisterDefaults();
```

w kodzie uruchomienia aplikacji.

Jeśli potrzebujesz bardziej precyzyjnej kontroli nad ładowaniem programu MSBuild, możesz wybrać wynik, który ma `MSBuildLocator.QueryVisualStudioInstances()` zostać przekazany `MSBuildLocator.RegisterInstance()` ręcznie, ale zazwyczaj nie jest to konieczne.
