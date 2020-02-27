---
title: MarkupCompilePass1 — zadanie | Microsoft Docs
ms.date: 11/04/2016
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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a847f096edf5e42623cb2cb32cf4fd871a89aad7
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633515"
---
# <a name="markupcompilepass1-task"></a>MarkupCompilePass1, zadanie

Zadanie <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> konwertuje nielokalizowalne pliki projektu XAML na skompilowany format binarny.

## <a name="task-parameters"></a>Parametry zadania

| Parametr | Opis |
| - | - |
| `AllGeneratedFiles` | Opcjonalny parametr wyjściowy **ITaskItem []** .<br /><br /> Zawiera kompletną listę plików, które są generowane przez zadanie <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>. |
| `AlwaysCompileMarkupFilesInSeparateDomain` | Opcjonalny parametr **logiczny** .<br /><br /> Określa, czy zadanie ma zostać uruchomione w osobnym <xref:System.AppDomain>. Jeśli ten parametr zwraca **wartość false**, zadanie jest uruchamiane w tym samym <xref:System.AppDomain> jak MSBuild i działa szybciej. Jeśli parametr zwraca **wartość true**, zadanie jest uruchamiane w drugim <xref:System.AppDomain>, który jest odizolowany od MSBuild i działa wolniej. |
| `ApplicationMarkup` | Opcjonalny parametr **ITaskItem []** .<br /><br /> Określa nazwę pliku języka XAML definicji aplikacji. |
| `AssembliesGeneratedDuringBuild` | Opcjonalny parametr **String []** .<br /><br /> Określa odwołania do zestawów, które zmieniają się w procesie kompilacji. Na przykład rozwiązanie programu Visual Studio może zawierać jeden projekt, który odwołuje się do skompilowanych danych wyjściowych innego projektu. W takim przypadku skompilowane dane wyjściowe drugiego projektu można dodać do parametru **AssembliesGeneratedDuringBuild** .<br /><br /> Uwaga: parametr **AssembliesGeneratedDuringBuild** musi zawierać odwołania do kompletnego zestawu zestawów, które są generowane przez rozwiązanie kompilacji. |
| `AssemblyName` | Wymagany parametr **ciągu** .<br /><br /> Określa krótką nazwę zestawu, który jest generowany dla projektu. Na przykład jeśli projekt generuje plik wykonywalny systemu Windows o nazwie *WinExeAssembly. exe*, parametr **AssemblyName** ma wartość **WinExeAssembly**. |
| `AssemblyPublicKeyToken` | Opcjonalny parametr **ciągu** .<br /><br /> Określa token klucza publicznego dla zestawu. |
| `AssemblyVersion` | Opcjonalny parametr **ciągu** .<br /><br /> Określa numer wersji zestawu. |
| `ContentFiles` | Opcjonalny parametr **ITaskItem []** .<br /><br /> Określa listę luźnych plików zawartości. |
| `DefineConstants` | Opcjonalny parametr **ciągu** .<br /><br /> Określa, że jest zachowywana bieżąca wartość **DefineConstants**. co ma wpływ na generowanie zestawu docelowego; Jeśli ten parametr zostanie zmieniony, publiczny interfejs API w zestawie docelowym może zostać zmieniony i będzie to miało miejsce kompilacja plików XAML odwołujących się do typów lokalnych. |
| `ExtraBuildControlFiles` | Opcjonalny parametr **ITaskItem []** .<br /><br /> Określa listę plików, które kontrolują, czy Odbudowywanie jest wyzwalane po ponownym uruchomieniu zadania <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>; ponowne kompilowanie jest wyzwalane, jeśli jeden z tych plików ulegnie zmianie. |
| `GeneratedBamlFiles` | Opcjonalny parametr wyjściowy **ITaskItem []** .<br /><br /> Zawiera listę wygenerowanych plików w formacie binarnym XAML. |
| `GeneratedCodeFiles` | Opcjonalny parametr wyjściowy **ITaskItem []** .<br /><br /> Zawiera listę wygenerowanych plików kodu zarządzanego. |
| `GeneratedLocalizationFiles` | Opcjonalny parametr wyjściowy **ITaskItem []** .<br /><br /> Zawiera listę plików lokalizacji, które zostały wygenerowane dla każdego lokalizowalnego pliku XAML. |
| `HostInBrowser` | Opcjonalny parametr **ciągu** .<br /><br /> Określa, czy wygenerowany zestaw jest aplikacją przeglądarki XAML (XBAP). Prawidłowe opcje to **true** i **false**. Jeśli **wartość jest równa true**, kod jest generowany do obsługi hostingu w przeglądarce. |
| `KnownReferencePaths` | Opcjonalny parametr **String []** .<br /><br /> Określa odwołania do zestawów, które nie są zmieniane podczas procesu kompilacji. Zawiera zestawy, które znajdują się w globalnej pamięci podręcznej zestawów (GAC), w katalogu instalacyjnym platformy .NET i tak dalej. |
| `Language` | Wymagany parametr **ciągu** .<br /><br /> Określa język zarządzany obsługiwany przez kompilator. Prawidłowe opcje to **C#** , **VB**, **JScript**i **C++** . |
| `LanguageSourceExtension` | Opcjonalny parametr **ciągu** .<br /><br /> Określa rozszerzenie, które jest dołączone do rozszerzenia wygenerowanego pliku kodu zarządzanego:<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> Jeśli parametr **LanguageSourceExtension** nie jest ustawiony z określoną wartością, używane jest domyślne rozszerzenie nazwy pliku źródłowego dla języka: *. vb* dla Visual Basic, *. CSharp* dla C#. |
| `LocalizationDirectivesToLocFile` | Opcjonalny parametr **ciągu** .<br /><br /> Określa sposób generowania informacji o lokalizacji dla każdego źródłowego pliku XAML. Prawidłowe opcje to **none**, **CommentsOnly**i **All**. |
| `OutputPath` | Wymagany parametr **ciągu** .<br /><br /> Określa katalog, w którym generowane są pliki generowanego kodu zarządzanego i pliki binarne w formacie XAML. |
| `OutputType` | Wymagany parametr **ciągu** .<br /><br /> Określa typ zestawu, który jest generowany przez projekt. Prawidłowe opcje to **winexe**, **exe**, **Library**i **module**. |
| `PageMarkup` | Opcjonalny parametr **ITaskItem []** .<br /><br /> Określa listę plików XAML do przetworzenia. |
| `References` | Opcjonalny parametr **ITaskItem []** .<br /><br /> Określa listę odwołań z plików do zestawów, które zawierają typy, które są używane w plikach XAML. |
| `RequirePass2ForMainAssembly` | Opcjonalny parametr wyjściowy **wartości logicznej** .<br /><br /> Wskazuje, czy projekt zawiera nielokalizowalne pliki XAML odwołujące się do lokalnych typów, które są osadzone w zestawie głównym. |
| `RequirePass2ForSatelliteAssembly` | Opcjonalny parametr wyjściowy **wartości logicznej** .<br /><br /> Wskazuje, czy projekt zawiera lokalizowalne pliki XAML odwołujące się do lokalnych typów, które są osadzone w zestawie głównym. |
| `RootNamespace` | Opcjonalny parametr **ciągu** .<br /><br /> Określa główną przestrzeń nazw dla klas, które znajdują się wewnątrz projektu. **RootNamespace** jest również używana jako domyślna przestrzeń nazw wygenerowanego pliku kodu zarządzanego, gdy odpowiedni plik XAML nie zawiera atrybutu `x:Class`. |
| `SourceCodeFiles` | Opcjonalny parametr **ITaskItem []** .<br /><br /> Określa listę plików kodu dla bieżącego projektu. Lista nie zawiera wygenerowanych plików kodu zarządzanego specyficznych dla języka. |
| `UICulture` | Opcjonalny parametr **ciągu** .<br /><br /> Określa zestaw satelicki dla kultury interfejsu użytkownika, w którym są osadzone wygenerowane pliki formatu binarnego XAML. Jeśli **UICulture** nie jest ustawiona, wygenerowane pliki formatu binarnego XAML są osadzone w zestawie głównym. |
| `XAMLDebuggingInformation` | Opcjonalny parametr **logiczny** .<br /><br /> W przypadku **wartości true**informacje diagnostyczne są generowane i uwzględniane w SKOMPILOWANYM języku XAML w celu ułatwienia debugowania. |

