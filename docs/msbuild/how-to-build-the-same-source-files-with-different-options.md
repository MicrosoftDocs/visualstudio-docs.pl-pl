---
title: Kompilacja tych samych plików źródłowych przy użyciu różnych opcji
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source files, building with different options
- MSBuild, properties
- project properties, modifying
- Hello World example [Visual Studio]
ms.assetid: d14f1212-ddd9-434f-b138-f840011b0fb2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23e76145df0fdf3f4cc3a3dfa8e14c6826b0dbdf
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037598"
---
# <a name="how-to-build-the-same-source-files-with-different-options"></a>Instrukcje: kompilowanie tych samych plików źródłowych przy użyciu różnych opcji

Podczas kompilowania projektów często kompilujesz te same składniki z różnymi opcjami kompilacji. Na przykład możesz utworzyć kompilację debugowania z informacjami o symbolach lub kompilacją wydania bez informacji o symbolach, ale z włączonymi optymalizacjami. Lub można skompilować projekt do uruchamiania na określonej platformie, takiej jak x86 lub x64. We wszystkich tych przypadkach większość opcji kompilacji pozostaje taka sama; tylko kilka opcji jest zmienianych w celu sterowania konfiguracją kompilacji. Za pomocą programu MSBuild można używać właściwości i warunków do tworzenia różnych konfiguracji kompilacji.

## <a name="use-properties-to-control-build-settings"></a>Używanie właściwości do kontrolowania ustawień kompilacji

`Property`Element definiuje zmienną, do której odwołuje się kilka razy w pliku projektu, takich jak lokalizacja katalogu tymczasowego lub ustawienie wartości właściwości, które są używane w kilku konfiguracjach, takich jak Kompilacja debugowania i kompilacja wydania. Aby uzyskać więcej informacji na temat właściwości, zobacz [Właściwości programu MSBuild](../msbuild/msbuild-properties.md).

Właściwości można użyć do zmiany konfiguracji kompilacji bez konieczności zmiany pliku projektu. `Condition`Atrybut `Property` elementu i `PropertyGroup` elementu umożliwia zmianę wartości właściwości. Aby uzyskać więcej informacji na temat warunków programu MSBuild, zobacz [warunki](../msbuild/msbuild-conditions.md).

### <a name="to-set-a-group-of-properties-that-depends-on-another-property"></a>Aby ustawić grupę właściwości, które są zależne od innej właściwości

- Użyj `Condition` atrybutu w `PropertyGroup` elemencie podobnym do poniższego:

  ```xml
  <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">
      <DebugType>full</DebugType>
      <Optimize>no</Optimize>
  </PropertyGroup>
  ```

### <a name="to-define-a-property-that-depends-on-another-property"></a>Aby zdefiniować właściwość, która zależy od innej właściwości

- Użyj `Condition` atrybutu w `Property` elemencie podobnym do poniższego:

  ```xml
  <DebugType Condition="'$(Flavor)'=='DEBUG'">full</DebugType>
  ```

## <a name="specify-properties-on-the-command-line"></a>Określ właściwości w wierszu polecenia

Po zapisaniu pliku projektu w celu zaakceptowania wielu konfiguracji należy mieć możliwość zmiany tych konfiguracji przy każdym kompilowaniu projektu. Program MSBuild zapewnia tę możliwość, umożliwiając określenie właściwości w wierszu polecenia przy użyciu przełącznika **-Property** lub **-p** .

### <a name="to-set-a-project-property-at-the-command-line"></a>Aby ustawić właściwość projektu w wierszu polecenia

- Użyj przełącznika **-Property** z wartością właściwości i właściwości. Na przykład:

  ```cmd
  msbuild file.proj -property:Flavor=Debug
  ```

  lub

  ```cmd
  Msbuild file.proj -p:Flavor=Debug
  ```

### <a name="to-specify-more-than-one-project-property-at-the-command-line"></a>Aby określić więcej niż jedną właściwość projektu w wierszu polecenia

- Należy wielokrotnie używać przełącznika **-Property** lub **-p** z wartościami właściwości i właściwości albo użyć jednej **Właściwości** lub **-p** przełącznika i oddzielić wiele właściwości średnikami (;). Na przykład:

  ```cmd
  msbuild file.proj -p:Flavor=Debug;Platform=x86
  ```

  lub

  ```cmd
  msbuild file.proj -p:Flavor=Debug -p:Platform=x86
  ```

  Zmienne środowiskowe są również traktowane jako właściwości i automatycznie włączane przez program MSBuild. Aby uzyskać więcej informacji o używaniu zmiennych środowiskowych, zobacz [How to: use Environment w Build](../msbuild/how-to-use-environment-variables-in-a-build.md).

  Wartość właściwości określona w wierszu polecenia ma pierwszeństwo przed każdą wartością ustawioną dla tej samej właściwości w pliku projektu, a ta wartość w pliku projektu ma pierwszeństwo przed wartością w zmiennej środowiskowej.

  Można zmienić to zachowanie przy użyciu `TreatAsLocalProperty` atrybutu w tagu projektu. W przypadku nazw właściwości, które są wyświetlane na liście z tym atrybutem wartość właściwości określona w wierszu polecenia nie ma pierwszeństwa przed wartością w pliku projektu. Przykład można znaleźć w dalszej części tego tematu.

## <a name="example"></a>Przykład

Poniższy przykład kodu, projekt "Hello world", zawiera dwie nowe grupy właściwości, których można użyć do utworzenia kompilacji debugowania i kompilacji wydania.

Aby skompilować wersję do debugowania tego projektu, wpisz:

```cmd
msbuild consolehwcs1.proj -p:flavor=debug
```

Aby skompilować wersję handlową tego projektu, wpisz:

```cmd
msbuild consolehwcs1.proj -p:flavor=retail
```

```xml
<Project DefaultTargets = "Compile"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <!-- Sets the default flavor if an environment variable called
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

Poniższy przykład ilustruje sposób użycia `TreatAsLocalProperty` atrybutu. `Color`Właściwość ma wartość `Blue` w pliku projektu i `Green` w wierszu polecenia. `TreatAsLocalProperty="Color"`W tagu projektu właściwość wiersza polecenia ( `Green` ) nie przesłania właściwości zdefiniowanej w pliku projektu ( `Blue` ).

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
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [Project — element (MSBuild)](../msbuild/project-element-msbuild.md)
