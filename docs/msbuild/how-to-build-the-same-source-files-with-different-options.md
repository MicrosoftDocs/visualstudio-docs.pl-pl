---
title: 'Instrukcje: Kompilacja tych samych plików źródłowych przy użyciu różnych opcji | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source files, building with different options
- MSBuild, properties
- project properties, modifying
- Hello World example [Visual Studio]
ms.assetid: d14f1212-ddd9-434f-b138-f840011b0fb2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8cb678a05b9301982b4842d272c3032cafa46a87
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62977336"
---
# <a name="how-to-build-the-same-source-files-with-different-options"></a>Instrukcje: Kompilacja tych samych plików źródłowych przy użyciu różnych opcji
Podczas kompilowania projektów kompilacji są często te same składniki z opcjami różne kompilacje. Na przykład można utworzyć kompilacji debugowania przy użyciu informacji o symbolach lub kompilację wydania z nie informacji o symbolach, ale z włączonymi optymalizacjami. Możesz też skompilować projektu do uruchamiania na danej platformie, takich jak x86 lub [!INCLUDE[vcprx64](../extensibility/internals/includes/vcprx64_md.md)]. W takich przypadkach większości opcji kompilacji pozostają takie same; tylko kilka opcji zostały zmienione, aby kontrolować konfigurację kompilacji. Za pomocą [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], użyj właściwości i warunki do tworzenia innych konfiguracji kompilacji.

## <a name="use-properties-to-modify-projects"></a>Użyj właściwości, aby zmodyfikować projektów
`Property` Element definiuje zmienną, która odwołuje się do pliku projektu, takie jak lokalizacja katalogu tymczasowego, lub do ustawiania wartości właściwości, które są używane w kompilacji, kilka konfiguracji, takie jak kompilacja do debugowania i wydania. Aby uzyskać więcej informacji o właściwościach, zobacz [właściwości programu MSBuild](../msbuild/msbuild-properties.md).

Aby zmienić konfigurację kompilacji, bez konieczności zmiany w pliku projektu, można użyć właściwości. `Condition` Atrybutu `Property` elementu i `PropertyGroup` elementu pozwala na zmianę wartości właściwości. Aby uzyskać więcej informacji na temat [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] warunkach, zobacz [warunki](../msbuild/msbuild-conditions.md).

#### <a name="to-set-a-group-of-properties-based-on-another-property"></a>Aby ustawić grupę na podstawie właściwości innej właściwości

- Użyj `Condition` atrybutu w `PropertyGroup` podobny do następującego elementu:

  ```xml
  <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">
      <DebugType>full</DebugType>
      <Optimize>no</Optimize>
  </PropertyGroup>
  ```

#### <a name="to-define-a-property-based-on-another-property"></a>Aby zdefiniować właściwość, na podstawie innej właściwości

- Użyj `Condition` atrybutu w `Property` podobny do następującego elementu:

  ```xml
  <DebugType Condition="'$(Flavor)'=='DEBUG'">full</DebugType>
  ```

## <a name="specify-properties-on-the-command-line"></a>Określ właściwości w wierszu polecenia
Napisana pliku projektu, aby akceptował wiele konfiguracji musisz mieć możliwość zmiany te konfiguracje przy każdej kompilacji projektu. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zapewnia tę możliwość, umożliwiając właściwości można określić w wierszu polecenia za pomocą **— właściwość** lub **-p** przełącznika.

#### <a name="to-set-a-project-property-at-the-command-line"></a>Aby ustawić właściwości projektu w wierszu polecenia

- Użyj **— właściwość** przełącznik z właściwości i wartości właściwości. Na przykład:

  ```cmd
  msbuild file.proj -property:Flavor=Debug
  ```

  lub

  ```cmd
  Msbuild file.proj -p:Flavor=Debug
  ```

#### <a name="to-specify-more-than-one-project-property-at-the-command-line"></a>Aby określić więcej niż jednej właściwości projektu w wierszu polecenia

