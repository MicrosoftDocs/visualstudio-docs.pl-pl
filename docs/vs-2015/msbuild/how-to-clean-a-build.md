---
title: 'Instrukcje: czyszczenie kompilacji | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, cleaning a build
- directories [.NET Framework], for output items
- output, removing items
ms.assetid: 999ba473-b0c4-45c7-930a-63ea7a510509
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f8c64bb19d65540f8c72be9acb1c5f59deb3c8f9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156643"
---
# <a name="how-to-clean-a-build"></a>Porady: czyszczenie kompilacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gdy czyścisz kompilację, wszystkie pliki pośrednie i wyjściowe zostaną usunięte, pozostawiając tylko pliki projektu i składnika. Z plików projektu i składników można następnie skompilować nowe wystąpienia plików pośrednich i wyjściowych. Biblioteka typowych zadań, które znajdują się w programie, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zawiera zadanie [exec](../msbuild/exec-task.md) , którego można użyć do uruchamiania poleceń systemowych. Aby uzyskać więcej informacji na temat biblioteki zadań, zobacz [Dokumentacja zadania](../msbuild/msbuild-task-reference.md).  
  
## <a name="creating-a-directory-for-output-items"></a>Tworzenie katalogu dla elementów wyjściowych  
 Domyślnie plik. exe, który jest tworzony podczas kompilowania projektu, jest umieszczany w tym samym katalogu, w którym znajdują się pliki projektu i plików źródłowych. Zwykle jednak elementy wyjściowe są tworzone w osobnym katalogu.  
  
#### <a name="to-create-a-directory-for-output-items"></a>Aby utworzyć katalog dla elementów wyjściowych  
  
1. Użyj `Property` elementu, aby zdefiniować lokalizację i nazwę katalogu. Na przykład Utwórz katalog o nazwie `BuiltApp` w katalogu zawierającym pliki projektu i źródła:  
  
     `<builtdir>BuiltApp</builtdir>`  
  
2. Użyj zadania [MakeDir](../msbuild/makedir-task.md) , aby utworzyć katalog, jeśli katalog nie istnieje. Na przykład:  
  
     `<MakeDir Directories = "$(builtdir)"`  
  
     `Condition = "!Exists('$(builtdir)')" />`  
  
## <a name="removing-the-output-items"></a>Usuwanie elementów wyjściowych  
 Przed utworzeniem nowych wystąpień plików pośrednich i wyjściowych warto wyczyścić wszystkie poprzednie wystąpienia plików pośrednich i wyjściowych. Użyj zadania [RemoveDir —](../msbuild/removedir-task.md) , aby usunąć katalog i wszystkie pliki i katalogi, które zawiera z dysku.  
  
#### <a name="to-remove-a-directory-and-all-files-contained-in-the-directory"></a>Aby usunąć katalog i wszystkie pliki znajdujące się w katalogu  
  
- Użyj `RemoveDir` zadania, aby usunąć katalog. Na przykład:  
  
     `<RemoveDir Directories="$(builtdir)" />`  
  
## <a name="example"></a>Przykład  
 Następujący przykładowy kod projektu zawiera nowy obiekt docelowy, `Clean` który używa `RemoveDir` zadania do usuwania katalogu i wszystkich plików i katalogów, które zawiera. Ponadto w tym przykładzie `Compile` obiekt docelowy tworzy oddzielny katalog dla elementów wyjściowych, które są usuwane podczas czyszczenia kompilacji.  
  
 `Compile` jest zdefiniowany jako domyślny element docelowy i dlatego jest używany automatycznie, o ile nie zostanie określony inny element docelowy lub docelowy. Aby określić inny element docelowy, należy użyć opcji wiersz polecenia **/Target** . Na przykład:  
  
 `msbuild <file name>.proj /target:Clean`  
  
 Przełącznik **/Target** można skrócić do **/t** i można określić więcej niż jeden obiekt docelowy. Na przykład, aby użyć obiektu docelowego `Clean` `Compile` , należy wpisać:  
  
 `msbuild <file name>.proj /t:Clean;Compile`  
  
```  
<Project DefaultTargets = "Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003" >  
  
    <PropertyGroup>  
        <!-- Set the application name as a property -->  
        <name>HelloWorldCS</name>  
  
        <!-- Set the output folder as a property -->  
        <builtdir>BuiltApp</builtdir>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <!-- Specify the inputs by type and file name -->  
        <CSFile Include = "consolehwcs1.cs"/>  
    </ItemGroup>  
  
    <Target Name = "Compile">  
        <!-- Check whether an output folder exists and create  
        one if necessary -->  
        <MakeDir Directories = "$(builtdir)"   
            Condition = "!Exists('$(builtdir)')" />  
  
        <!-- Run the Visual C# compiler -->  
        <CSC Sources = "@(CSFile)"   
            OutputAssembly = "$(BuiltDir)\$(appname).exe">  
            <Output TaskParameter = "OutputAssembly"  
                ItemName = "EXEFile" />  
        </CSC>  
  
        <!-- Log the file name of the output file -->  
        <Message Text="The output file is @(EXEFile)"/>  
    </Target>  
  
    <Target Name = "Clean">  
        <RemoveDir Directories="$(builtdir)" />  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Exec — zadanie](../msbuild/exec-task.md)   
 [MakeDir, zadanie](../msbuild/makedir-task.md)   
 [RemoveDir —, zadanie](../msbuild/removedir-task.md)   
 [CSC — zadanie](../msbuild/csc-task.md)   
 [Targets (Obiekty docelowe)](../msbuild/msbuild-targets.md)
