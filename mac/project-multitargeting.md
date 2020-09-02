---
title: Projekty wieloelementowe
description: Ten dokument zawiera omówienie sposobu konfigurowania projektów wielowymiarowych w programie Visual Studio dla komputerów Mac.
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 12/12/2019
ms.assetid: 2a561af4-f1fe-493e-9a53-aa6d77d15498
ms.openlocfilehash: 3d1372ab5bd08ce164352293ec9d341ca567e3d5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75451441"
---
# <a name="projects-with-multiple-target-frameworks"></a>Projekty z wieloma platformami docelowymi
W Visual Studio dla komputerów Mac można skonfigurować projekt Xamarin lub .NET Core do uruchamiania w jednej z kilku wersji .NET Framework i na jednej z kilku platform systemowych. Można na przykład określić, że projekt ma być uruchamiany na obu .NET Framework 4,6 i .NET Core 3,1. 

Aby uzyskać więcej informacji na temat platform docelowych, zobacz [Platformy docelowe](/dotnet/standard/frameworks).

> [!NOTE] 
> Ten temat ma zastosowanie do Visual Studio dla komputerów Mac. W przypadku programu Visual Studio w systemie Windows Zobacz temat [Omówienie funkcji określania wartości docelowej](/visualstudio/ide/visual-studio-multi-targeting-overview).

## <a name="targeting-multiple-frameworks"></a>Kierowanie wielu struktur

Platformy docelowe są określone w pliku projektu, który można edytować, klikając prawym przyciskiem myszy projekt i wybierając polecenie **narzędzia > Edytuj plik** . W przypadku określenia pojedynczej platformy docelowej należy użyć elementu TargetFramework. Poniższy plik projektu aplikacji konsolowej pokazuje, jak kierować platformą .NET Core 3,0:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Użyj elementu TargetFrameworks w liczbie mnogiej z wieloma platformami docelowymi:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>
```

Dowiedz się więcej o tym, jak dowiedzieć się, jak [kierować wiele platform](/dotnet/standard/frameworks#how-to-specify-target-frameworks).

## <a name="working-with-code-in-a-multi-target-project"></a>Praca z kodem w projekcie wielodostępnym
Gdy edytujesz plik C# w projekcie z wieloma platformami docelowymi, możesz określić platformę docelową, która ma być używana do obsługi środowiska edytora (na przykład wyświetlanie ostrzeżeń w przypadku używania interfejsu API nieobsługiwanego przez platformę). Możesz zmienić platformę docelową, używając selektora **Target Framework** w lewym górnym rogu okna edytora.

![Aby zmienić platformę docelową na początku okna edytora przy użyciu selektora platformy docelowej](media/project-multitargeting-framework-selector.png)

Czasami trzeba wywołać inne interfejsy API w zależności od platformy, w której aplikacja jest ukierunkowana. W tym celu można napisać kod warunkowy, aby skompilować kod dla określonej platformy:

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

Podczas pisania kodu zobaczysz ostrzeżenia w sugestiach autouzupełniania IntelliSense, informując o braku określonych interfejsów API dla dowolnych platform docelowych obsługiwanych przez aplikację.

![Komunikat ostrzegawczy wyświetlany w IntelliSense, interfejs API nie będzie działał dla określonej platformy docelowej. Przykładowy tekst: przestrzeń nazw System. buffers, SharedUtils (Standard 2.0) — niedostępny. Możesz użyć paska nawigacyjnego, aby przełączyć kontekst.](media/project-multitargeting-intellisense-warnings.png)

## <a name="see-also"></a>Zobacz też

- [Omówienie określania celu platformy (Windows)](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [Platformy docelowe w projektach w stylu zestawu SDK](/dotnet/standard/frameworks#how-to-specify-target-frameworks)
