---
title: MarkupCompilePass2 — zadanie | Microsoft Docs
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f239670200a75dc3494b22b9a6aa761b1736119d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592220"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 — zadanie

Zadanie <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> wykonuje kompilację z drugim przekazaniem znaczników na plikach [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)], które odwołują się do typów w tym samym projekcie.

## <a name="task-parameters"></a>Parametry zadania

| Parametr | Opis |
| - | - |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Opcjonalny parametr **logiczny** .<br /><br /> Określa, czy zadanie ma zostać uruchomione w osobnym <xref:System.AppDomain>. Jeśli ten parametr zwraca **wartość false**, zadanie jest uruchamiane w tym samym <xref:System.AppDomain> co [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)]i działa szybciej. Jeśli parametr zwraca **wartość true**, zadanie jest uruchamiane w drugim <xref:System.AppDomain>, który jest odizolowany od [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] i działa wolniej. |
| `AssembliesGeneratedDuringBuild` | Opcjonalny parametr **String []** .<br /><br /> Określa odwołania do zestawów, które zmieniają się w procesie kompilacji. Na przykład rozwiązanie programu Visual Studio może zawierać jeden projekt, który odwołuje się do skompilowanych danych wyjściowych innego projektu. W takim przypadku skompilowane dane wyjściowe drugiego projektu można dodać do **AssembliesGeneratedDuringBuild**.<br /><br /> Uwaga: **AssembliesGeneratedDuringBuild** musi zawierać odwołania do kompletnego zestawu zestawów, które są generowane przez rozwiązanie kompilacji. |
| `AssemblyName` | Wymagany parametr **ciągu** .<br /><br /> Określa krótką nazwę zestawu, który jest generowany dla projektu. Na przykład jeśli projekt generuje [!INCLUDE[TLA#tla_win](../msbuild/includes/tlasharptla_win_md.md)] pliku wykonywalnego, którego nazwa to *WinExeAssembly. exe*, parametr **AssemblyName** ma wartość **WinExeAssembly**. |
| `GeneratedBaml` | Opcjonalny parametr wyjściowy **ITaskItem []** .<br /><br /> Zawiera listę wygenerowanych plików w formacie binarnym [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]. |
| `KnownReferencePaths` | Opcjonalny parametr **String []** .<br /><br /> Określa odwołania do zestawów, które nigdy nie ulegają zmianie podczas procesu kompilacji. Zawiera zestawy, które znajdują się w [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)], w katalogu instalacyjnym [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] i tak dalej. |
| `Language` | Wymagany parametr **ciągu** .<br /><br /> Określa język zarządzany obsługiwany przez kompilator. Prawidłowe opcje to **C#** , **VB**, **JScript**i **C++** . |
| `LocalizationDirectivesToLocFile` | Opcjonalny parametr **ciągu** .<br /><br /> Określa sposób generowania informacji o lokalizacji dla każdego źródłowego pliku [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]. Prawidłowe opcje to **none**, **CommentsOnly**i **All**. |
| `OutputPath` | Wymagany parametr **ciągu** .<br /><br /> Określa katalog, w którym generowane są wygenerowane pliki w formacie binarnym [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]. |
| `OutputType` | Wymagany parametr **ciągu** .<br /><br /> Określa typ zestawu, który jest generowany przez projekt. Prawidłowe opcje to **winexe**, **exe**, **Library**i **module**. |
| `References` | Opcjonalny parametr **ITaskItem []** .<br /><br /> Określa listę odwołań z plików do zestawów, które zawierają typy, które są używane w plikach [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)]. Jedno odwołanie odwołuje się do zestawu, który został wygenerowany przez zadanie <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>, które należy uruchomić przed zadaniem <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>. |
| `RootNamespace` | Opcjonalny parametr **ciągu** .<br /><br /> Określa główną przestrzeń nazw dla klas, które znajdują się wewnątrz projektu. **RootNamespace** jest również używana jako domyślna przestrzeń nazw wygenerowanego pliku kodu zarządzanego, gdy odpowiedni plik [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] nie zawiera atrybutu `x:Class`. |
| `XAMLDebuggingInformation` | Opcjonalny parametr **logiczny** .<br /><br /> W przypadku **wartości true**informacje diagnostyczne są generowane i uwzględniane w skompilowanym [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)], aby pomóc w debugowaniu. |

## <a name="remarks"></a>Uwagi

Przed uruchomieniem programu **MarkupCompilePass2**należy wygenerować tymczasowy zestaw zawierający typy, które są używane przez pliki [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)], dla których zostało odroczone przekazanie kompilacji znaczników. Zestaw tymczasowy jest generowany przez uruchomienie zadania **GenerateTemporaryTargetAssembly —** .

Odwołanie do wygenerowanego zestawu tymczasowego jest zapewnione <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> podczas jego uruchamiania, co umożliwia [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] plików, których kompilacja została odroczona w pierwszym przejściu kompilacji znaczników do teraz, w formacie binarnym.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak za pomocą zadania <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> wykonać drugą kompilację.

```xml
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

## <a name="see-also"></a>Zobacz także

- [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Odwołanie do zadania WPF MSBuild](../msbuild/wpf-msbuild-task-reference.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [Odwołanie do zadania programu MSBuild](../msbuild/msbuild-task-reference.md)
- [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Omówienie aplikacji przeglądarki XAML w języku WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
