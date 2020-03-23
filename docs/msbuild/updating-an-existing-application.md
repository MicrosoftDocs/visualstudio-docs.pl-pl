---
title: Aktualizowanie istniejącej aplikacji do MSBuild 15 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d4e7d84768307964b495e8c5e97e7731b0622a1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75597142"
---
# <a name="update-an-existing-application-for-msbuild-15"></a>Aktualizowanie istniejącej aplikacji dla usługi MSBuild 15

W wersjach MSBuild przed 15.0 MSBuild został załadowany z globalnej pamięci podręcznej zestawu (GAC) i rozszerzenia MSBuild zostały zainstalowane w rejestrze. Dzięki temu wszystkie aplikacje używały tej samej wersji programu MSBuild i miały dostęp do tych samych zestawów narzędzi, ale zapobiegały instalacjom obok siebie w różnych wersjach programu Visual Studio.

Aby obsługiwać szybszą, mniejszą i side-by-side instalacji, Visual Studio 2017 i nowsze wersje nie umieszczają już MSBuild w pliku GAC lub modyfikuje rejestr. Niestety oznacza to, że aplikacje, które chcą używać interfejsu API MSBuild do oceny lub tworzenia projektów nie mogą niejawnie polegać na instalacji programu Visual Studio.

## <a name="use-msbuild-from-visual-studio"></a>Używanie usługi MSBuild z programu Visual Studio

Aby upewnić się, że kompilacje programowe z kompilacji dopasowania aplikacji wykonane w programie Visual Studio lub *MSBuild.exe*, załadować zestawy MSBuild z programu Visual Studio i używać zestawów SDK dostępnych w programie Visual Studio. Pakiet Microsoft.Build.Locator NuGet usprawnia ten proces.

## <a name="use-microsoftbuildlocator"></a>Użyj microsoft.build.locator

Jeśli ponownie rozdzielasz plik *Microsoft.Build.Locator.dll* z aplikacją, nie trzeba będzie rozpowszechniać innych zestawów MSBuild.

Aktualizowanie projektu w celu użycia MSBuild 15 i interfejsu API lokalizatora wymaga kilku zmian w projekcie, opisanych poniżej. Aby zobaczyć przykład zmian wymaganych do aktualizacji projektu, zobacz [zatwierdzenia wprowadzone do przykładowego projektu w repozytorium MSBuildLocator](https://github.com/Microsoft/MSBuildLocator/commits/example-updating-to-msbuild-15).

### <a name="change-msbuild-references"></a>Zmienianie odwołań do budynków MSBuild

Aby upewnić się, że MSBuild ładuje się z centralnej lokalizacji, nie należy rozpowszechniać jego zestawów z aplikacją.

Mechanizm zmiany projektu, aby uniknąć ładowania MSBuild z centralnej lokalizacji zależy od sposobu odwoływania się do MSBuild.

#### <a name="use-nuget-packages-preferred"></a>Użyj pakietów NuGet (preferowane)

W tych instrukcjach założono, że używasz [odwołania NuGet w stylu PackageReference.](/nuget/consume-packages/package-references-in-project-files)

Zmień pliki projektu, aby odwoływać się do zestawów MSBuild z ich pakietów NuGet. Określ, aby poinformować `ExcludeAssets=runtime` NuGet, że zestawy są potrzebne tylko w czasie kompilacji i nie powinny być kopiowane do katalogu wyjściowego.

Wersja główna i pomocnicza pakietów MSBuild musi być mniejsza lub równa minimalnej wersji programu Visual Studio, którą chcesz obsługiwać. Na przykład jeśli chcesz obsługiwać program Visual Studio 2017 `15.1.548`i nowsze wersje, odwołuje się do wersji pakietu .

Można na przykład użyć tego kodu XML:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Build" Version="15.1.548" ExcludeAssets="runtime" />
  <PackageReference Include="Microsoft.Build.Utilities.Core" Version="15.1.548" ExcludeAssets="runtime" />
</ItemGroup>
```

#### <a name="use-extension-assemblies"></a>Używanie zestawów rozszerzeń

Jeśli nie można użyć pakietów NuGet, można odwoływać się do zestawów MSBuild, które są dystrybuowane za pomocą programu Visual Studio. Jeśli odwołujesz się bezpośrednio do usługi MSBuild, upewnij się, że `Copy Local` nie `False`zostanie skopiowany do katalogu wyjściowego, ustawiając na . W pliku projektu to ustawienie będzie wyglądać następująco:

```xml
    <Reference Include="Microsoft.Build, Version=15.1.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
      <Private>False</Private>
    </Reference>
```

#### <a name="binding-redirects"></a>Przekierowania powiązania

Odwołaj się do pakietu Microsoft.Build.Locator, aby upewnić się, że aplikacja automatycznie używa wymaganych przekierowań powiązania do wersji 15.1.0.0. Powiązanie przekierowuje do tej wersji obsługuje zarówno MSBuild 15 i MSBuild 16.

### <a name="ensure-output-is-clean"></a>Upewnij się, że wyjście jest czyste

Skompiluj projekt i sprawdź katalog danych wyjściowych, aby upewnić się, że nie zawiera on żadnych programów *Microsoft.Build.\*. dll* zestawy inne niż *Microsoft.Build.Locator.dll*, dodane w następnym kroku.

### <a name="add-package-reference-for-microsoftbuildlocator"></a>Dodaj odwołanie do pakietu dla microsoft.build.locator

Dodaj odwołanie do pakietu NuGet dla [microsoft.build.locator](https://www.nuget.org/packages/Microsoft.Build.Locator/).

```xml
    <PackageReference Include="Microsoft.Build.Locator">
      <Version>1.1.2</Version>
    </PackageReference>
```

Nie należy `ExcludeAssets=runtime` określać pakietu Microsoft.Build.Locator.

### <a name="register-instance-before-calling-msbuild"></a>Zarejestruj wystąpienie przed wywołaniem MSBuild

Dodaj wywołanie interfejsu API lokalizatora przed wywołaniem dowolnej metody korzystającej z usługi MSBuild.

Najprostszym sposobem dodania wywołania do interfejsu API lokalizatora jest dodanie

```csharp
MSBuildLocator.RegisterDefaults();
```

w kodzie startowym aplikacji.

Jeśli chcesz bardziej ziarniste kontroli nad ładowaniem MSBuild, można `MSBuildLocator.QueryVisualStudioInstances()` wybrać wynik `MSBuildLocator.RegisterInstance()` przekazać ręcznie, ale zazwyczaj nie jest to potrzebne.
