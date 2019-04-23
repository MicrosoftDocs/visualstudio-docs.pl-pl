---
title: 'Instrukcje: Użycie znaków zarezerwowanych XML w plikach projektu | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60089383"
---
# <a name="how-to-use-reserved-xml-characters-in-project-files"></a>Instrukcje: Użycie znaków zarezerwowanych XML w plikach projektu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas tworzenia plików projektu, może być konieczne użycie zarezerwowanych znaków XML w przypadku, na przykład w wartości właściwości lub wartości parametrów zadania. Jednak niektóre zastrzeżone znaki muszą zostać zastąpione nazwanych jednostek, dzięki czemu można przeanalizować pliku projektu.  
  
## <a name="using-reserved-characters"></a>Przy użyciu znaków zastrzeżonych  
 W poniższej tabeli opisano zarezerwowanych znaków XML, które muszą zostać zastąpione odpowiednia jednostka o nazwie, dzięki czemu można przeanalizować pliku projektu.  
  
|Zastrzeżonego znaku|Nazwanych jednostek|  
|------------------------|------------------|  
|\<|&lt;|  
|>|&gt;|  
|&|&amp;|  
|"|&quot;|  
|'|&apos;|  
  
#### <a name="to-use-double-quotes-in-a-project-file"></a>Aby używać cudzysłowów w pliku projektu  
  
- Zamień podwójnych cudzysłowów odpowiadającą nazwie podmiotu, &quot;. Na przykład, aby umieścić podwójnego cudzysłowu wokół `EXEFile` listy elementów, wpisz:  
  
    ```  
    <Message Text="The output file is "@(EXEFile)"."/>  
    ```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie kodu podwójne cudzysłowy są używane do zaznacz nazwę pliku na komunikat, który jest wysyłany przy użyciu pliku projektu.  
  
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
 [Odwołanie do MSBuild](../msbuild/msbuild-reference.md) [MSBuild](msbuild.md)
