---
title: Zadanie MarkupCompilePass2 | Dokumenty firmy Microsoft
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
ms.openlocfilehash: d18bc3638454e2a6b034cd2e35c3a158361a033e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633528"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 — zadanie

Zadanie <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> wykonuje kompilację znaczników drugiego przebiegu w plikach XAML, które odwołują się do typów w tym samym projekcie.

## <a name="task-parameters"></a>Parametry zadania

| Parametr | Opis |
| - | - |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Opcjonalny parametr **logiczny.**<br /><br /> Określa, czy zadanie ma być <xref:System.AppDomain>uruchamiane w osobnym pliku . Jeśli ten parametr zwraca **false**, <xref:System.AppDomain> zadanie jest uruchamiane w taki sam jak MSBuild i działa szybciej. Jeśli parametr zwraca **wartość true,** zadanie <xref:System.AppDomain> jest uruchamiane w sekundę, która jest izolowana od MSBuild i działa wolniej. |
| `AssembliesGeneratedDuringBuild` | Parametr **Opcjonalny ciąg[].**<br /><br /> Określa odwołania do zestawów, które zmieniają się podczas procesu kompilacji. Na przykład rozwiązanie programu Visual Studio może zawierać jeden projekt, który odwołuje się do skompilowanych danych wyjściowych innego projektu. W takim przypadku skompilowane dane wyjściowe drugiego projektu można dodać do **assembliesGeneratedDwingBuild**.<br /><br /> Uwaga: **ZestawyGeneratedDw trakciebuż** musi zawierać odwołania do pełnego zestawu zestawów, które są generowane przez rozwiązanie kompilacji. |
| `AssemblyName` | Wymagany parametr **String.**<br /><br /> Określa krótką nazwę zestawu, który jest generowany dla projektu. Na przykład jeśli projekt generuje plik wykonywalny, którego nazwa to *WinExeAssembly.exe*, **parametr AssemblyName** ma wartość **WinExeAssembly**. |
| `GeneratedBaml` | Opcjonalny parametr **wyjściowy ITaskItem[].**<br /><br /> Zawiera listę wygenerowanych plików w formacie binarnym XAML. |
| `KnownReferencePaths` | Parametr **Opcjonalny ciąg[].**<br /><br /> Określa odwołania do zestawów, które nigdy nie są zmieniane podczas procesu kompilacji. Zawiera zestawy, które znajdują się w globalnej pamięci podręcznej zestawów (GAC), w katalogu instalacji .NET i tak dalej. |
| `Language` | Wymagany parametr **String.**<br /><br /> Określa język zarządzany, który obsługuje kompilator. Prawidłowe opcje to **C#**, **VB,** **JScript**i **C++**. |
| `LocalizationDirectivesToLocFile` | Opcjonalny parametr **String.**<br /><br /> Określa sposób generowania informacji o lokalizacji dla każdego źródłowego pliku XAML. Prawidłowe opcje to **Brak**, **KomentarzeOnly**i **Wszystkie**. |
| `OutputPath` | Wymagany parametr **String.**<br /><br /> Określa katalog, w którym generowane są wygenerowane pliki formatu binarnego XAML. |
| `OutputType` | Wymagany parametr **String.**<br /><br /> Określa typ zestawu, który jest generowany przez projekt. Prawidłowe opcje to **winexe,** **exe,** **library**i **netmodule**. |
| `References` | Opcjonalny parametr **ITaskItem[].**<br /><br /> Określa listę odwołań z plików do zestawów zawierających typy, które są używane w plikach XAML. Jednym z odwołań jest zestaw, <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> który został wygenerowany <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> przez zadanie, które muszą być uruchamiane przed zadaniem. |
| `RootNamespace` | Opcjonalny parametr **String.**<br /><br /> Określa główny obszar nazw dla klas, które znajdują się wewnątrz projektu. **RootNamespace** jest również używany jako domyślny obszar nazw wygenerowanego pliku kodu zarządzanego, gdy odpowiedni plik XAML nie zawiera atrybutu. `x:Class` |
| `XAMLDebuggingInformation` | Opcjonalny parametr **logiczny.**<br /><br /> Gdy **true**, informacje diagnostyczne są generowane i zawarte w skompilowanym XAML w celu ułatwienia debugowania. |

## <a name="remarks"></a>Uwagi

Przed uruchomieniem **MarkupCompilePass2**należy wygenerować zestaw tymczasowy zawierający typy używane przez pliki XAML, których przebieg kompilacji znaczników został odroczony. Generowanie zestawu tymczasowego przez uruchomienie **generateTemporaryTargetAssembly** zadania.

Odwołanie do wygenerowanego zestawu tymczasowego <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> jest dostarczany podczas jego pracy, dzięki czemu pliki XAML, których kompilacja została odroczona w pierwszym przebiegu kompilacji znaczników, są teraz kompilowane do formatu binarnego.

## <a name="example"></a>Przykład

W poniższym przykładzie <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> pokazano, jak użyć zadania do wykonania kompilacji drugiego przebiegu.

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

## <a name="see-also"></a>Zobacz też

- [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Odwołanie do zadania WPF MSBuild](../msbuild/wpf-msbuild-task-reference.md)
- [Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)
- [Odwołanie do zadania MSBuild](../msbuild/msbuild-task-reference.md)
- [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Omówienie aplikacji przeglądarki WPF XAML](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
