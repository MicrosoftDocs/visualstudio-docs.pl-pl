---
title: 'Instrukcje: Czyszczenie kompilacji | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Exec task [MSBuild]
- MSBuild, cleaning a build
- directories [.NET Framework], for output items
- output, removing items
ms.assetid: 999ba473-b0c4-45c7-930a-63ea7a510509
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ddd4158561b0bac7ea3347738f13f0f9530002ea
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53841135"
---
# <a name="how-to-clean-a-build"></a>Instrukcje: Czyszczenie kompilacji
Podczas oczyszczania kompilacji są usuwane wszystkie pliki pośrednich i wynikowych, pozostawiając tylko pliki projektu, jak i składnika. W plikach projektu, jak i składnika nowych wystąpień pośrednich i pliki wyjściowe może następnie być skompilowana. Biblioteka typowych zadań, które jest dostarczane z [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] obejmuje [Exec](../msbuild/exec-task.md) zadanie, które służy do uruchamiania poleceń systemowych. Aby uzyskać więcej informacji na temat biblioteki zadań, zobacz [zadania, odwołanie](../msbuild/msbuild-task-reference.md).  
  
## <a name="create-a-directory-for-output-items"></a>Utwórz katalog dla danych wyjściowych elementów  
 Domyślnie *.exe* plik, który jest tworzony podczas kompilowania projektu jest umieszczany w tym samym katalogu co pliki projektu i źródła. Zwykle jednak dane wyjściowe są tworzone elementy w oddzielnym katalogu.  
  
#### <a name="to-create-a-directory-for-output-items"></a>Można utworzyć katalogu danych wyjściowych elementów  
  
1.  Użyj `Property` elementu, aby zdefiniować lokalizację i nazwę katalogu. Na przykład można utworzyć katalog o nazwie *BuiltApp* w katalogu, który zawiera pliki projektu i źródła:  
  
     `<builtdir>BuiltApp</builtdir>`  
  
2.  Użyj [MakeDir](../msbuild/makedir-task.md) zadania do utworzenia katalogu, jeśli katalog nie istnieje. Na przykład:  
  
     ```xml
     <MakeDir Directories = "$(builtdir)"  
      Condition = "!Exists('$(builtdir)')" />
     ```
  
## <a name="remove-the-output-items"></a>Usuń elementy danych wyjściowych  
 Przed utworzeniem nowych wystąpień plików pośrednich i wynikowych, warto wyczyścić wszystkie poprzednie wystąpień plików pośrednich i wynikowych. Użyj [removedir —](../msbuild/removedir-task.md) zadanie, aby usunąć katalog i wszystkie pliki i katalogi, które zawiera z dysku.  
  
#### <a name="to-remove-a-directory-and-all-files-contained-in-the-directory"></a>Aby usunąć katalog i wszystkie pliki znajdujące się w katalogu  
  
-   Użyj `RemoveDir` zadań można usunąć katalogu. Na przykład:  
  
     `<RemoveDir Directories="$(builtdir)" />`  
  
## <a name="example"></a>Przykład  
 Poniższy kod przykładowy projekt zawiera nowy obiekt docelowy `Clean`, który używa `RemoveDir` zadanie, aby usunąć katalog i wszystkie pliki i katalogi, które zawiera. Również w tym przykładzie `Compile` docelowej tworzy oddzielny katalog dla elementów danych wyjściowych, które są usuwane, gdy kompilacja jest czyszczona.  
  
 `Compile` jest zdefiniowany jako domyślnego obiektu docelowego i w związku z tym jest używany automatycznie, chyba że określisz inną docelową lub miejsc docelowych. Możesz użyć przełącznika wiersza polecenia **-target** Aby określić inny element docelowy. Na przykład:  
  
 `msbuild <file name>.proj -target:Clean`  
  
 **-Target** przełącznik może zostać skrócony do **-t** i można określić więcej niż jeden element docelowy. Na przykład użycie wartości docelowej `Clean` następnie element docelowy `Compile`, wpisz:  
  
 `msbuild <file name>.proj -t:Clean;Compile`  
  
```xml  
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
  
## <a name="see-also"></a>Zobacz także  
 [Exec — zadanie](../msbuild/exec-task.md)   
 [Makedir — zadanie](../msbuild/makedir-task.md)   
 [Removedir — zadanie](../msbuild/removedir-task.md)   
 [CSC — zadanie](../msbuild/csc-task.md)   
 [Docelowe elementy](../msbuild/msbuild-targets.md)