## <a name="remarks"></a>Uwagi

Zadanie <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> zwykle kompiluje kod XAML w formacie binarnym i generuje pliki kodu. Jeśli plik XAML zawiera odwołania do typów, które są zdefiniowane w tym samym projekcie, jego kompilacja do formatu binarnego jest odroczona przez **MarkupCompilePass1** do drugiego przebiegu kompilacji znacznika (**MarkupCompilePass2**). Takie pliki muszą mieć odroczoną kompilację, ponieważ muszą czekać, aż zostaną skompilowane typy zdefiniowane lokalnie. Jeśli jednak plik XAML ma atrybut `x:Class`, <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> generuje dla niego plik kodu specyficzny dla języka.

Plik XAML jest Lokalizowalny, jeśli zawiera elementy, które używają `x:Uid` atrybutu:

```xml
<Page x:Class="WPFMSBuildSample.Page1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    x:Uid="Page1Uid"
    >
  ...
</Page>
```

Plik XAML odwołuje się do typu zdefiniowanego lokalnie, gdy deklaruje przestrzeń nazw XML, która używa wartości `clr-namespace`, aby odwołać się do przestrzeni nazw w bieżącym projekcie:

```xml
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

Jeśli dowolny plik XAML jest Lokalizowalny lub odwołuje się do typu zdefiniowanego lokalnie, wymagany jest drugi przebieg kompilacji znacznika, który wymaga uruchomienia [GenerateTemporaryTargetAssembly —](../msbuild/generatetemporarytargetassembly-task.md) , a następnie [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak skonwertować trzy pliki XAML *stron* do plików w formacie binarnym. Element *Strona1* zawiera odwołanie do typu, `Class1`, który znajduje się w głównej przestrzeni nazw projektu, w związku z czym nie jest konwertowany na pliki w formacie binarnym w tym przebiegu kompilacji znaczników. Zamiast tego [GenerateTemporaryTargetAssembly —](../msbuild/generatetemporarytargetassembly-task.md) jest wykonywany i następuje [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).

```xml
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

- [Odwołanie do WPF MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Odwołanie do zadania WPF MSBuild](../msbuild/wpf-msbuild-task-reference.md)
- [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md)
- [Odwołanie do zadania programu MSBuild](../msbuild/msbuild-task-reference.md)
- [Tworzenie aplikacji WPF (WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Omówienie aplikacji przeglądarki XAML w języku WPF](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)