---
title: 'Instrukcje: użycie znaków zarezerwowanych XML w plikach projektu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, using reserved XML characters
- MSBuild, reserved XML characters
ms.assetid: 1ae37275-96bf-4e6e-897b-6b048e5bbe93
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: aba17e94486ca04e12055c7bf9959f927440c53d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178316"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Porady: użycie znaków zarezerwowanych XML w plikach projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas tworzenia plików projektu może być konieczne użycie znaków zarezerwowanych XML, na przykład w wartościach właściwości lub w wartościach parametrów zadania. Jednak niektóre zastrzeżone znaki muszą zostać zastąpione przez nazwaną jednostkę, aby można było analizować plik projektu.  
  
## <a name="using-reserved-characters"></a>Używanie znaków zarezerwowanych  
 W poniższej tabeli opisano zastrzeżone znaki XML, które muszą zostać zastąpione przez odpowiadającą mu nazwę jednostki, aby można było analizować plik projektu.  
  
|Znak zarezerwowany|Nazwana jednostka|  
|------------------------|------------------|  
|\<|&lt;|  
|>|&gt;|  
|&|&amp;|  
|"|&quot;|  
|'|&apos;|  
  
#### <a name="to-use-double-quotes-in-a-project-file"></a>Aby użyć podwójnych cudzysłowów w pliku projektu  
  
- Zamień podwójne cudzysłowy na odpowiadającą nazwaną jednostkę &quot; . Na przykład, aby umieścić podwójne cudzysłowy wokół `EXEFile` listy elementów, wpisz:  
  
    ```  
    <Message Text="The output file is "@(EXEFile)"."/>  
    ```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu podwójne cudzysłowy są używane do wyróżnienia nazwy pliku w wiadomości wyjściowej przez plik projektu.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
    <!-- Set the application name as a property -->  
    <PropertyGroup>  
        <appname>"HelloWorldCS"</appname>  
    </PropertyGroup>  
    <!-- Specify the inputs -->  
    <ItemGroup>  
        <CSFile Include = "consolehwcs1.cs" />  
    </ItemGroup>  
    <Target Name = "Compile">  
        <!-- Run the Visual C# compilation using input  
        files of type CSFile -->  
        <Csc Sources = "@(CSFile)">  
            <!-- Set the OutputAssembly attribute of the CSC task  
            to the name of the executable file that is created -->  
            <Output  
                TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile"/>  
        </Csc>  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is "@(EXEFile)"."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [MSBuild Reference](../msbuild/msbuild-reference.md) [MSBuild](msbuild.md) odwołania programu MSBuild
