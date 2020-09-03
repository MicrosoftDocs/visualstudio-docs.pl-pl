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
ms.openlocfilehash: 74ccc29417cdee7a9f93c39509c0f7d06a5c72ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "76826474"
---
# <a name="how-to-use-msbuild-project-sdks"></a>Instrukcje: korzystanie z zestawów SDK projektu MSBuild

Program MSBuild 15,0 wprowadził koncepcję "zestawu SDK projektu", która upraszcza korzystanie z zestawów deweloperskich oprogramowania, które wymagają zaimportowania właściwości i obiektów docelowych.

```xml
<Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
        <TargetFramework>net46</TargetFramework>
    </PropertyGroup>
</Project>
```

Podczas obliczania projektu, MSBuild dodaje niejawne Importy u góry i u dołu pliku projektu:

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

- Użyj `Sdk` atrybutu dla `<Project/>` elementu:

    ```xml
    <Project Sdk="My.Custom.Sdk">
        ...
    </Project>
    ```

    Niejawny import jest dodawany do góry i u dołu projektu, jak opisano wcześniej.
    
    Aby określić określoną wersję zestawu SDK, Dołącz ją do `Sdk` atrybutu:

    ```xml
    <Project Sdk="My.Custom.Sdk/1.2.3">
        ...
    </Project>
    ```

    > [!NOTE]
    > Obecnie jedynym obsługiwanym sposobem odwoływania się do zestawu SDK projektu w Visual Studio dla komputerów Mac.

- Użyj elementu najwyższego poziomu `<Sdk/>` :

    ```xml
    <Project>
        <Sdk Name="My.Custom.Sdk" Version="1.2.3" />
        ...
    </Project>
   ```

   Niejawny import jest dodawany do góry i u dołu projektu, jak opisano wcześniej.
   
   Ten `Version` atrybut nie jest wymagany.

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

   Jawne uwzględnienie Importy w projekcie umożliwia pełną kontrolę nad kolejnością.

   W przypadku używania `<Import/>` elementu można również określić opcjonalny `Version` atrybut. Na przykład można określić `<Import Project="Sdk.props" Sdk="My.Custom.Sdk" Version="1.2.3" />` .

## <a name="how-project-sdks-are-resolved"></a>Jak są rozwiązywane zestawy SDK projektu

Podczas oceny importu program MSBuild dynamicznie rozpoznaje ścieżkę do zestawu SDK projektu na podstawie określonej nazwy i wersji.  Program MSBuild zawiera również listę zarejestrowanych narzędzi do rozwiązywania problemów z zestawem SDK, które są wtyczkami do lokalizowania zestawów SDK projektu na komputerze. Te wtyczki obejmują:

- Mechanizm rozwiązywania konfliktów oparty na pakiecie NuGet, który wysyła zapytanie do skonfigurowanych kanałów informacyjnych pakietu dla pakietów NuGet zgodnych z IDENTYFIKATORem i wersją określonego zestawu SDK.

   Ten mechanizm rozwiązywania konfliktów jest aktywny tylko w przypadku wybrania wersji opcjonalnej. Może być używana dla dowolnego niestandardowego zestawu SDK projektu.
   
- Program rozpoznawania interfejsu wiersza polecenia platformy .NET, który rozwiązuje zestawy SDK instalowane z [interfejsem wiersza polecenia platformy .NET](/dotnet/core/tools/).

   Ten program rozpoznawania nazw lokalizuje zestawy projektów, takie jak `Microsoft.NET.Sdk` i `Microsoft.NET.Sdk.Web` , które są częścią produktu.
   
- Domyślny program rozpoznawania nazw, który rozwiązuje zestawy SDK, które zostały zainstalowane z programem MSBuild.

Mechanizm rozwiązywania konfliktów oparty na pakiecie NuGet obsługuje określanie wersji w [global.js](/dotnet/core/tools/global-json) pliku, co umożliwia kontrolowanie wersji zestawu SDK projektu w jednym miejscu, a nie w każdym projekcie:

```json
{
    "msbuild-sdks": {
        "My.Custom.Sdk": "5.0.0",
        "My.Other.Sdk": "1.0.0-beta"
    }
}
```

Podczas kompilacji można używać tylko jednej wersji zestawu SDK projektu. Jeśli odwołujesz się do dwóch różnych wersji tego samego zestawu SDK projektu, MSBuild emituje ostrzeżenie. Zaleca się, aby **nie** określać wersji w projektach, jeśli w pliku *global.js* jest określona wersja.

## <a name="see-also"></a>Zobacz też

- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
- [Dostosowywanie kompilacji](../msbuild/customize-your-build.md)
- [Pakiety, metadane i struktury](/dotnet/core/packages)
- [Dodatki do formatu csproj dla platformy .NET Core](/dotnet/core/tools/csproj)
