---
title: MarkupCompilePass1 — zadanie | Microsoft Docs
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
- converting XAML to binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], parameters
- converting XAML projects to compiled binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], converting XAML to binary format
ms.assetid: 693d6945-fd6f-4698-8f64-9dfcb71052d3
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dd5a6edc2f89470b4aacf05ef0a416c060cf23df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65703555"
---
# <a name="markupcompilepass1-task"></a>MarkupCompilePass1 — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>Zadanie konwertuje nielokalizowalne [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] pliki projektu na skompilowany format binarny.  
  
## <a name="task-parameters"></a>Parametry zadania  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AllGeneratedFiles`|Opcjonalny parametr wyjściowy **ITaskItem []** .<br /><br /> Zawiera kompletną listę plików, które są generowane przez <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> zadanie.|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|Opcjonalny parametr **logiczny** .<br /><br /> Określa, czy zadanie ma zostać uruchomione w osobnym <xref:System.AppDomain> . Jeśli ten parametr zwraca **wartość false**, zadanie jest uruchamiane w taki sam <xref:System.AppDomain> sposób, jak [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)] i działa szybciej. Jeśli parametr zwraca **wartość true**, zadanie działa w drugim, <xref:System.AppDomain> który jest odizolowany od [!INCLUDE[TLA2#tla_msbuild](../includes/tla2sharptla-msbuild-md.md)] i działa wolniej.|  
|`ApplicationMarkup`|Opcjonalny parametr **ITaskItem []** .<br /><br /> Określa nazwę pliku definicji aplikacji [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] .|  
|`AssembliesGeneratedDuringBuild`|Opcjonalny parametr **String []** .<br /><br /> Określa odwołania do zestawów, które zmieniają się w procesie kompilacji. Na przykład [!INCLUDE[TLA#tla_visualstu2005](../includes/tlasharptla-visualstu2005-md.md)] rozwiązanie może zawierać jeden projekt, który odwołuje się do skompilowanych danych wyjściowych innego projektu. W takim przypadku skompilowane dane wyjściowe drugiego projektu można dodać do parametru **AssembliesGeneratedDuringBuild** .<br /><br /> Uwaga: parametr **AssembliesGeneratedDuringBuild** musi zawierać odwołania do kompletnego zestawu zestawów, które są generowane przez rozwiązanie kompilacji.|  
|`AssemblyName`|Wymagany parametr **ciągu** .<br /><br /> Określa krótką nazwę zestawu, który jest generowany dla projektu. Na przykład jeśli projekt generuje [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] plik wykonywalny, którego nazwa jest **WinExeAssembly.exe**, parametr **AssemblyName** ma wartość **WinExeAssembly**.|  
|`AssemblyPublicKeyToken`|Opcjonalny parametr **ciągu** .<br /><br /> Określa token klucza publicznego dla zestawu.|  
|`AssemblyVersion`|Opcjonalny parametr **ciągu** .<br /><br /> Określa numer wersji zestawu.|  
|`ContentFiles`|Opcjonalny parametr **ITaskItem []** .<br /><br /> Określa listę luźnych plików zawartości.|  
|`DefineConstants`|Opcjonalny parametr **ciągu** .<br /><br /> Określa, że jest zachowywana bieżąca wartość **DefineConstants**. co ma wpływ na generowanie zestawu docelowego; Jeśli ten parametr zostanie zmieniony, publiczny interfejs API w zestawie docelowym może ulec zmianie, a kompilacja [!INCLUDE[TLA2#tla_titlexaml](../includes/tla2sharptla-titlexaml-md.md)] plików odwołująca się do typów lokalnych może być zależna.|  
|`ExtraBuildControlFiles`|Opcjonalny parametr **ITaskItem []** .<br /><br /> Określa listę plików, które kontrolują, czy kompilacja jest wyzwalana, gdy zadanie zostanie ponownie uruchomione <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> ; kompilacja jest wyzwalana po zmianie jednego z tych plików.|  
|`GeneratedBamlFiles`|Opcjonalny parametr wyjściowy **ITaskItem []** .<br /><br /> Zawiera listę wygenerowanych plików w [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] formacie binarnym.|  
|`GeneratedCodeFiles`|Opcjonalny parametr wyjściowy **ITaskItem []** .<br /><br /> Zawiera listę wygenerowanych plików kodu zarządzanego.|  
|`GeneratedLocalizationFiles`|Opcjonalny parametr wyjściowy **ITaskItem []** .<br /><br /> Zawiera listę plików lokalizacji, które zostały wygenerowane dla każdego lokalizowalnego [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] pliku.|  
|`HostInBrowser`|Opcjonalny parametr **ciągu** .<br /><br /> Określa, czy wygenerowany zestaw to [!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)] . Prawidłowe opcje to **true** i **false**. Jeśli **wartość jest równa true**, kod jest generowany do obsługi hostingu w przeglądarce.|  
|`KnownReferencePaths`|Opcjonalny parametr **String []** .<br /><br /> Określa odwołania do zestawów, które nie są zmieniane podczas procesu kompilacji. Zawiera zestawy, które znajdują się w [!INCLUDE[TLA#tla_gac](../includes/tlasharptla-gac-md.md)] , w [!INCLUDE[TLA#tla_netframewk](../includes/tlasharptla-netframewk-md.md)] katalogu instalacyjnym i tak dalej.|  
|`Language`|Wymagany parametr **ciągu** .<br /><br /> Określa język zarządzany obsługiwany przez kompilator. Prawidłowe opcje to **C#**, **VB**, **JScript**i **C++**.|  
|`LanguageSourceExtension`|Opcjonalny parametr **ciągu** .<br /><br /> Określa rozszerzenie, które jest dołączone do rozszerzenia wygenerowanego pliku kodu zarządzanego:<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> Jeśli parametr **LanguageSourceExtension** nie jest ustawiony z określoną wartością, używane jest domyślne rozszerzenie nazwy pliku źródłowego dla języka: **. vb** dla [!INCLUDE[TLA#tla_visualb](../includes/tlasharptla-visualb-md.md)] , **CSharp** dla [!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)] .|  
|`LocalizationDirectivesToLocFile`|Opcjonalny parametr **ciągu** .<br /><br /> Określa, jak generować informacje o lokalizacji dla każdego [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] pliku źródłowego. Prawidłowe opcje to **none**, **CommentsOnly**i **All**.|  
|`OutputPath`|Wymagany parametr **ciągu** .<br /><br /> Określa katalog, w którym generowane są generowane pliki i pliki [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] formatu binarnego kodu zarządzanego.|  
|`OutputType`|Wymagany parametr **ciągu** .<br /><br /> Określa typ zestawu, który jest generowany przez projekt. Prawidłowe opcje to **winexe**, **exe**, **Library**i **module**.|  
|`PageMarkup`|Opcjonalny parametr **ITaskItem []** .<br /><br /> Określa listę [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plików do przetworzenia.|  
|`References`|Opcjonalny parametr **ITaskItem []** .<br /><br /> Określa listę odwołań z plików do zestawów, które zawierają typy, które są używane w [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plikach.|  
|`RequirePass2ForMainAssembly`|Opcjonalny parametr wyjściowy **wartości logicznej** .<br /><br /> Wskazuje, czy projekt zawiera nielokalizowalne [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] pliki, które odwołują się do lokalnych typów, które są osadzone w zestawie głównym.|  
|`RequirePass2ForSatelliteAssembly`|Opcjonalny parametr wyjściowy **wartości logicznej** .<br /><br /> Wskazuje, czy projekt zawiera lokalizowalne [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] pliki, które odwołują się do lokalnych typów, które są osadzone w zestawie głównym.|  
|`RootNamespace`|Opcjonalny parametr **ciągu** .<br /><br /> Określa główną przestrzeń nazw dla klas, które znajdują się wewnątrz projektu. **RootNamespace** jest również używana jako domyślna przestrzeń nazw wygenerowanego pliku kodu zarządzanego, gdy odpowiedni [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plik nie zawiera `x:Class` atrybutu.|  
|`SourceCodeFiles`|Opcjonalny parametr **ITaskItem []** .<br /><br /> Określa listę plików kodu dla bieżącego projektu. Lista nie zawiera wygenerowanych plików kodu zarządzanego specyficznych dla języka.|  
|`UICulture`|Opcjonalny parametr **ciągu** .<br /><br /> Określa zestaw satelicki dla kultury interfejsu użytkownika, w którym [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] są osadzone wygenerowane pliki formatu binarnego. Jeśli **UICulture** nie jest ustawiona, generowane [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] pliki formatu binarnego są osadzone w zestawie głównym.|  
|`XAMLDebuggingInformation`|Opcjonalny parametr **logiczny** .<br /><br /> W przypadku **wartości true**informacje diagnostyczne są generowane i uwzględniane w skompilowanym czasie [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] w celu ułatwienia debugowania.|  
  
## <a name="remarks"></a>Uwagi  
 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>Zadanie zazwyczaj kompiluje [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] w formacie binarnym i generuje pliki kodu. Jeśli [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plik zawiera odwołania do typów, które są zdefiniowane w tym samym projekcie, jego kompilacja do formatu binarnego jest odroczona przez **MarkupCompilePass1** do drugiego przebiegu kompilacji znacznika (**MarkupCompilePass2**). Takie pliki muszą mieć odroczoną kompilację, ponieważ muszą czekać, aż zostaną skompilowane typy zdefiniowane lokalnie. Jeśli jednak [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plik ma `x:Class` atrybut, <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> generuje dla niego plik kodu specyficzny dla języka.  
  
 [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)]Plik jest Lokalizowalny, jeśli zawiera elementy, które używają `x:Uid` atrybutu:  
  
```  
<Page x:Class="WPFMSBuildSample.Page1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    x:Uid="Page1Uid"  
    >  
  ...  
</Page>  
```  
  
 [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)]Plik odwołuje się do typu zdefiniowanego lokalnie, gdy deklaruje [!INCLUDE[TLA#tla_xml](../includes/tlasharptla-xml-md.md)] przestrzeń nazw, która używa `clr-namespace` wartości, aby odwołać się do przestrzeni nazw w bieżącym projekcie:  
  
```  
<Page x:Class="WPFMSBuildSample.Page1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:localNamespace="clr-namespace:WPFMSBuildSample"  
    >  
    <Grid>  
      <Grid.Resources>  
        <localNameSpace:LocalType x:Key="localType" />  
      </Grid.Resources>  
      ...  
    </Grid>  
</Page>  
```  
  
 Jeśli dowolny [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plik jest Lokalizowalny lub odwołuje się do typu zdefiniowanego lokalnie, wymagany jest drugi przebieg kompilacji znacznika, który wymaga uruchomienia [GenerateTemporaryTargetAssembly —](../msbuild/generatetemporarytargetassembly-task.md) , a następnie [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak konwertować trzy `Page` [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] pliki na pliki w formacie binarnym. `Page1` zawiera odwołanie do typu, `Class1` , który znajduje się w głównej przestrzeni nazw projektu i w związku z tym nie jest konwertowane na pliki w formacie binarnym w tym przebiegu kompilacji znaczników. Zamiast tego [GenerateTemporaryTargetAssembly —](../msbuild/generatetemporarytargetassembly-task.md) jest wykonywany i następuje [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass1"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MarkupCompilePass1Task">  
    <MarkupCompilePass1   
      AssemblyName="WPFMSBuildSample"  
      Language="C#"  
      OutputType="WinExe"  
      OutputPath="obj\Debug\"  
      ApplicationMarkup="App.xaml"  
      PageMarkup="Page1.xaml;Page2.xaml;Page3.xaml"  
      SourceCodeFiles="Class1.cs"  
      References="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />  
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
