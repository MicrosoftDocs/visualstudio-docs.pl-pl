---
title: 'Instrukcje: odwoływanie się do zestawu SDK projektu MSBuild | Microsoft Docs'
ms.date: 01/25/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, SDKs, SDK
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d40e437763ba3eb75daa80a3a1bbf55ba9d896c9
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75574460"
---
# <a name="how-to-use-msbuild-project-sdks"></a>Instrukcje: korzystanie z zestawów SDK projektu MSBuild

[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 15,0 wprowadza koncepcję "zestawu SDK projektu", która upraszcza korzystanie z zestawów deweloperskich oprogramowania, które wymagają zaimportowania właściwości i obiektów docelowych.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```

Podczas obliczania projektu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] dodaje niejawne Importy u góry i u dołu projektu:

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

## <a name="reference-a-project-sdk"></a>Odwoływanie się do zestawu SDK projektu

 Istnieją trzy sposoby odwoływania się do zestawu SDK projektu:

1. Użyj `Sdk` atrybutu dla elementu `<Project/>`:

    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```

    Niejawny import jest dodawany do góry i u dołu projektu, jak wspomniano powyżej.
    
    Aby określić określoną wersję zestawu SDK, możesz dołączyć go do `Sdk` atrybutu:

    ```xml
    <Project Sdk="My.Custom.Sdk/1.2.3">
        ...
    </Project>
    ```

    > [!NOTE]
    > Obecnie jedynym obsługiwanym sposobem odwoływania się do zestawu SDK projektu w Visual Studio dla komputerów Mac.

2. Użyj `<Sdk/>` elementu najwyższego poziomu:

    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```

   Niejawny import jest dodawany do góry i u dołu projektu, jak wspomniano powyżej.  Atrybut `Version` nie jest wymagany.

3. Użyj elementu `<Import/>` w dowolnym miejscu w projekcie:

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

   Jawne uwzględnienie Importy w projekcie umożliwia pełną kontrolę nad kolejnością.

   Korzystając z elementu `<Import/>`, można również określić opcjonalny atrybut `Version`.  Na przykład można określić `<Import Project="Sdk.props" Sdk="My.Custom.Sdk" Version="1.2.3" />`.

## <a name="how-project-sdks-are-resolved"></a>Jak są rozwiązywane zestawy SDK projektu

Podczas oceny importu [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] dynamicznie rozpoznaje ścieżkę do zestawu SDK projektu na podstawie określonej nazwy i wersji.  [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ma także listę zarejestrowanych resolverów zestawu SDK, które są wtyczkami, które lokalizują zestawy SDK projektu na komputerze.  Te wtyczki obejmują:

1. Mechanizm rozwiązywania konfliktów oparty na pakiecie NuGet, który wysyła zapytanie do skonfigurowanych kanałów informacyjnych pakietu dla pakietów NuGet zgodnych z IDENTYFIKATORem i wersją określonego zestawu SDK.<br/>
   Ten program rozpoznawania nazw jest aktywny tylko wtedy, gdy określono opcjonalną wersję i można jej użyć dla dowolnego niestandardowego zestawu SDK projektu.
2. Program rozpoznawania interfejsu wiersza polecenia platformy .NET, który rozwiązuje zestawy SDK instalowane z interfejsem wiersza polecenia platformy .NET.<br/>
   Ten mechanizm rozwiązywania konfliktów lokalizuje zestawy SDK projektu, takie jak `Microsoft.NET.Sdk` i `Microsoft.NET.Sdk.Web`, które są częścią produktu.
3. Domyślny program rozpoznawania nazw, który rozwiązuje zestawy SDK, które zostały zainstalowane z programem MSBuild.

Program rozpoznawania SDK oparty na pakiecie NuGet obsługuje określanie wersji w pliku [Global. JSON](/dotnet/core/tools/global-json) , który umożliwia kontrolowanie wersji zestawu SDK projektu w jednym miejscu, a nie w każdym projekcie:

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```

Podczas kompilacji można używać tylko jednej wersji zestawu SDK projektu.  Jeśli odwołujesz się do dwóch różnych wersji tego samego zestawu SDK projektu, program MSBuild wyemituje ostrzeżenie.  Zaleca się, aby **nie** określać wersji w projektach, jeśli w pliku *Global. JSON*została określona wersja.

## <a name="see-also"></a>Zobacz także

- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
- [Dostosowywanie kompilacji](../msbuild/customize-your-build.md)
- [Pakiety, metadane i struktury](/dotnet/core/packages)
- [Dodatki do formatu csproj dla platformy .NET Core](/dotnet/core/tools/csproj)
