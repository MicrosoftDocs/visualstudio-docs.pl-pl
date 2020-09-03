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
ms.openlocfilehash: d18bc3638454e2a6b034cd2e35c3a158361a033e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77633528"
---
# <a name="markupcompilepass2-task"></a>MarkupCompilePass2 — zadanie

<xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2>Zadanie wykonuje kompilację drugiego przebiegu znaczników dla plików XAML, które odwołują się do typów w tym samym projekcie.

## <a name="task-parameters"></a>Parametry zadania

| Parametr | Opis |
| - | - |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Opcjonalny parametr **logiczny** .<br /><br /> Określa, czy zadanie ma zostać uruchomione w osobnym <xref:System.AppDomain> . Jeśli ten parametr zwraca **wartość false**, zadanie jest uruchamiane w taki sam <xref:System.AppDomain> sposób jak MSBuild i działa szybciej. Jeśli parametr zwraca **wartość true**, zadanie jest uruchamiane w drugim <xref:System.AppDomain> odizolowanym od programu MSBuild i działa wolniej. |
| `AssembliesGeneratedDuringBuild` | Opcjonalny parametr **String []** .<br /><br /> Określa odwołania do zestawów, które zmieniają się w procesie kompilacji. Na przykład rozwiązanie programu Visual Studio może zawierać jeden projekt, który odwołuje się do skompilowanych danych wyjściowych innego projektu. W takim przypadku skompilowane dane wyjściowe drugiego projektu można dodać do **AssembliesGeneratedDuringBuild**.<br /><br /> Uwaga: **AssembliesGeneratedDuringBuild** musi zawierać odwołania do kompletnego zestawu zestawów, które są generowane przez rozwiązanie kompilacji. |
| `AssemblyName` | Wymagany parametr **ciągu** .<br /><br /> Określa krótką nazwę zestawu, który jest generowany dla projektu. Na przykład jeśli projekt generuje plik wykonywalny, którego nazwa jest *WinExeAssembly.exe*, parametr **AssemblyName** ma wartość **WinExeAssembly**. |
| `GeneratedBaml` | Opcjonalny parametr wyjściowy **ITaskItem []** .<br /><br /> Zawiera listę wygenerowanych plików w formacie binarnym XAML. |
| `KnownReferencePaths` | Opcjonalny parametr **String []** .<br /><br /> Określa odwołania do zestawów, które nigdy nie ulegają zmianie podczas procesu kompilacji. Zawiera zestawy, które znajdują się w globalnej pamięci podręcznej zestawów (GAC), w katalogu instalacyjnym platformy .NET i tak dalej. |
| `Language` | Wymagany parametr **ciągu** .<br /><br /> Określa język zarządzany obsługiwany przez kompilator. Prawidłowe opcje to **C#**, **VB**, **JScript**i **C++**. |
| `LocalizationDirectivesToLocFile` | Opcjonalny parametr **ciągu** .<br /><br /> Określa sposób generowania informacji o lokalizacji dla każdego źródłowego pliku XAML. Prawidłowe opcje to **none**, **CommentsOnly**i **All**. |
| `OutputPath` | Wymagany parametr **ciągu** .<br /><br /> Określa katalog, w którym generowane są generowane pliki binarne w formacie XAML. |
| `OutputType` | Wymagany parametr **ciągu** .<br /><br /> Określa typ zestawu, który jest generowany przez projekt. Prawidłowe opcje to **winexe**, **exe**, **Library**i **module**. |
| `References` | Opcjonalny parametr **ITaskItem []** .<br /><br /> Określa listę odwołań z plików do zestawów, które zawierają typy, które są używane w plikach XAML. Jedno odwołanie odwołuje się do zestawu, który został wygenerowany przez <xref:Microsoft.Build.Tasks.Windows.GenerateTemporaryTargetAssembly> zadanie, które należy uruchomić przed <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> zadaniem. |
| `RootNamespace` | Opcjonalny parametr **ciągu** .<br /><br /> Określa główną przestrzeń nazw dla klas, które znajdują się wewnątrz projektu. **RootNamespace** jest również używana jako domyślna przestrzeń nazw wygenerowanego pliku kodu zarządzanego, gdy odpowiedni plik XAML nie zawiera `x:Class` atrybutu. |
| `XAMLDebuggingInformation` | Opcjonalny parametr **logiczny** .<br /><br /> W przypadku **wartości true**informacje diagnostyczne są generowane i uwzględniane w SKOMPILOWANYM języku XAML w celu ułatwienia debugowania. |

## <a name="remarks"></a>Uwagi

Przed uruchomieniem programu **MarkupCompilePass2**należy wygenerować tymczasowy zestaw zawierający typy, które są używane przez pliki XAML, dla których zostało odroczone przekazanie kompilacji znaczników. Zestaw tymczasowy jest generowany przez uruchomienie zadania **GenerateTemporaryTargetAssembly —** .

Odwołanie do wygenerowanego zestawu tymczasowego jest dostarczane do <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> momentu jego uruchomienia, co zezwala na pliki XAML, których kompilacja została odroczona w pierwszym przejściu kompilacji znaczników do teraz, w formacie binarnym.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak za pomocą <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass2> zadania wykonać drugą kompilację.

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
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [Odwołanie do zadania programu MSBuild](../msbuild/msbuild-task-reference.md)
- [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Omówienie aplikacji przeglądarki XAML w języku WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
