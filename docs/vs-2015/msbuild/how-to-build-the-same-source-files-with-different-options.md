---
title: 'Instrukcje: kompilowanie tych samych plików źródłowych przy użyciu różnych opcji | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- source files, building with different options
- MSBuild, properties
- project properties, modifying
- Hello World example [Visual Studio]
ms.assetid: d14f1212-ddd9-434f-b138-f840011b0fb2
caps.latest.revision: 23
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8bf76967363f4c0d97d93c895fbeb6209c8503f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67821682"
---
# <a name="how-to-build-the-same-source-files-with-different-options"></a>Porady: kompilacja tych samych plików źródłowych przy użyciu różnych opcji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas kompilowania projektów często kompilujesz te same składniki z różnymi opcjami kompilacji. Na przykład możesz utworzyć kompilację debugowania z informacjami o symbolach lub kompilacją wydania bez informacji o symbolach, ale z włączonymi optymalizacjami. Lub można skompilować projekt do uruchamiania na określonej platformie, takiej jak x86 lub [!INCLUDE[vcprx64](../includes/vcprx64-md.md)] . We wszystkich tych przypadkach większość opcji kompilacji pozostaje taka sama; tylko kilka opcji jest zmienianych w celu sterowania konfiguracją kompilacji. W programie należy [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] używać właściwości i warunków do tworzenia różnych konfiguracji kompilacji.  
  
## <a name="using-properties-to-modify-projects"></a>Modyfikowanie projektów przy użyciu właściwości  
 `Property`Element definiuje zmienną, do której odwołuje się kilka razy w pliku projektu, takich jak lokalizacja katalogu tymczasowego lub ustawienie wartości właściwości, które są używane w kilku konfiguracjach, takich jak Kompilacja debugowania i kompilacja wydania. Aby uzyskać więcej informacji na temat właściwości, zobacz [Właściwości programu MSBuild](msbuild-properties1.md).  
  
 Właściwości można użyć do zmiany konfiguracji kompilacji bez konieczności zmiany pliku projektu. `Condition`Atrybut `Property` elementu i `PropertyGroup` elementu umożliwia zmianę wartości właściwości. Aby uzyskać więcej informacji o [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] warunkach, zobacz [warunki](../msbuild/msbuild-conditions.md).  
  
#### <a name="to-set-a-group-of-properties-based-on-another-property"></a>Aby ustawić grupę właściwości na podstawie innej właściwości  
  
- Użyj `Condition` atrybutu w `PropertyGroup` elemencie podobnym do poniższego:  
  
    ```  
    <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">  
        <DebugType>full</DebugType>  
        <Optimize>no</Optimize>  
    </PropertyGroup>  
    ```  
  
#### <a name="to-define-a-property-based-on-another-property"></a>Aby zdefiniować właściwość w oparciu o inną właściwość  
  
- Użyj `Condition` atrybutu w `Property` elemencie podobnym do poniższego:  
  
    ```  
    <DebugType Condition="'$(Flavor)'=='DEBUG'">full</DebugType>  
    ```  
  
## <a name="specifying-properties-on-the-command-line"></a>Określanie właściwości w wierszu polecenia  
 Po zapisaniu pliku projektu w celu zaakceptowania wielu konfiguracji należy mieć możliwość zmiany tych konfiguracji przy każdym kompilowaniu projektu. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zapewnia tę możliwość, umożliwiając określenie właściwości w wierszu polecenia przy użyciu przełącznika **/Property** lub **/p** .  
  
#### <a name="to-set-a-project-property-at-the-command-line"></a>Aby ustawić właściwość projektu w wierszu polecenia  
  
- Użyj przełącznika **/Property** z wartością właściwości i właściwości. Na przykład:  
  
    ```  
    msbuild file.proj /property:Flavor=Debug  
    ```  
  
     \- oraz  
  
    ```  
    Msbuild file.proj /p:Flavor=Debug  
    ```  
  
#### <a name="to-specify-more-than-one-project-property-at-the-command-line"></a>Aby określić więcej niż jedną właściwość projektu w wierszu polecenia  
  
- Użyj przełącznika **/Property** lub **/p** wiele razy z wartościami właściwości i właściwości albo użyj jednego **/Property** lub **/p** Switch i Oddziel wiele właściwości średnikami (;). Na przykład:  
  
  ```  
  msbuild file.proj /p:Flavor=Debug;Platform=x86  
  ```  
  
   \- oraz  
  
  ```  
  msbuild file.proj /p:Flavor=Debug /p:Platform=x86  
  ```  
  
  Zmienne środowiskowe są również traktowane jako właściwości i automatycznie włączane przez program [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Aby uzyskać więcej informacji o używaniu zmiennych środowiskowych, zobacz [How to: use Environment w Build](../msbuild/how-to-use-environment-variables-in-a-build.md).  
  
  Wartość właściwości określona w wierszu polecenia ma pierwszeństwo przed każdą wartością ustawioną dla tej samej właściwości w pliku projektu, a ta wartość w pliku projektu ma pierwszeństwo przed wartością w zmiennej środowiskowej.  
  
  Można zmienić to zachowanie przy użyciu `TreatAsLocalProperty` atrybutu w tagu projektu. W przypadku nazw właściwości, które są wyświetlane na liście z tym atrybutem wartość właściwości określona w wierszu polecenia nie ma pierwszeństwa przed wartością w pliku projektu. Przykład można znaleźć w dalszej części tego tematu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu, projekt "Hello world", zawiera dwie nowe grupy właściwości, których można użyć do utworzenia kompilacji debugowania i kompilacji wydania.  
  
 Aby skompilować wersję do debugowania tego projektu, wpisz:  
  
```  
msbuild consolehwcs1.proj /p:flavor=debug  
```  
  
 Aby skompilować wersję handlową tego projektu, wpisz:  
  
```  
msbuild consolehwcs1.proj /p:flavor=retail  
```  
  
```  
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
 Poniższy przykład ilustruje sposób użycia `TreatAsLocalProperty` atrybutu. `Color`Właściwość ma wartość `Blue` w pliku projektu i `Green` w wierszu polecenia. `TreatAsLocalProperty="Color"`W tagu projektu właściwość wiersza polecenia ( `Green` ) nie przesłania właściwości zdefiniowanej w pliku projektu ( `Blue` ).  
  
 Aby skompilować projekt, wprowadź następujące polecenie:  
  
```  
msbuild colortest.proj /t:go /property:Color=Green  
```  
  
```  
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
[MSBuild](msbuild.md)  
 [Pojęcia dotyczące programu MSBuild](../msbuild/msbuild-concepts.md)   
 [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)   
 [Project — Element (MSBuild)](../msbuild/project-element-msbuild.md)