- Użyj **— właściwość** lub **-p** przełącznika wiele razy przy użyciu właściwości i wartości właściwości lub użyć jednego **— właściwość** lub **-p** przełącznika i wiele właściwości należy oddzielić średnikami (;). Na przykład:

  ```cmd
  msbuild file.proj -p:Flavor=Debug;Platform=x86
  ```

  lub

  ```cmd
  msbuild file.proj -p:Flavor=Debug -p:Platform=x86
  ```

  Zmienne środowiskowe są także traktowane jako właściwości i są automatycznie włączone przez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Aby uzyskać więcej informacji na temat używania zmiennych środowiskowych, zobacz [jak: Użycie zmiennych środowiskowych w kompilacji](../msbuild/how-to-use-environment-variables-in-a-build.md).

  Wartość właściwości, która jest określona w wierszu polecenia mają pierwszeństwo przed wszystkie wartości, który jest skonfigurowany dla tej samej właściwości w pliku projektu, a wartość w pliku projektu mają pierwszeństwo przed wartość w zmiennej środowiskowej.

  To zachowanie można zmienić za pomocą `TreatAsLocalProperty` atrybutów w znaczniku projektu. Dla nazwy właściwości, które są wyświetlane z tego atrybutu wartość właściwości, która jest określona w wierszu polecenia nie pierwszeństwo przed wartością w pliku projektu. Przykład można znaleźć w dalszej części tego tematu.

## <a name="example"></a>Przykład
Poniższy przykład kodu, projekt "Hello World" zawiera dwie nowe grupy właściwości, które mogą służyć do tworzenia kompilacji debugowania i kompilacji wydania.

Tworzenie wersji debugowania tego projektu, należy wpisać:

```cmd
msbuild consolehwcs1.proj -p:flavor=debug
```

Aby skompilować wersji detalicznej tego projektu, należy wpisać:

```cmd
msbuild consolehwcs1.proj -p:flavor=retail
```

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <!-- Sets the default flavor of an environment variable called
    Flavor is not set or specified on the command line -->
    <PropertyGroup>
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>
    </PropertyGroup>

    <!-- Define the DEBUG settings -->
    <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">
        <DebugType>full</DebugType>
        <Optimize>no</Optimize>
    </PropertyGroup>

    <!-- Define the RETAIL settings -->
    <PropertyGroup Condition="'$(Flavor)'=='RETAIL'">
        <DebugType>pdbonly</DebugType>
        <Optimize>yes</Optimize>
    </PropertyGroup>

    <!-- Set the application name as a property -->
    <PropertyGroup>
        <appname>HelloWorldCS</appname>
    </PropertyGroup>

    <!-- Specify the inputs by type and file name -->
    <ItemGroup>
        <CSFile Include = "consolehwcs1.cs"/>
    </ItemGroup>

    <Target Name = "Compile">
        <!-- Run the Visual C# compilation using input files
        of type CSFile -->
        <CSC  Sources = "@(CSFile)"
            DebugType="$(DebugType)"
            Optimize="$(Optimize)"
            OutputAssembly="$(appname).exe" >

            <!-- Set the OutputAssembly attribute of the CSC
            task to the name of the executable file that is
            created -->
            <Output TaskParameter="OutputAssembly"
                ItemName = "EXEFile" />
        </CSC>
        <!-- Log the file name of the output file -->
        <Message Text="The output file is @(EXEFile)"/>
    </Target>
</Project>
```

## <a name="example"></a>Przykład
Poniższy przykład ilustruje sposób używania `TreatAsLocalProperty` atrybutu. `Color` Właściwość ma wartość `Blue` w pliku projektu i `Green` w wierszu polecenia. Za pomocą `TreatAsLocalProperty="Color"` w znaczniku projektu, a właściwość wiersza polecenia (`Green`) nie zastępuje właściwość, która jest zdefiniowana w pliku projektu (`Blue`).

Aby skompilować projekt, wprowadź następujące polecenie:

```cmd
msbuild colortest.proj -t:go -property:Color=Green
```

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003"
ToolsVersion="4.0" TreatAsLocalProperty="Color">

    <PropertyGroup>
        <Color>Blue</Color>
    </PropertyGroup>

    <Target Name="go">
        <Message Text="Color: $(Color)" />
    </Target>
</Project>

<!--
  Output with TreatAsLocalProperty="Color" in project tag:
     Color: Blue

  Output without TreatAsLocalProperty="Color" in project tag:
     Color: Green
-->
```

## <a name="see-also"></a>Zobacz także
- [MSBuild](../msbuild/msbuild.md)
- [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)
- [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)
- [Project — element (MSBuild)](../msbuild/project-element-msbuild.md)
