---
title: Aktualizowanie istniejącej aplikacji do programu MSBuild 15 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0487ee8cdbb89b7c781cb13225d209d840eda134
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53836874"
---
# <a name="update-an-existing-application-for-msbuild-15"></a>Aktualizowanie istniejących aplikacji dla programu MSBuild 15

W wersjach programu MSBuild przed 15.0 program MSBuild został załadowany z globalnej pamięci podręcznej zestawów (GAC) i rozszerzenia programu MSBuild zostały zainstalowane w rejestrze. To zapewnia wszystkie aplikacje używane w tej samej wersji programu MSBuild logować się na tym samym zestawy narzędzi, ale uniemożliwił instalacje side-by-side w różnych wersjach programu Visual Studio.

Aby obsługiwać szybciej i mniejsze i side-by-side instalacji, programu Visual Studio 2017 już nie umieszcza MSBuild w pamięci podręcznej GAC lub modyfikuje rejestr. Niestety oznacza to, że aplikacje, które chcą oceny lub kompilowanie projektów za pomocą interfejsu API programu MSBuild nie można niejawnie polegać na instalację programu Visual Studio.

## <a name="use-msbuild-from-visual-studio"></a>Użyj programu MSBuild w programie Visual Studio

Aby upewnić się, że programowe kompilacje z aplikacji są takie same kompilacje wykonywane w programie Visual Studio lub *MSBuild.exe*załadować zestawów programu MSBuild w programie Visual Studio i korzystanie z zestawów SDK dostępnych w programie Visual Studio. Pakiet Microsoft.Build.Locator NuGet usprawnia ten proces.

## <a name="use-microsoftbuildlocator"></a>Użyj Microsoft.Build.Locator

Jeśli ponownie dystrybuujesz *Microsoft.Build.Locator.dll* z aplikacją, nie trzeba rozpowszechniać innych zestawów programu MSBuild.

Aktualizowanie projektu, aby użyć programu MSBuild 15 i lokalizatora interfejsu API wymaga kilku zmian w projekcie, opisane poniżej. Aby zapoznać się przykładem zmiany musieli zaktualizować projekt, zobacz [zatwierdzenia wprowadzonych przykładowy projekt w repozytorium MSBuildLocator](https://github.com/Microsoft/MSBuildLocator/commits/example-updating-to-msbuild-15).

### <a name="change-msbuild-references"></a>Zmień odwołania programu MSBuild

Aby upewnić się, że program MSBuild ładuje z centralnej lokalizacji, nie należy rozesłać jej zestawy z aplikacją.

Zmienianie projektu pozwala uniknąć wczytywania programu MSBuild z centralnej lokalizacji przy użyciu mechanizmu zależy od tego, jak możesz odwoływać się do programu MSBuild.

#### <a name="use-nuget-packages-preferred"></a>Korzystanie z pakietów NuGet (preferowane)

W poniższych instrukcjach przyjęto, że używasz [odwołań NuGet PackageReference stylu](https://docs.microsoft.com/nuget/consume-packages/package-references-in-project-files).

Zmień swoje pliki projektu, aby odwoływać się do zestawów programu MSBuild z pakietów NuGet. Określ `ExcludeAssets=runtime` NuGet można stwierdzić, że zestawy są wymagane tylko w czasie kompilacji, a nie powinny być kopiowany do katalogu wyjściowego.

Główna i pomocnicza wersja pakietów MSBuild musi być mniejsza lub równa minimalnej wersji programu Visual Studio, które chcesz obsługiwać. Jeśli chcesz obsługiwać dowolną wersję programu Visual Studio 2017, odwoływać się do pakietu wersji `15.1.548`.

Na przykład można użyć tego kodu XML:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Build" Version="15.1.548" ExcludeAssets="runtime" />
  <PackageReference Include="Microsoft.Build.Utilities" Version="15.1.548" ExcludeAssets="runtime" />
</ItemGroup>
```

#### <a name="use-extension-assemblies"></a>Korzystanie z zestawów rozszerzeń

Jeśli nie możesz użyć pakietów NuGet, możesz odwoływać się zestawów programu MSBuild, które są dystrybuowane za pomocą programu Visual Studio. Jeśli bezpośrednio odwołują się MSBuild upewnij się, że jej nie będą kopiowane do katalogu wyjściowego, ustawiając `Copy Local` do `False`. W pliku projektu to ustawienie będzie wyglądać podobnie do poniższego kodu:

```xml
    <Reference Include="Microsoft.Build, Version=15.1.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
      <Private>False</Private>
    </Reference>
```

#### <a name="binding-redirects"></a>Przekierowania powiązań

Odwołanie do pakietu Microsoft.Build.Locator, aby upewnić się, że aplikacja używa automatycznie wymaganego powiązania przekierowuje wszystkich wersji zestawów programu MSBuild do wersji `15.1.0.0`.

### <a name="ensure-output-is-clean"></a>Upewnij się, że dane wyjściowe są czyste

Kompilowanie projektu i Sprawdź katalog wyjściowy, aby upewnić się, że nie zawiera żadnego *Microsoft.Build.\* Biblioteka DLL* zestawów innych niż *Microsoft.Build.Locator.dll*dodano w następnym kroku.

### <a name="add-package-reference"></a>Dodawanie odwołania do pakietu

Dodawanie odwołania do pakietu NuGet, aby [Microsoft.Build.Locator](https://www.nuget.org/packages/Microsoft.Build.Locator/).

```xml
    <PackageReference Include="Microsoft.Build.Locator">
      <Version>1.0.7-preview-ge60d679b53</Version>
    </PackageReference>
```

### <a name="register-instance-before-calling-msbuild"></a>Rejestrowanie wystąpienia przed wywołaniem programu MSBuild

Dodaj wywołanie interfejsu API lokalizatora przed wywołaniem dowolnej metody, która używa programu MSBuild.

Najprostszym sposobem, aby dodać wywołanie interfejsu API lokalizatora jest Dodaj wywołanie do

```csharp
MSBuildLocator.RegisterDefaults();
```

w kodzie uruchamiania aplikacji.

Jeśli chcesz bardziej szczegółowej kontroli nad podczas ładowania programu MSBuild, możesz wybrać wynikiem `MSBuildLocator.QueryVisualStudioInstances()` do przekazania do `MSBuildLocator.RegisterInstance()` ręcznie, ale nie jest to zazwyczaj konieczne.
