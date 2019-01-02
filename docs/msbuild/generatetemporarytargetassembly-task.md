---
title: Generatetemporarytargetassembly — zadanie | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- build process [WPF MSBuild], XAML page refers to a locally declared type
- GenerateTemporaryTargetAssembly task [WPF MSBuild]
- GenerateTemporaryTargetAssembly task [WPF MSBuild], parameters
- creating an assembly [WPF MSBuild], XAML page refers to a locally declared type
ms.assetid: 92b6539c-6897-45e0-8989-0c234bbfe782
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 87ec3fff69bd5d8ddf7ffdfdc5590e1c18a02038
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53968011"
---
# <a name="generatetemporarytargetassembly-task"></a>Generatetemporarytargetassembly — zadanie
<xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> Zadanie generuje zestaw, jeśli co najmniej jeden [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] strony w projekcie odwołuje się do typu, który jest zadeklarowany lokalnie w tym projekcie. Wygenerowanego zestawu jest usuwany po zakończeniu procesu kompilacji, czy Proces kompilacji zakończy się niepowodzeniem.  
  
## <a name="task-parameters"></a>Parametry zadania  
  
| Parametr | Opis |
|--------------------------| - |
| `AssemblyName` | Wymagane **ciąg** parametru.<br /><br /> Określa krótką nazwę zestawu, który jest generowany dla projektu i jest również nazwą zestawu docelowego, który tymczasowo jest generowany. Na przykład, jeśli projekt wygeneruje [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] plik wykonywalny, którego nazwa jest *WinExeAssembly.exe*, **AssemblyName** parametr ma wartość **WinExeAssembly**. |
| `CompileTargetName` | Wymagane **ciąg** parametru.<br /><br /> Określa nazwę [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] docelowy, który jest używany do generowania zestawów z plików kodu źródłowego. Typowa wartość dla **CompileTargetName** jest **CoreCompile**. |
| `CompileTypeName` | Wymagane **ciąg** parametru.<br /><br /> Określa typ kompilacji, która jest wykonywana przez element docelowy, który jest określony przez **CompileTargetName** parametru. Aby uzyskać **CoreCompile** obiektu docelowego, ta wartość jest **skompilować**. |
| `CurrentProject` | Wymagane **ciąg** parametru.<br /><br /> Określa pełną ścieżkę [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] pliku projektu, który wymaga zestawu tymczasowego docelowego. |
| `GeneratedCodeFiles` | Opcjonalnie **[] ITaskItem** parametru.<br /><br /> Określa listę plików specyficznych dla języka kodu zarządzanego, które zostały wygenerowane przez [markupcompilepass1 —](../msbuild/markupcompilepass1-task.md) zadania. |
| `IntermediateOutputPath` | Wymagane **ciąg** parametru.<br /><br /> Określa katalog wygenerowanego zestawu docelowego tymczasowej. |
| `MSBuildBinPath` | Wymagane **ciąg** parametru.<br /><br /> Określa lokalizację *MSBuild.exe*, co jest wymagane do kompilowania zestawu docelowego tymczasowej. |
| `ReferencePath` | Opcjonalnie **[] ITaskItem** parametru.<br /><br /> Określa listę zestawów, ścieżkę i nazwę pliku, który odwołuje się typy, które są kompilowane do zestawu docelowego tymczasowej. |
| `ReferencePathTypeName` | Wymagane **ciąg** parametru.<br /><br /> Określa parametr, który jest używany przez element docelowy kompilacji (**CompileTargetName**) parametr, który określa listę odwołań do zestawu (**ReferencePath**). Jest odpowiednią wartość **ReferencePath**. |
  
## <a name="remarks"></a>Uwagi  
 Pierwszym przebiegu kompilacji znaczników, który jest wykonywany przez [markupcompilepass1 —](../msbuild/markupcompilepass1-task.md), kompiluje [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] pliki na format binarny. W związku z tym, kompilator musi listę przywoływanych zestawów zawierających typy, które są używane przez [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] plików. Jednak jeśli [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] plik używa typ, który jest zdefiniowany w tym samym projekcie, odpowiedniego zestawu dla tego projektu nie jest tworzony, dopóki projekt jest kompilowany. W związku z tym odwołania do zestawu, nie można podać podczas pierwszego przejścia znaczników w kompilacji.  
  
 Zamiast tego **markupcompilepass1 —** odracza konwersji [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] przekazać pliki, które zawierają odwołania do typów w tym samym projekcie do drugiego kompilacji znaczników, które jest wykonywane przez [markupcompilepass2 —](../msbuild/markupcompilepass2-task.md). Przed **markupcompilepass2 —** jest wykonywane, tymczasowy zestawu jest generowany. Ten zestaw zawiera typy, które są używane przez [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] pliki, których kompilacji znaczników — dostęp próbny został wstrzymany. Odwołanie do zestawu wygenerowany został dostarczony do **markupcompilepass2 —** podczas wykonywania umożliwiające odroczonego kompilacji [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] pliki, które ma zostać przekonwertowany na format binarny.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje zestaw tymczasowego, ponieważ *Page1.xaml* zawiera odwołanie do typu, który znajduje się w tym samym projekcie.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask  
    TaskName="Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="GenerateTemporaryTargetAssemblyTask">  
    <GenerateTemporaryTargetAssembly  
      AssemblyName="WPFMSBuildSample"  
      CompileTargetName="CoreCompile"  
      CompileTypeName="Compile"  
      CurrentProject="FullBuild.proj"  
      GeneratedCodeFiles="obj\debug\app.g.cs;obj\debug\Page1.g.cs;obj\debug\Page2.g.cs"  
      ReferencePath="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll"  
      IntermediateOutputPath=".\obj\debug\"  
      MSBuildBinPath="$(MSBuildBinPath)"  
      ReferencePathTypeName="ReferencePath"/>  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/wpf-msbuild-task-reference.md)   
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)   
 [Omówienie aplikacji przeglądarki XAML w WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)