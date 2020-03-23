---
title: 'Jak: Tworzenie tych samych plików źródłowych z różnymi opcjami | Dokumenty firmy Microsoft'
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
ms.openlocfilehash: c31da244e5c264bb81498c6091aefce7e6318bb2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633944"
---
# <a name="how-to-build-the-same-source-files-with-different-options"></a>Jak: Tworzenie tych samych plików źródłowych z różnymi opcjami

Podczas tworzenia projektów często kompilować te same składniki z różnych opcji kompilacji. Na przykład można utworzyć kompilację debugowania z informacjami o symbolu lub kompilację wydania bez informacji o symbolu, ale z włączoną optymalizacją. Możesz też utworzyć projekt do uruchomienia na określonej platformie, takiej jak x86 lub x64. We wszystkich tych przypadkach większość opcji kompilacji pozostają takie same; tylko kilka opcji są zmieniane, aby kontrolować konfigurację kompilacji. Za pomocą MSBuild, można użyć właściwości i warunki do tworzenia różnych konfiguracji kompilacji.

## <a name="use-properties-to-control-build-settings"></a>Używanie właściwości do kontrolowania ustawień kompilacji

Element `Property` definiuje zmienną, do którego odwołuje się kilka razy w pliku projektu, takich jak lokalizacja katalogu tymczasowego lub ustawić wartości dla właściwości, które są używane w kilku konfiguracjach, takich jak kompilacja debugowania i kompilacja wydania. Aby uzyskać więcej informacji o właściwościach, zobacz [WŁAŚCIWOŚCI MSBuild](../msbuild/msbuild-properties.md).

Właściwości można użyć, aby zmienić konfigurację kompilacji bez konieczności zmiany pliku projektu. Atrybut `Condition` `Property` elementu i `PropertyGroup` elementu pozwala na zmianę wartości właściwości. Aby uzyskać więcej informacji na temat warunków MSBuild, zobacz [Warunki](../msbuild/msbuild-conditions.md).

### <a name="to-set-a-group-of-properties-that-depends-on-another-property"></a>Aby ustawić grupę właściwości zależną od innej właściwości

- Użyj `Condition` atrybutu w `PropertyGroup` elemencie podobnym do następującego:

  ```xml
  <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">
      <DebugType>full</DebugType>
      <Optimize>no</Optimize>
  </PropertyGroup>
  ```

### <a name="to-define-a-property-that-depends-on-another-property"></a>Aby zdefiniować właściwość zależną od innej właściwości

- Użyj `Condition` atrybutu w `Property` elemencie podobnym do następującego:

  ```xml
  <DebugType Condition="'$(Flavor)'=='DEBUG'">full</DebugType>
  ```

## <a name="specify-properties-on-the-command-line"></a>Określanie właściwości w wierszu polecenia

Po zapisaniu pliku projektu w celu zaakceptowania wielu konfiguracji, musisz mieć możliwość zmiany tych konfiguracji przy każdym tworzeniu projektu. MSBuild zapewnia tę możliwość, zezwalając na właściwości, które mają być określone w wierszu polecenia za pomocą **przełącznika -property** lub **-p.**

### <a name="to-set-a-project-property-at-the-command-line"></a>Aby ustawić właściwość projektu w wierszu polecenia

- Użyj przełącznika **-property** z właściwością i wartością właściwości. Przykład:

  ```cmd
  msbuild file.proj -property:Flavor=Debug
  ```

  lub

  ```cmd
  Msbuild file.proj -p:Flavor=Debug
  ```

### <a name="to-specify-more-than-one-project-property-at-the-command-line"></a>Aby określić więcej niż jedną właściwość projektu w wierszu polecenia

- Użyj **przełącznika -property** lub **-p** wiele razy z wartościami właściwości i właściwości lub użyj przełącznika **"właściwość** lub **-p"** i oddziel wiele właściwości średnikami (;). Przykład:

  ```cmd
  msbuild file.proj -p:Flavor=Debug;Platform=x86
  ```

  lub

  ```cmd
  msbuild file.proj -p:Flavor=Debug -p:Platform=x86
  ```

  Zmienne środowiskowe są również traktowane jako właściwości i są automatycznie włączane przez MSBuild. Aby uzyskać więcej informacji na temat używania zmiennych środowiskowych, zobacz [Jak: Używanie zmiennych środowiskowych w kompilacji](../msbuild/how-to-use-environment-variables-in-a-build.md).

  Wartość właściwości, która jest określona w wierszu polecenia ma pierwszeństwo przed dowolną wartością, która jest ustawiona dla tej samej właściwości w pliku projektu, a ta wartość w pliku projektu ma pierwszeństwo przed wartością w zmiennej środowiskowej.

  To zachowanie można zmienić `TreatAsLocalProperty` za pomocą atrybutu w tagu projektu. W przypadku nazw właściwości, które są wymienione z tym atrybutem, wartość właściwości określona w wierszu polecenia nie ma pierwszeństwa przed wartością w pliku projektu. Przykład można znaleźć w dalszej części tego tematu.

## <a name="example"></a>Przykład

Poniższy przykład kodu, "Hello World" projekt zawiera dwie nowe grupy właściwości, które mogą służyć do tworzenia kompilacji debugowania i kompilacji release.

Aby utworzyć wersję debugowania tego projektu, wpisz:

```cmd
msbuild consolehwcs1.proj -p:flavor=debug
```

Aby utworzyć wersję detaliczną tego projektu, wpisz:

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

Poniższy przykład ilustruje `TreatAsLocalProperty` sposób użycia atrybutu. Właściwość `Color` ma wartość `Blue` w pliku `Green` projektu i w wierszu polecenia. W `TreatAsLocalProperty="Color"` tagu projektu właściwość wiersza`Green`polecenia ( ) nie zastępuje właściwości zdefiniowanej w`Blue`pliku projektu ( ).

Aby utworzyć projekt, wprowadź następujące polecenie:

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

## <a name="see-also"></a>Zobacz też

- [Msbuild](../msbuild/msbuild.md)
- [Koncepcje MSBuild](../msbuild/msbuild-concepts.md)
- [Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)
- [Element projektu (MSBuild)](../msbuild/project-element-msbuild.md)
