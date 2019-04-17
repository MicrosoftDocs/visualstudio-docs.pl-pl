---
title: MarkupCompilePass1 Task | Microsoft Docs
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
ms.openlocfilehash: 5ce5ad99abb356c1b047fb2507be9a08f688b993
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59651438"
---
# <a name="markupcompilepass1-task"></a>MarkupCompilePass1 — Zadanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> Zadań konwertuje niemożliwe do zlokalizowania [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] pliki na skompilowany format binarny projektu.  
  
## <a name="task-parameters"></a>Parametry zadania  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`AllGeneratedFiles`|Opcjonalnie **[] ITaskItem** parametr wyjściowy.<br /><br /> Zawiera pełną listę plików, które są generowane przez <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> zadania.|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|Opcjonalnie **logiczna** parametru.<br /><br /> Określa, czy zadanie ma być uruchamiane w oddzielnej <xref:System.AppDomain>. Jeśli ten parametr zwraca **false**, zadanie jest uruchamiane w tym samym <xref:System.AppDomain> jako [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)] i działa szybciej. Jeśli parametr zwraca **true**, zadanie jest uruchamiane na sekundę <xref:System.AppDomain> jest odizolowana od [!INCLUDE[TLA2#tla_msbuild](../includes/tla2sharptla-msbuild-md.md)] i działa wolniej.|  
|`ApplicationMarkup`|Opcjonalnie **[] ITaskItem** parametru.<br /><br /> Określa nazwę definicji aplikacji [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] pliku.|  
|`AssembliesGeneratedDuringBuild`|Opcjonalnie **String []** parametru.<br /><br /> Określa odwołania do zestawów, które zmieniają się w procesie kompilacji. Na przykład [!INCLUDE[TLA#tla_visualstu2005](../includes/tlasharptla-visualstu2005-md.md)] rozwiązanie może zawierać jeden projekt, który odwołuje się do skompilowanych danych wyjściowych innego projektu. W tym przypadku skompilowanych danych wyjściowych drugi projektu można dodać do **AssembliesGeneratedDuringBuild** parametru.<br /><br /> Uwaga: **AssembliesGeneratedDuringBuild** parametr musi zawierać odwołania do pełnego zestawu zestawów, które są generowane przez rozwiązanie do kompilacji.|  
|`AssemblyName`|Wymagane **ciąg** parametru.<br /><br /> Określa krótką nazwę zestawu, który jest generowany dla projektu. Na przykład, jeśli projekt jest generowanie [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] plik wykonywalny, którego nazwa jest **WinExeAssembly.exe**, **AssemblyName** parametr ma wartość **WinExeAssembly**.|  
|`AssemblyPublicKeyToken`|Opcjonalnie **ciąg** parametru.<br /><br /> Określa token klucza publicznego dla zestawu.|  
|`AssemblyVersion`|Opcjonalnie **ciąg** parametru.<br /><br /> Określa numer wersji zestawu.|  
|`ContentFiles`|Opcjonalnie **[] ITaskItem** parametru.<br /><br /> Określa listę luźne pliki zawartości.|  
|`DefineConstants`|Opcjonalnie **ciąg** parametru.<br /><br /> Określa, że bieżąca wartość **DefineConstants**, są przechowywane. co ma wpływ na Generowanie zestawu docelowego; Jeśli ten parametr zostanie zmieniony, publicznego interfejsu API w zestawie docelowym może być zmieniona i tworzenia [!INCLUDE[TLA2#tla_titlexaml](../includes/tla2sharptla-titlexaml-md.md)] może mieć wpływ na pliki, które lokalne typy odwołań.|  
|`ExtraBuildControlFiles`|Opcjonalnie **[] ITaskItem** parametru.<br /><br /> Określa listę plików, które kontrolują, czy ponownej kompilacji jest wyzwalany, gdy <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> zadanie uruchamia ponownie; ponownej kompilacji jest wyzwalany, gdy pliki te zmiany.|  
|`GeneratedBamlFiles`|Opcjonalnie **[] ITaskItem** parametr wyjściowy.<br /><br /> Zawiera listę plików wygenerowanych w [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] format binarny.|  
|`GeneratedCodeFiles`|Opcjonalnie **[] ITaskItem** parametr wyjściowy.<br /><br /> Zawiera listę plików wygenerowanych kodu zarządzanego.|  
|`GeneratedLocalizationFiles`|Opcjonalnie **[] ITaskItem** parametr wyjściowy.<br /><br /> Zawiera listę plików lokalizacji, które zostały wygenerowane dla każdego Lokalizowalny [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] pliku.|  
|`HostInBrowser`|Opcjonalnie **ciąg** parametru.<br /><br /> Określa, czy wygenerowanego zestawu [!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)]. Prawidłowe opcje to **true** i **false**. Jeśli **true**, generowania kodu do obsługi hostingu przeglądarki.|  
|`KnownReferencePaths`|Opcjonalnie **String []** parametru.<br /><br /> Określa odwołania do zestawów, które nie zmieniają się w procesie kompilacji. Zawiera zestawy, które znajdują się w [!INCLUDE[TLA#tla_gac](../includes/tlasharptla-gac-md.md)]w [!INCLUDE[TLA#tla_netframewk](../includes/tlasharptla-netframewk-md.md)] katalog instalacyjny i tak dalej.|  
|`Language`|Wymagane **ciąg** parametru.<br /><br /> Określa język zarządzanych, obsługiwanych przez kompilator. Prawidłowe opcje to **C#**, **VB**, **JScript**, i **C++**.|  
|`LanguageSourceExtension`|Opcjonalnie **ciąg** parametru.<br /><br /> Określa numer wewnętrzny, który jest dołączany do rozszerzenia pliku wygenerowanego kodu zarządzanego:<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> Jeśli **LanguageSourceExtension** parametr nie jest ustawiony przy użyciu określonej wartości, używane jest domyślne rozszerzenie nazwy pliku źródła dla języka: **.vb** dla [!INCLUDE[TLA#tla_visualb](../includes/tlasharptla-visualb-md.md)], **.csharp** dla [!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)].|  
|`LocalizationDirectivesToLocFile`|Opcjonalnie **ciąg** parametru.<br /><br /> Określa sposób generowania informacji o lokalizacji dla każdego źródła [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] pliku. Prawidłowe opcje to **Brak**, **CommentsOnly**, i **wszystkich**.|  
|`OutputPath`|Wymagane **ciąg** parametru.<br /><br /> Określa katalog, w którym wygenerowany kod plików zarządzanych i [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] generowanych plików binarnych.|  
|`OutputType`|Wymagane **ciąg** parametru.<br /><br /> Określa typ zestawu, który został wygenerowany przez projekt. Prawidłowe opcje to **winexe**, **exe**, **biblioteki**, i **modułu netmodule**.|  
|`PageMarkup`|Opcjonalnie **[] ITaskItem** parametru.<br /><br /> Określa listę [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plików do przetworzenia.|  
|`References`|Opcjonalnie **[] ITaskItem** parametru.<br /><br /> Określa listę odwołań z plików do zestawów zawierających typy, które są używane w [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plików.|  
|`RequirePass2ForMainAssembly`|Opcjonalnie **logiczna** parametr wyjściowy.<br /><br /> Wskazuje, czy projekt zawiera niemożliwe do zlokalizowania [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] pliki odwołujące się do lokalnego typy, które są osadzone w głównym zestawie.|  
|`RequirePass2ForSatelliteAssembly`|Opcjonalnie **logiczna** parametr wyjściowy.<br /><br /> Wskazuje, czy projekt zawiera Lokalizowalny [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] pliki, które odwołują się lokalnego typy, które są osadzone w głównym zestawie.|  
|`RootNamespace`|Opcjonalnie **ciąg** parametru.<br /><br /> Określa przestrzeń nazw korzenia dla klas, które znajdują się wewnątrz projektu. **RootNamespace** jest również używany jako domyślny obszar nazw wygenerowanego kodu zarządzanego pliku, gdy odpowiedni [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plik nie zawiera `x:Class` atrybutu.|  
|`SourceCodeFiles`|Opcjonalnie **[] ITaskItem** parametru.<br /><br /> Określa listę plików kodu dla bieżącego projektu. Lista nie zawiera plików wygenerowanych specyficzny dla języka kodu zarządzanego.|  
|`UICulture`|Opcjonalnie **ciąg** parametru.<br /><br /> Określa zestawu satelickiego dla kultury interfejsu użytkownika, w której wygenerowany [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plików binarnych są osadzone. Jeśli **UICulture** nie ustawiono, wygenerowany [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plików binarnych są osadzone w głównym zestawie.|  
|`XAMLDebuggingInformation`|Opcjonalnie **logiczna** parametru.<br /><br /> Gdy **true**, informacje diagnostyczne jest wygenerowany i zawarty w skompilowanych [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] w celu pomocy w debugowaniu.|  
  
## <a name="remarks"></a>Uwagi  
 <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> Zadania zazwyczaj kompiluje [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] w formacie binarnym i generuje pliki kodu. Jeśli [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plik zawiera odwołania do typów, które są zdefiniowane w tym samym projekcie, jego kompilacji na format binarny zostanie odłożona **markupcompilepass1 —** do drugiego przebiegu kompilacji znaczników ( **Markupcompilepass2 —**). Takie pliki muszą mieć ich kompilacji odroczone, ponieważ ich należy zaczekać na lokalnie zdefiniowanych typów są kompilowane. Jednak jeśli [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plik ma `x:Class` atrybutu <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> generuje plik kodu specyficznego dla języka go.  
  
 A [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plik jest Lokalizowalny, jeśli zawiera on elementy, które używają `x:Uid` atrybutu:  
  
```  
<Page x:Class="WPFMSBuildSample.Page1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    x:Uid="Page1Uid"  
    >  
  ...  
</Page>  
```  
  
 A [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plik odwołuje się do typu lokalnie zdefiniowane, gdy deklaruje [!INCLUDE[TLA#tla_xml](../includes/tlasharptla-xml-md.md)] przestrzeni nazw, która używa `clr-namespace` wartość do odwoływania się do przestrzeni nazw w bieżącym projekcie:  
  
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
  
 Ewentualne [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] możliwych do zlokalizowania, lub pliku odwołuje się do typu lokalnie zdefiniowane, drugi przebieg kompilacji znaczników jest wymagany, które wymagają uruchamiania [generatetemporarytargetassembly —](../msbuild/generatetemporarytargetassembly-task.md) a następnie [ Markupcompilepass2 —](../msbuild/markupcompilepass2-task.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak przekonwertować trzy `Page` [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] plików do plików binarnych. `Page1` zawiera odwołanie do typu, `Class1`, który znajduje się w głównej przestrzeni nazw projektu i w związku z tym, nie jest konwertowana na format binarny pliki w tym przebiegu kompilacji znaczników. Zamiast tego [generatetemporarytargetassembly —](../msbuild/generatetemporarytargetassembly-task.md) jest wykonywany i następuje [markupcompilepass2 —](../msbuild/markupcompilepass2-task.md).  
  
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
 [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)   
 [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)   
 [Kompilowanie aplikacji WPF (WPF)](http://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Aplikacje przeglądarek WPF XAML — omówienie](http://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)
