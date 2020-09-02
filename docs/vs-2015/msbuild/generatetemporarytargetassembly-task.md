---
title: GenerateTemporaryTargetAssembly — — Zadanie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2ce412fdeb8d466708f3231cba14718d13720c69
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65676647"
---
# <a name="generatetemporarytargetassembly-task"></a>GenerateTemporaryTargetAssembly — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>Zadanie generuje zestaw, jeśli co najmniej jedna [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] Strona w projekcie odwołuje się do typu, który jest zadeklarowany lokalnie w tym projekcie. Wygenerowany zestaw jest usuwany po zakończeniu procesu kompilacji lub w przypadku niepowodzenia procesu kompilacji.  
  
## <a name="task-parameters"></a>Parametry zadania  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AssemblyName`|Wymagany parametr **ciągu** .<br /><br /> Określa krótką nazwę zestawu, który jest generowany dla projektu i jest również nazwą zestawu docelowego, który jest tymczasowo generowany. Na przykład jeśli projekt generuje [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] plik wykonywalny, którego nazwa jest **WinExeAssembly.exe**, parametr **AssemblyName** ma wartość **WinExeAssembly**.|  
|`CompileTargetName`|Wymagany parametr **ciągu** .<br /><br /> Określa nazwę [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)] obiektu docelowego, który jest używany do generowania zestawów z plików kodu źródłowego. Typową wartością dla **CompileTargetName** jest **CoreCompile**.|  
|`CompileTypeName`|Wymagany parametr **ciągu** .<br /><br /> Określa typ kompilacji wykonywanej przez obiekt docelowy określony przez parametr **CompileTargetName** . Dla elementu docelowego **CoreCompile** ta wartość jest **Kompiluj**.|  
|`CurrentProject`|Wymagany parametr **ciągu** .<br /><br /> Określa pełną ścieżkę [!INCLUDE[TLA2#tla_msbuild](../includes/tla2sharptla-msbuild-md.md)] pliku projektu dla projektu, który wymaga tymczasowego zestawu docelowego.|  
|`GeneratedCodeFiles`|Opcjonalny parametr **ITaskItem []** .<br /><br /> Określa listę plików kodu zarządzanego specyficznego dla języka, które zostały wygenerowane przez zadanie [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md) .|  
|`IntermediateOutputPath`|Wymagany parametr **ciągu** .<br /><br /> Określa katalog, do którego jest generowany tymczasowy zestaw docelowy.|  
|`MSBuildBinPath`|Wymagany parametr **ciągu** .<br /><br /> Określa lokalizację **MSBuild.exe**, która jest wymagana do skompilowania tymczasowego zestawu docelowego.|  
|`ReferencePath`|Opcjonalny parametr **ITaskItem []** .<br /><br /> Określa listę zestawów, według ścieżki i nazwy pliku, do których odwołują się typy, które są kompilowane do tymczasowego zestawu docelowego.|  
|`ReferencePathTypeName`|Wymagany parametr **ciągu** .<br /><br /> Określa parametr, który jest używany przez parametr docelowa kompilacji (**CompileTargetName**), który określa listę odwołań do zestawów (**ReferencePath**). Odpowiednia wartość to **ReferencePath**.|  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy przebieg kompilacji znacznika, który jest uruchamiany przez [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md), kompiluje [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] pliki w formacie binarnym. W związku z tym kompilator potrzebuje listy przywoływanych zestawów, które zawierają typy, które są używane przez [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] pliki. Jeśli jednak [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plik używa typu, który jest zdefiniowany w tym samym projekcie, odpowiedni zestaw dla tego projektu nie zostanie utworzony do czasu skompilowania projektu. W związku z tym nie można podać odwołania do zestawu podczas pierwszego przebiegu kompilacji znaczników.  
  
 Zamiast tego **MarkupCompilePass1** uwzględnia konwersję [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plików, które zawierają odwołania do typów w tym samym projekcie, do drugiego przebiegu kompilacji znaczników, który jest wykonywany przez [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md). Przed wykonaniem **MarkupCompilePass2** zostaje wygenerowany zestaw tymczasowy. Ten zestaw zawiera typy, które są używane przez pliki, dla [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] których została odroczona kompilacja znaczników. Odwołanie do wygenerowanego zestawu jest dostarczane do **MarkupCompilePass2** , gdy zostanie uruchomione, aby zezwolić na konwertowanie odroczonych [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plików kompilacji na format binarny.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje tymczasowy zestaw `Page1.xaml` , ponieważ zawiera odwołanie do typu, który znajduje się w tym samym projekcie.  
  
```  
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
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/wpf-msbuild-task-reference.md)   
 [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Kompilowanie aplikacji WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Przegląd Aplikacje przeglądarek WPF XAML](https://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)
