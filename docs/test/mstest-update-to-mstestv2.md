---
title: Aktualizacja do MSTestV2
description: Dowiedz się, jak zaktualizować z MSTestV1 do MSTestV2
ms.custom: SEO-VS-2020
ms.date: 02/26/2021
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.Migrate
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ffe45c444321a7efbaee0a2eb5729850a06c5910
ms.sourcegitcommit: 99b66b0f4ced46ead0b2506a103f974f40cc0076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2021
ms.locfileid: "103366259"
---
# <a name="upgrade-from-mstestv1-to-mstestv2"></a>Uaktualnianie z MSTestV1 do MSTestV2

Możesz uaktualnić projekt testowy, przewołując wersję MSTest, do której odwołuje się element *csproj* z MSTestV1 do MSTestV2. Nie wszystkie funkcje w MSTestV1 zostały przekazane do MSTestV2, więc może być konieczne wprowadzenie pewnych zmian w celu rozwiązania błędów. Zobacz [funkcje MSTestV1, które nie są obsługiwane w programie MSTestV2](#mstestv1-features-that-are-not-supported-in-mstestv2) , aby zrozumieć, jakie funkcje nie będą już działać. Niektóre z nich mogą wymagać usunięcia z testów.

1. Usuń odwołanie do zestawu do Microsoft. VisualStudio. QualityTools. UnitTestFramework z projektu testów jednostkowych.
2. Dodaj odwołania do pakietów NuGet do MSTestV2, w tym [MSTest. TestFramework](https://www.nuget.org/packages/MSTest.TestFramework) i [MSTest. TestAdapter](https://www.nuget.org/packages/MSTest.TestAdapter/) na NuGet.org. Pakiety można zainstalować w konsoli Menedżera pakietów NuGet przy użyciu następujących poleceń:

    ```console
    PM> Install-Package MSTest.TestAdapter -Version 2.1.2
    PM> Install-Package MSTest.TestFramework -Version 2.1.2
    ```

### <a name="old-style-csproj-example"></a>Przykład csproj starego stylu

Przykład *. csproj* określania wartości docelowej MSTestV1:

```xml
<Reference Include="Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=10.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
  <Private>False</Private>
</Reference>
```

Przykład *. csproj* teraz docelowy MSTestV2:

```xml
<Reference Include="Microsoft.VisualStudio.TestPlatform.TestFramework, Version=14.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
  <HintPath>..\packages\MSTest.TestFramework.2.1.2\lib\net45\Microsoft.VisualStudio.TestPlatform.TestFramework.dll</HintPath>
</Reference>
```

> [!NOTE]
> Projekty testowe, które są kodowanymi testami interfejsu użytkownika lub testy obciążenia sieci Web, nie są zgodne z MSTestV2. Te typy projektów są przestarzałe. Przeczytaj więcej na temat [zaniechania kodowanego testu interfejsu użytkownika](https://devblogs.microsoft.com/devops/changes-to-coded-ui-test-in-visual-studio-2019/) i [wycofania testu obciążenia sieci Web](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/).

### <a name="sdk-style-csproj-net-core-and-net-5"></a>CSPROJ w stylu zestawu SDK (.NET Core i .NET 5)

Jeśli *. csproj* to nowszy styl zestawu SDK *. csproj* najprawdopodobniej już korzystasz z MSTestV2. Pakiety NuGet dla [MSTestV2](https://www.nuget.org/packages/MSTest.TestFramework) i [adaptera MSTestV2](https://www.nuget.org/packages/MSTest.TestAdapter/) można znaleźć w pakiecie NuGet.

Przykład:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="16.7.1" />
  <PackageReference Include="MSTest.TestAdapter" Version="2.1.1" />
  <PackageReference Include="MSTest.TestFramework" Version="2.1.1" />
</ItemGroup>
```

## <a name="why-upgrade-to-mstestv2"></a>Dlaczego warto przeprowadzić uaktualnienie do MSTestV2?

W 2016 został opublikowany następny krok w rozwijającej się strukturze MSTest z MSTestV2. Więcej informacji na temat tej zmiany znajdziesz w [blogu](https://devblogs.microsoft.com/devops/taking-the-mstest-framework-forward-with-mstest-v2/)ogłoszenie.

* Usługa MSTestV2 jest łatwiejsza do pozyskania i aktualizowania, ponieważ jest dostarczana jako [pakiet NuGet](https://www.nuget.org/packages/MSTest.TestFramework/).
* MSTestV2 to [Open Source](https://github.com/microsoft/testfx).
* Jednolita obsługa platformy aplikacji — MSTestV2 to zbieżna implementacja, która oferuje jednolitą obsługę platformy aplikacji w .NET Framework, .NET Core, ASP.NET Core i platformy UWP. [Przeczytaj więcej](https://blogs.msdn.microsoft.com/devops/2016/09/01/announcing-mstest-v2-framework-support-for-net-core-1-0-rtm/).
* Implementacja jest w pełni międzyplatformowa (Windows, Linux, Mac). [Przeczytaj więcej](https://blogs.msdn.microsoft.com/devops/2017/04/05/mstest-v2-is-open-source/).
* MSTestV2 obsługuje .NET Framework 4.5.0 i nowszych, .NET Core 1,0 i nowszych (Aplikacje uniwersalne systemu Windows 10 +), ASP.NET Core 1,0 i nowsze oraz .NET 5 i nowszych.
* Zapewnia jednolity mechanizm rozszerzalności dla użytkowników końcowych. [Przeczytaj więcej](https://blogs.msdn.microsoft.com/devops/2017/07/18/extending-mstest-v2/).
* Zapewnia jednolitą `DataRow` obsługę wszystkich projektów testowych opartych na MSTest. [Przeczytaj więcej](https://blogs.msdn.microsoft.com/devops/2017/02/25/mstest-v2-now-and-ahead/).
* Włącza umieszczenie `TestCategory` atrybutu na poziomie klasy lub zestawu. [Przeczytaj więcej](https://blogs.msdn.microsoft.com/devops/2017/02/25/mstest-v2-now-and-ahead/).
* Metody testowe z klas bazowych zdefiniowanych w innym zestawie są teraz odnajdywane i uruchamiane z klasy testów pochodnych. Ta zmiana powoduje spójne zachowanie przy użyciu pochodnych typów klas testów. Jeśli takie zachowanie nie jest wymagane ze względu na zgodność, można je zmienić z powrotem przy użyciu następujących ustawień uruchamiania:

    ```xml
    <RunSettings>    
    <MSTest> 
      <EnableBaseClassTestMethodsFromOtherAssemblies>false</EnableBaseClassTestMethodsFromOtherAssemblies> 
    </MSTest> 
    </RunSettings>
    ```

* Zapewnia precyzyjną kontrolę nad równoległym wykonywaniem przez [równoległe wykonywanie](https://github.com/Microsoft/testfx-docs/blob/master/RFCs/004-In-Assembly-Parallel-Execution.md) testów. Umożliwia to równoległe uruchamianie testów wewnątrz zestawu.
* `TestCleanup`Metoda na `TestClass` jest wywoływana, nawet jeśli jej odpowiadająca `TestInitialize` Metoda nie powiedzie się. [Szczegóły problemu](https://github.com/Microsoft/testfx/issues/250).
* Czas `AssemblyInitialize` trwania przez i `ClassInitialize` nie jest liczony do czasu testu. Ta zmiana ogranicza wpływ na limit czasu testu.
* Testy, które nie są możliwy do uruchomienia, można skonfigurować tak, aby były oznaczone jako nieudane przez `MapNotRunnableToFailed` tag, który jest częścią węzła karty w `.runsettings` pliku.

    ```xml
    <RunSettings>    
    <MSTest> 
      <MapNotRunnableToFailed>true</MapNotRunnableToFailed> 
    </MSTest> 
    </RunSettings>
    ```

## <a name="mstestv1-features-that-are-not-supported-in-mstestv2"></a>Funkcje MSTestV1, które nie są obsługiwane w MSTestV2

*   Testy nie mogą zostać uwzględnione w "uporządkowanym teście".
*   Adapter nie obsługuje konfigurowania za pośrednictwem pliku *. testsettings* . Użyj nowego pliku [ *. runsettings*](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) do konfiguracji przebiegu testu.
*   Adapter nie obsługuje list testów określonych jako plik *. vsmdi* .
*   Typy "projekt kodowanego testu interfejsu użytkownika" i "projekt testów wydajności i obciążenia sieci Web" nie są obsługiwane. Przeczytaj więcej na temat [zaniechania kodowanego testu interfejsu użytkownika](https://devblogs.microsoft.com/devops/changes-to-coded-ui-test-in-visual-studio-2019/) i [wycofania testu obciążenia sieci Web](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/).

## <a name="see-also"></a>Zobacz też

- [Skonfiguruj przebiegi testowe z `.runsettings`](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Testowanie jednostkowe kodu](../test/unit-test-your-code.md)
- [Debugowanie testów jednostkowych za pomocą narzędzia Eksplorator testów](../test/debug-unit-tests-with-test-explorer.md)
