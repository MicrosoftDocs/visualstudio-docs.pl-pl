---
title: Zadanie generowaniaTemporaryTargetAssembly | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634048"
---
# <a name="generatetemporarytargetassembly-task"></a>Generowanie zadania DatatemporaryTargetAssembly

Zadanie <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> generuje zestaw, jeśli co najmniej jedna strona XAML w projekcie odwołuje się do typu, który jest zadeklarowany lokalnie w tym projekcie. Wygenerowany zestaw jest usuwany po zakończeniu procesu kompilacji lub jeśli proces kompilacji zakończy się niepowodzeniem.

## <a name="task-parameters"></a>Parametry zadania

| Parametr | Opis |
|--------------------------| - |
| `AssemblyName` | Wymagany parametr **String.**<br /><br /> Określa krótką nazwę zestawu, który jest generowany dla projektu i jest również nazwą zestawu docelowego, który jest tymczasowo generowany. Na przykład jeśli projekt generuje plik wykonywalny systemu Windows, którego nazwa to *WinExeAssembly.exe*, **parametr AssemblyName** ma wartość **WinExeAssembly**. |
| `CompileTargetName` | Wymagany parametr **String.**<br /><br /> Określa nazwę obiektu docelowego MSBuild, który jest używany do generowania zestawów z plików kodu źródłowego. Typową wartością **dla CompileTargetName** jest **CoreCompile**. |
| `CompileTypeName` | Wymagany parametr **String.**<br /><br /> Określa typ kompilacji wykonywanej przez obiekt docelowy określony przez parametr **CompileTargetName.** Dla **celu CoreCompile** ta wartość jest **Compile**. |
| `CurrentProject` | Wymagany parametr **String.**<br /><br /> Określa pełną ścieżkę pliku projektu MSBuild dla projektu, który wymaga tymczasowego zestawu docelowego. |
| `GeneratedCodeFiles` | Opcjonalny parametr **ITaskItem[].**<br /><br /> Określa listę plików kodu zarządzanego specyficznego dla języka, które zostały wygenerowane przez zadanie [MarkupCompilePass1.](../msbuild/markupcompilepass1-task.md) |
| `IntermediateOutputPath` | Wymagany parametr **String.**<br /><br /> Określa katalog, do który jest generowany tymczasowy zestaw docelowy. |
| `MSBuildBinPath` | Wymagany parametr **String.**<br /><br /> Określa lokalizację *pliku MSBuild.exe*, która jest wymagana do skompilowania tymczasowego zestawu docelowego. |
| `ReferencePath` | Opcjonalny parametr **ITaskItem[].**<br /><br /> Określa listę zestawów według ścieżki i nazwy pliku, do których odwołują się typy skompilowane w tymczasowym zestawie docelowym. |
| `ReferencePathTypeName` | Wymagany parametr **String.**<br /><br /> Określa parametr używany przez parametr kompilacji (**CompileTargetName**), który określa listę odwołań do złożenia (**ReferencePath**). Odpowiednią wartością jest **ReferencePath**. |

## <a name="remarks"></a>Uwagi

Pierwszy przebieg kompilacji znaczników, który jest uruchamiany przez [MarkupCompilePass1,](../msbuild/markupcompilepass1-task.md)kompiluje pliki XAML do formatu binarnego. W związku z tym kompilator potrzebuje listy zestawów, do których istnieje odwołanie, które zawierają typy, które są używane przez pliki XAML. Jeśli jednak plik XAML używa typu zdefiniowanego w tym samym projekcie, odpowiedni zestaw dla tego projektu nie jest tworzony, dopóki projekt nie zostanie utworzony. W związku z tym odwołanie do zestawu nie można podać podczas pierwszego przebiegu kompilacji znaczników.

Zamiast tego **MarkupCompilePass1** odpiera konwersję plików XAML, które zawierają odwołania do typów w tym samym projekcie do drugiego przebiegu kompilacji znaczników, który jest wykonywany przez [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md). Przed **wykonaniem MarkupCompilePass2** generowany jest zestaw tymczasowy. Ten zestaw zawiera typy, które są używane przez pliki XAML, których przebieg kompilacji znaczników został odroczony. Odwołanie do wygenerowanego zestawu jest dostarczane do **MarkupCompilePass2,** gdy jest uruchamiany, aby umożliwić odroczone kompilacji plików XAML, które mają być konwertowane do formatu binarnego.

## <a name="example"></a>Przykład

Poniższy przykład generuje zestaw tymczasowy, ponieważ *Page1.xaml* zawiera odwołanie do typu, który znajduje się w tym samym projekcie.

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
- [Odwołanie do zadania](../msbuild/wpf-msbuild-task-reference.md)
- [Odwołanie do budynku MSBuild](../msbuild/msbuild-reference.md)
- [Odwołanie do zadania](../msbuild/msbuild-task-reference.md)
- [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Omówienie aplikacji przeglądarki WPF XAML](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
