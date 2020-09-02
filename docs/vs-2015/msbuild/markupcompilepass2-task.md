---
title: MarkupCompilePass2 — zadanie | Microsoft Docs
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
- performing second-pass markup [WPF MSBuild], MarkupCompilePass2 task
- MarkupCompilePass2 task [WPF MSBuild]
- MarkupCompilePass2 task [WPF MSBuild], parameters
ms.assetid: 1d25689a-d21f-4b05-be26-95aa0ed4fd03
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 47e27dbfa221a9476488d563ae2a48235a08f769
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703440"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>Zadanie wykonuje kompilację przy użyciu drugiego przebiegu znaczników dla [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] plików, które odwołują się do typów w tym samym projekcie.  
  
## <a name="task-parameters"></a>Parametry zadania  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|Opcjonalny parametr **logiczny** .<br /><br /> Określa, czy zadanie ma zostać uruchomione w osobnym <xref:System.AppDomain> . Jeśli ten parametr zwraca **wartość false**, zadanie jest uruchamiane w taki sam <xref:System.AppDomain> sposób jak [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)] i działa szybciej. Jeśli parametr zwraca **wartość true**, zadanie działa w drugim, <xref:System.AppDomain> który jest odizolowany od [!INCLUDE[TLA2#tla_msbuild](../includes/tla2sharptla-msbuild-md.md)] i działa wolniej.|  
|`AssembliesGeneratedDuringBuild`|Opcjonalny parametr **String []** .<br /><br /> Określa odwołania do zestawów, które zmieniają się w procesie kompilacji. Na przykład [!INCLUDE[TLA#tla_visualstu2005](../includes/tlasharptla-visualstu2005-md.md)] rozwiązanie może zawierać jeden projekt, który odwołuje się do skompilowanych danych wyjściowych innego projektu. W takim przypadku skompilowane dane wyjściowe drugiego projektu można dodać do **AssembliesGeneratedDuringBuild**.<br /><br /> Uwaga: **AssembliesGeneratedDuringBuild** musi zawierać odwołania do kompletnego zestawu zestawów, które są generowane przez rozwiązanie kompilacji.|  
|`AssemblyName`|Wymagany parametr **ciągu** .<br /><br /> Określa krótką nazwę zestawu, który jest generowany dla projektu. Na przykład jeśli projekt generuje [!INCLUDE[TLA#tla_win](../includes/tlasharptla-win-md.md)] plik wykonywalny, którego nazwa jest **WinExeAssembly.exe**, parametr **AssemblyName** ma wartość **WinExeAssembly**.|  
|`GeneratedBaml`|Opcjonalny parametr wyjściowy **ITaskItem []** .<br /><br /> Zawiera listę wygenerowanych plików w [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] formacie binarnym.|  
|`KnownReferencePaths`|Opcjonalny parametr **String []** .<br /><br /> Określa odwołania do zestawów, które nigdy nie ulegają zmianie podczas procesu kompilacji. Zawiera zestawy, które znajdują się w [!INCLUDE[TLA#tla_gac](../includes/tlasharptla-gac-md.md)] , w [!INCLUDE[TLA#tla_netframewk](../includes/tlasharptla-netframewk-md.md)] katalogu instalacyjnym i tak dalej.|  
|`Language`|Wymagany parametr **ciągu** .<br /><br /> Określa język zarządzany obsługiwany przez kompilator. Prawidłowe opcje to **C#**, **VB**, **JScript**i **C++**.|  
|`LocalizationDirectivesToLocFile`|Opcjonalny parametr **ciągu** .<br /><br /> Określa, jak generować informacje o lokalizacji dla każdego [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] pliku źródłowego. Prawidłowe opcje to **none**, **CommentsOnly**i **All**.|  
|`OutputPath`|Wymagany parametr **ciągu** .<br /><br /> Określa katalog, w którym [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] generowane są generowane pliki formatu binarnego.|  
|`OutputType`|Wymagany parametr **ciągu** .<br /><br /> Określa typ zestawu, który jest generowany przez projekt. Prawidłowe opcje to **winexe**, **exe**, **Library**i **module**.|  
|`References`|Opcjonalny parametr **ITaskItem []** .<br /><br /> Określa listę odwołań z plików do zestawów, które zawierają typy, które są używane w [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plikach. Jedno odwołanie odwołuje się do zestawu, który został wygenerowany przez <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> zadanie, które należy uruchomić przed <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> zadaniem.|  
|`RootNamespace`|Opcjonalny parametr **ciągu** .<br /><br /> Określa główną przestrzeń nazw dla klas, które znajdują się wewnątrz projektu. **RootNamespace** jest również używana jako domyślna przestrzeń nazw wygenerowanego pliku kodu zarządzanego, gdy odpowiedni [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plik nie zawiera `x:Class` atrybutu.|  
|`XAMLDebuggingInformation`|Opcjonalny parametr **logiczny** .<br /><br /> W przypadku **wartości true**informacje diagnostyczne są generowane i uwzględniane w skompilowanym czasie [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] w celu ułatwienia debugowania.|  
  
## <a name="remarks"></a>Uwagi  
 Przed uruchomieniem programu **MarkupCompilePass2**należy wygenerować tymczasowy zestaw, który zawiera typy, które są używane przez pliki, dla [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] których zostało odroczone przekazanie kompilacji znaczników. Zestaw tymczasowy jest generowany przez uruchomienie zadania **GenerateTemporaryTargetAssembly —** .  
  
 Odwołanie do wygenerowanego zestawu tymczasowego jest dostarczane do <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> momentu jego uruchomienia, co zezwala na [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] pliki, których kompilacja została odroczona w pierwszym przejściu kompilacji znaczników do teraz, w formacie binarnym.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak za pomocą <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> zadania wykonać drugą kompilację.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass2"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MarkupCompilePass2Task">  
    <MarkupCompilePass2   
      AssemblyName="WPFMSBuildSample"  
      Language="C#"  
      OutputType="WinExe"  
      OutputPath="obj\Debug\"  
      References=".\obj\debug\WPFMSBuildSample.exe;c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />  
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
