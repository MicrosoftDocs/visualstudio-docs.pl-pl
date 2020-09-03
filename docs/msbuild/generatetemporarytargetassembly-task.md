---
title: GenerateTemporaryTargetAssembly — — Zadanie | Microsoft Docs
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69333b87720513244e90c131f052d11099b62e35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77634048"
---
# <a name="generatetemporarytargetassembly-task"></a>GenerateTemporaryTargetAssembly, zadanie

<xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly>Zadanie generuje zestaw, jeśli co najmniej jedna strona XAML w projekcie odwołuje się do typu, który jest zadeklarowany lokalnie w tym projekcie. Wygenerowany zestaw jest usuwany po zakończeniu procesu kompilacji lub w przypadku niepowodzenia procesu kompilacji.

## <a name="task-parameters"></a>Parametry zadania

| Parametr | Opis |
|--------------------------| - |
| `AssemblyName` | Wymagany parametr **ciągu** .<br /><br /> Określa krótką nazwę zestawu, który jest generowany dla projektu i jest również nazwą zestawu docelowego, który jest tymczasowo generowany. Na przykład jeśli projekt generuje plik wykonywalny systemu Windows o nazwie *WinExeAssembly.exe*, parametr **AssemblyName** ma wartość **WinExeAssembly**. |
| `CompileTargetName` | Wymagany parametr **ciągu** .<br /><br /> Określa nazwę obiektu docelowego programu MSBuild, który jest używany do generowania zestawów z plików kodu źródłowego. Typową wartością dla **CompileTargetName** jest **CoreCompile**. |
| `CompileTypeName` | Wymagany parametr **ciągu** .<br /><br /> Określa typ kompilacji wykonywanej przez obiekt docelowy określony przez parametr **CompileTargetName** . Dla elementu docelowego **CoreCompile** ta wartość jest **Kompiluj**. |
| `CurrentProject` | Wymagany parametr **ciągu** .<br /><br /> Określa pełną ścieżkę pliku projektu MSBuild dla projektu, który wymaga tymczasowego zestawu docelowego. |
| `GeneratedCodeFiles` | Opcjonalny parametr **ITaskItem []** .<br /><br /> Określa listę plików kodu zarządzanego specyficznego dla języka, które zostały wygenerowane przez zadanie [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md) . |
| `IntermediateOutputPath` | Wymagany parametr **ciągu** .<br /><br /> Określa katalog, do którego jest generowany tymczasowy zestaw docelowy. |
| `MSBuildBinPath` | Wymagany parametr **ciągu** .<br /><br /> Określa lokalizację *MSBuild.exe*, która jest wymagana do skompilowania tymczasowego zestawu docelowego. |
| `ReferencePath` | Opcjonalny parametr **ITaskItem []** .<br /><br /> Określa listę zestawów, według ścieżki i nazwy pliku, do których odwołują się typy, które są kompilowane do tymczasowego zestawu docelowego. |
| `ReferencePathTypeName` | Wymagany parametr **ciągu** .<br /><br /> Określa parametr, który jest używany przez parametr docelowa kompilacji (**CompileTargetName**), który określa listę odwołań do zestawów (**ReferencePath**). Odpowiednia wartość to **ReferencePath**. |

## <a name="remarks"></a>Uwagi

Pierwszy przebieg kompilacji znacznika, który jest uruchamiany przez [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md), kompiluje pliki XAML w formacie binarnym. W związku z tym kompilator potrzebuje listy przywoływanych zestawów, które zawierają typy, które są używane przez pliki XAML. Jeśli jednak plik XAML używa typu, który jest zdefiniowany w tym samym projekcie, odpowiedni zestaw dla tego projektu nie zostanie utworzony do czasu skompilowania projektu. W związku z tym nie można podać odwołania do zestawu podczas pierwszego przebiegu kompilacji znaczników.

Zamiast tego **MarkupCompilePass1** dokonuje konwersji plików XAML, które zawierają odwołania do typów w tym samym projekcie, do drugiego przebiegu kompilacji znaczników, który jest wykonywany przez [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md). Przed wykonaniem **MarkupCompilePass2** zostaje wygenerowany zestaw tymczasowy. Ten zestaw zawiera typy, które są używane przez pliki XAML, dla których zostało odroczone przekazanie kompilacji znaczników. Odwołanie do wygenerowanego zestawu jest dostarczane do **MarkupCompilePass2** , gdy zostanie uruchomione, aby zezwolić na konwersję odroczonych plików XAML kompilacji na format binarny.

## <a name="example"></a>Przykład

Poniższy przykład generuje zestaw tymczasowy, ponieważ *Strona1. XAML* zawiera odwołanie do typu, który znajduje się w tym samym projekcie.

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

## <a name="see-also"></a>Zobacz też

- [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Dokumentacja zadań](../msbuild/wpf-msbuild-task-reference.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [Dokumentacja zadań](../msbuild/msbuild-task-reference.md)
- [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Omówienie aplikacji przeglądarki XAML w języku WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
