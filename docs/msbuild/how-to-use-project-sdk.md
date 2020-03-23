---
title: 'Jak: Odwoływanie się do sdk projektu MSBuild | Dokumenty firmy Microsoft'
ms.date: 01/25/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, SDKs, SDK
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 74ccc29417cdee7a9f93c39509c0f7d06a5c72ff
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "76826474"
---
# <a name="how-to-use-msbuild-project-sdks"></a>Jak: Korzystanie z sdk projektów MSBuild

Program MSBuild 15.0 wprowadził koncepcję "zestawu SDK projektu", która upraszcza korzystanie z zestawów programistycznych, które wymagają importowania właściwości i obiektów docelowych.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```

Podczas oceny projektu MSBuild dodaje niejawne importy u góry i u dołu pliku projektu:

```xml
<Project>
    <!-- Implicit top import -->
    <Import Project="Sdk.props" Sdk="Microsoft.NET.Sdk" />

    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>

    <!-- Implicit bottom import -->
    <Import Project="Sdk.targets" Sdk="Microsoft.NET.Sdk" />
</Project>
```

## <a name="reference-a-project-sdk"></a>Odwoływanie się do sdk projektu

Istnieją trzy sposoby odwoływania się do sdk projektu:

- Użyj `Sdk` atrybutu w `<Project/>` elemencie:

    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```

    Niejawny import jest dodawany do górnej i dolnej części projektu, jak wspomniano wcześniej.
    
    Aby określić określoną wersję sdk, dołącz `Sdk` go do atrybutu:

    ```xml
    <Project Sdk="My.Custom.Sdk/1.2.3">
        ...
    </Project>
    ```

    > [!NOTE]
    > Jest to obecnie jedyny obsługiwany sposób odwoływania się do sdk projektu w programie Visual Studio dla komputerów Mac.

- Użyj elementu najwyższego poziomu: `<Sdk/>`

    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```

   Niejawny import jest dodawany do górnej i dolnej części projektu, jak wspomniano wcześniej.
   
   Atrybut `Version` nie jest wymagany.

- Użyj `<Import/>` elementu w dowolnym miejscu w projekcie:

    ```xml
    <Project>
        <PropertyGroup>
            <MyProperty>Value</MyProperty>
        </PropertyGroup>
        <Import Project="Sdk.props" Sdk="My.Custom.Sdk" />
        ...
        <Import Project="Sdk.targets" Sdk="My.Custom.Sdk" />
    </Project>
   ```

   Jawnie włączenie importu w projekcie umożliwia pełną kontrolę nad zamówieniem.

   Podczas korzystania `<Import/>` z elementu, można `Version` określić atrybut opcjonalny, jak również. Na przykład można `<Import Project="Sdk.props" Sdk="My.Custom.Sdk" Version="1.2.3" />`określić .

## <a name="how-project-sdks-are-resolved"></a>Jak rozwiązywane są rozwiązania dotyczące skusi SDK projektów

Podczas oceny importu MSBuild dynamicznie rozpoznaje ścieżkę do sdk projektu na podstawie nazwy i wersji, które zostały określone.  MSBuild ma również listę zarejestrowanych programów rozpoznawania nazw SDK, które są wtyczkami, które lokalizują sdk projektu na komputerze. Wtyczki te obejmują:

- Program rozpoznawania nazw oparty na nuget, który wysyła kwerendy skonfigurowane źródła danych pakietu dla pakietów NuGet, które pasują do identyfikatora i wersji zestawu SDK, który został określony.

   Ten program rozpoznawania nazw jest aktywny tylko wtedy, gdy określono wersję opcjonalną. Może być używany dla dowolnego niestandardowego sdk projektu.
   
- Program rozpoznawcza interfejsu wiersza polecenia .NET, który rozpoznaje pakiety SDK zainstalowane z [programem .NET CLI](/dotnet/core/tools/).

   Ten program rozpoznawania nazw lokalizuje zestaw `Microsoft.NET.Sdk` `Microsoft.NET.Sdk.Web` sdk projektu, takich jak i które są częścią produktu.
   
- Domyślny program rozpoznawania nazw, który rozpoznaje sks, które zostały zainstalowane z MSBuild.

Program rozpoznawania nazw SDK oparty na nuget obsługuje określanie wersji w pliku [global.json,](/dotnet/core/tools/global-json) który umożliwia sterowanie wersją SDK projektu w jednym miejscu, a nie w każdym projekcie:

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```

Tylko jedna wersja każdego sdk projektu może służyć podczas kompilacji. Jeśli odwołujesz się do dwóch różnych wersji tego samego sdk projektu, MSBuild emituje ostrzeżenie. Zaleca **się,** aby nie określać wersji w projektach, jeśli wersja jest określona w pliku *global.json.*

## <a name="see-also"></a>Zobacz też

- [Koncepcje MSBuild](../msbuild/msbuild-concepts.md)
- [Dostosowywanie kompilacji](../msbuild/customize-your-build.md)
- [Pakiety, metadane i struktury](/dotnet/core/packages)
- [Dodatki do formatu csproj dla .NET Core](/dotnet/core/tools/csproj)
