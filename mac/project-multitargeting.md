---
title: Projekty wielotargowe
description: Ten dokument zawiera omówienie sposobu konfigurowania projektów wielokierunkowych w programie Visual Studio dla komputerów Mac.
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 12/12/2019
ms.assetid: 2a561af4-f1fe-493e-9a53-aa6d77d15498
ms.openlocfilehash: 3d1372ab5bd08ce164352293ec9d341ca567e3d5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451441"
---
# <a name="projects-with-multiple-target-frameworks"></a>Projekty z wieloma strukturami docelowymi
W programie Visual Studio dla komputerów Mac można skonfigurować projekt platformy Xamarin lub .NET Core do uruchamiania w dowolnej z kilku wersji programu .NET Framework i na dowolnej z kilku platform systemowych. Na przykład można kierować projekt do uruchomienia zarówno w programie .NET Framework 4.6 i .NET Core 3.1. 

Aby uzyskać więcej informacji na temat struktur docelowych, zobacz [struktury docelowe](/dotnet/standard/frameworks).

> [!NOTE] 
> W tym temacie stosuje się do programu Visual Studio dla komputerów Mac. W przypadku programu Visual Studio w systemie Windows zobacz [omówienie kierowania na ramy](/visualstudio/ide/visual-studio-multi-targeting-overview).

## <a name="targeting-multiple-frameworks"></a>Kierowanie na wiele struktur

Struktury docelowe są określone w pliku projektu, który można edytować, klikając prawym przyciskiem myszy na projekcie i wybierając **polecenie Narzędzia > Edytuj plik.** Po określeniu jednej struktury docelowej należy użyć elementu TargetFramework. Następujący plik projektu aplikacji konsoli pokazuje, jak kierować .NET Core 3.0:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Użyj elementu wielowarstwowego TargetFrameworks z wieloma strukturami docelowymi:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>
```

Dowiedz się więcej o tym, jak [kierować reklamy](/dotnet/standard/frameworks#how-to-specify-target-frameworks)na wiele struktur .

## <a name="working-with-code-in-a-multi-target-project"></a>Praca z kodem w projekcie wielocelowym
Podczas edytowania pliku Języka C# w projekcie z wieloma platformami docelowymi, można określić, która struktura docelowa ma być używana do kierowania edytorem (na przykład wyświetlanie ostrzeżeń, jeśli używasz interfejsu API nie obsługiwane przez tę platformę). Platformę docelową można zmienić za pomocą selektora **struktury docelowej** w lewym górnym rogu okna edytora.

![Używanie selektora struktury docelowej do zmiany struktury docelowej, znajdującej się w górnej części okna edytora](media/project-multitargeting-framework-selector.png)

Czasami trzeba wywołać różne interfejsy API w zależności od platformy aplikacji jest kierowana. Aby to zrobić, można napisać kod warunkowy do kompilacji kodu dla określonej platformy:

```C#
public class MyClass
{
    static void Main()
    {
#if NET40
        Console.WriteLine("Target framework: .NET Framework 4.0");
#elif NET45  
        Console.WriteLine("Target framework: .NET Framework 4.5");
#else
        Console.WriteLine("Target framework: .NET Standard 1.4");
#endif
    }
}
```

Podczas pisania kodu zostaną wyświetlone ostrzeżenia w sugestiach automatycznego uzupełniania IntelliSense, informując o tym, czy brakuje określonych interfejsów API dla dowolnej platformy docelowej, którą obsługuje aplikacja.

![Komunikat ostrzegawczy wyświetlany w intellisense, interfejs API nie będzie działać dla określonej struktury docelowej. Przykładowy tekst: namespace System.Buffers, SharedUtils (netstandard2.0) - Niedostępne. Za pomocą paska nawigacyjnego można przełączać kontekst.](media/project-multitargeting-intellisense-warnings.png)

## <a name="see-also"></a>Zobacz też

- [Omówienie kierowania na platformę (Windows)](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [Struktury docelowe w projektach w stylu SDK](/dotnet/standard/frameworks#how-to-specify-target-frameworks)
