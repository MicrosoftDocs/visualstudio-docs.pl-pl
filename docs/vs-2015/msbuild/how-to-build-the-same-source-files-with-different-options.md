---
title: 'Instrukcje: Kompilacja tych samych plików źródłowych przy użyciu różnych opcji | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: 0ce859a1fd6ee491ecf22003f5ef99936136496a
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59663148"
---
# <a name="how-to-build-the-same-source-files-with-different-options"></a>Instrukcje: Kompilacja tych samych plików źródłowych przy użyciu różnych opcji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas kompilowania projektów kompilacji są często te same składniki z opcjami różne kompilacje. Na przykład można utworzyć kompilacji debugowania przy użyciu informacji o symbolach lub kompilację wydania z nie informacji o symbolach, ale z włączonymi optymalizacjami. Możesz też skompilować projektu do uruchamiania na danej platformie, takich jak x86 lub [!INCLUDE[vcprx64](../includes/vcprx64-md.md)]. W takich przypadkach większości opcji kompilacji pozostają takie same; tylko kilka opcji zostały zmienione, aby kontrolować konfigurację kompilacji. Za pomocą [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], użyj właściwości i warunki do tworzenia innych konfiguracji kompilacji.  
  
## <a name="using-properties-to-modify-projects"></a>Aby zmodyfikować projektów za pomocą właściwości  
 `Property` Element definiuje zmienną, która odwołuje się do pliku projektu, takie jak lokalizacja katalogu tymczasowego, lub do ustawiania wartości właściwości, które są używane w kompilacji, kilka konfiguracji, takie jak kompilacja do debugowania i wydania. Aby uzyskać więcej informacji o właściwościach, zobacz [właściwości programu MSBuild](msbuild-properties1.md).  
  
 Aby zmienić konfigurację kompilacji, bez konieczności zmiany w pliku projektu, można użyć właściwości. `Condition` Atrybutu `Property` elementu i `PropertyGroup` elementu pozwala na zmianę wartości właściwości. Aby uzyskać więcej informacji na temat [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] warunkach, zobacz [warunki](../msbuild/msbuild-conditions.md).  
  
#### <a name="to-set-a-group-of-properties-based-on-another-property"></a>Aby ustawić grupę na podstawie właściwości innej właściwości  
  
-   Użyj `Condition` atrybutu w `PropertyGroup` podobny do następującego elementu:  
  
    ```  
    <PropertyGroup Condition="'$(Flavor)'=='DEBUG'">  
        <DebugType>full</DebugType>  
        <Optimize>no</Optimize>  
    </PropertyGroup>  
    ```  
  
#### <a name="to-define-a-property-based-on-another-property"></a>Aby zdefiniować właściwość, na podstawie innej właściwości  
  
-   Użyj `Condition` atrybutu w `Property` podobny do następującego elementu:  
  
    ```  
    <DebugType Condition="'$(Flavor)'=='DEBUG'">full</DebugType>  
    ```  
  
## <a name="specifying-properties-on-the-command-line"></a>Określanie właściwości w wierszu polecenia  
 Napisana pliku projektu, aby akceptował wiele konfiguracji musisz mieć możliwość zmiany te konfiguracje przy każdej kompilacji projektu. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zapewnia tę możliwość, umożliwiając właściwości można określić w wierszu polecenia za pomocą **/property** lub **/p** przełącznika.  
  
#### <a name="to-set-a-project-property-at-the-command-line"></a>Aby ustawić właściwości projektu w wierszu polecenia  
  
-   Użyj **/property** przełącznik z właściwości i wartości właściwości. Na przykład:  
  
    ```  
    msbuild file.proj /property:Flavor=Debug  
    ```  
  
     - lub —  
  
    ```  
    Msbuild file.proj /p:Flavor=Debug  
    ```  
  
#### <a name="to-specify-more-than-one-project-property-at-the-command-line"></a>Aby określić więcej niż jednej właściwości projektu w wierszu polecenia  
  
- Użyj **/property** lub **/p** przełącznika wiele razy przy użyciu właściwości i wartości właściwości lub użyć jednego **/property** lub **/p** przełącznika i wiele właściwości należy oddzielić średnikami (;). Na przykład:  
  
  ```  
  msbuild file.proj /p:Flavor=Debug;Platform=x86  
  ```  
  
   - or-  
  
  ```  
  msbuild file.proj /p:Flavor=Debug /p:Platform=x86  
  ```  
  
  Zmienne środowiskowe są także traktowane jako właściwości i są automatycznie włączone przez [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Aby uzyskać więcej informacji na temat używania zmiennych środowiskowych, zobacz [jak: Użycie zmiennych środowiskowych w kompilacji](../msbuild/how-to-use-environment-variables-in-a-build.md).  
  
  Wartość właściwości, która jest określona w wierszu polecenia mają pierwszeństwo przed wszystkie wartości, który jest skonfigurowany dla tej samej właściwości w pliku projektu, a wartość w pliku projektu mają pierwszeństwo przed wartość w zmiennej środowiskowej.  
  
  To zachowanie można zmienić za pomocą `TreatAsLocalProperty` atrybutów w znaczniku projektu. Dla nazwy właściwości, które są wyświetlane z tego atrybutu wartość właściwości, która jest określona w wierszu polecenia nie pierwszeństwo przed wartością w pliku projektu. Przykład można znaleźć w dalszej części tego tematu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu, projekt "Hello World" zawiera dwie nowe grupy właściwości, które mogą służyć do tworzenia kompilacji debugowania i kompilacji wydania.  
  
 Tworzenie wersji debugowania tego projektu, należy wpisać:  
  
```  
msbuild consolehwcs1.proj /p:flavor=debug  
```  
  
 Aby skompilować wersji detalicznej tego projektu, należy wpisać:  
  
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
 Poniższy przykład ilustruje sposób używania `TreatAsLocalProperty` atrybutu. `Color` Właściwość ma wartość `Blue` w pliku projektu i `Green` w wierszu polecenia. Za pomocą `TreatAsLocalProperty="Color"` w znaczniku projektu, a właściwość wiersza polecenia (`Green`) nie zastępuje właściwość, która jest zdefiniowana w pliku projektu (`Blue`).  
  
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
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)   
 [Project, element (MSBuild)](../msbuild/project-element-msbuild.md)
