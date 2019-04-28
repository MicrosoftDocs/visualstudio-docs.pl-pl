---
title: MarkupCompilePass2 Task | Microsoft Docs
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d929abc6581bf77dfd6ff5cf8b23d450a78a6f6c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62817355"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 — zadanie

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> Zadanie przeprowadza korektę znaczników kompilacji na [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] pliki, które odwołują się typy w tym samym projekcie.

## <a name="task-parameters"></a>Parametry zadania

| Parametr | Opis |
| - | - |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Opcjonalnie **logiczna** parametru.<br /><br /> Określa, czy zadanie ma być uruchamiane w oddzielnej <xref:System.AppDomain>. Jeśli ten parametr zwraca **false**, zadanie jest uruchamiane w tym samym <xref:System.AppDomain> jako [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)], i działa szybciej. Jeśli parametr zwraca **true**, zadanie jest uruchamiane na sekundę <xref:System.AppDomain> jest odizolowana od [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] i działa wolniej. |
| `AssembliesGeneratedDuringBuild` | Opcjonalnie **String []** parametru.<br /><br /> Określa odwołania do zestawów, które zmieniają się w procesie kompilacji. Na przykład rozwiązanie programu Visual Studio może zawierać jeden projekt, który odwołuje się do skompilowanych danych wyjściowych innego projektu. W tym przypadku skompilowanych danych wyjściowych drugi projektu można dodać do **AssembliesGeneratedDuringBuild**.<br /><br /> Uwaga: **AssembliesGeneratedDuringBuild** musi zawierać odwołania do pełnego zestawu zestawów, które są generowane przez rozwiązanie do kompilacji. |
| `AssemblyName` | Wymagane **ciąg** parametru.<br /><br /> Określa krótką nazwę zestawu, który jest generowany dla projektu. Na przykład, jeśli projekt jest generowanie [!INCLUDE[TLA#tla_win](../msbuild/includes/tlasharptla_win_md.md)] plik wykonywalny, którego nazwa jest *WinExeAssembly.exe*, **AssemblyName** parametr ma wartość **WinExeAssembly**. |
| `GeneratedBaml` | Opcjonalnie **[] ITaskItem** parametr wyjściowy.<br /><br /> Zawiera listę plików wygenerowanych w [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] format binarny. |
| `KnownReferencePaths` | Opcjonalnie **String []** parametru.<br /><br /> Określa odwołania do zestawów, które nigdy nie zostały zmienione w procesie kompilacji. Zawiera zestawy, które znajdują się w [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)]w [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] katalog instalacyjny i tak dalej. |
| `Language` | Wymagane **ciąg** parametru.<br /><br /> Określa język zarządzanych, obsługiwanych przez kompilator. Prawidłowe opcje to **C#**, **VB**, **JScript**, i **C++**. |
| `LocalizationDirectivesToLocFile` | Opcjonalnie **ciąg** parametru.<br /><br /> Określa sposób generowania informacji o lokalizacji dla każdego źródła [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] pliku. Prawidłowe opcje to **Brak**, **CommentsOnly**, i **wszystkich**. |
| `OutputPath` | Wymagane **ciąg** parametru.<br /><br /> Określa katalog, w którym wygenerowany [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] generowanych plików binarnych. |
| `OutputType` | Wymagane **ciąg** parametru.<br /><br /> Określa typ zestawu, który został wygenerowany przez projekt. Prawidłowe opcje to **winexe**, **exe**, **biblioteki**, i **modułu netmodule**. |
| `References` | Opcjonalnie **[] ITaskItem** parametru.<br /><br /> Określa listę odwołań z plików do zestawów zawierających typy, które są używane w [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] plików. Jedno odwołanie się do zestawu, który został wygenerowany przez <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> zadania, które należy uruchomić przed <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> zadania. |
| `RootNamespace` | Opcjonalnie **ciąg** parametru.<br /><br /> Określa przestrzeń nazw korzenia dla klas, które znajdują się wewnątrz projektu. **RootNamespace** jest również używany jako domyślny obszar nazw wygenerowanego kodu zarządzanego pliku, gdy odpowiedni [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] plik nie zawiera `x:Class` atrybutu. |
| `XAMLDebuggingInformation` | Opcjonalnie **logiczna** parametru.<br /><br /> Gdy **true**, informacje diagnostyczne jest wygenerowany i zawarty w skompilowanych [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] w celu pomocy w debugowaniu. |

## <a name="remarks"></a>Uwagi

Przed uruchomieniem **markupcompilepass2 —**, należy wygenerować tymczasowej zestawu, który zawiera typy, które są używane przez [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] pliki, których kompilacji znaczników — dostęp próbny zostały odłożone. Wygeneruj tymczasowe zestawu, uruchamiając **generatetemporarytargetassembly —** zadania.

Odwołanie do tymczasowego wygenerowanego zestawu został dostarczony do <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> po jego uruchomieniu, dzięki czemu [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] plików, w której Kompilacja została odroczona w pierwszej kompilacji znaczników przekazać teraz być tworzone na format binarny.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> zadania do wykonania drugiej przekazać kompilacji.

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
- [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md)
- [Odwołanie do zadania MSBuild](../msbuild/msbuild-task-reference.md)
- [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Omówienie aplikacji przeglądarki XAML w WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)