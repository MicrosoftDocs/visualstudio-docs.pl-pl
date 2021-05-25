---
title: Funkcje właściwości | Microsoft Docs
description: Dowiedz się, jak używać funkcji właściwości, które są wywołaniami .NET Framework, które pojawiają się w definicjach właściwości programu MSBuild.
ms.custom: SEO-VS-2020
ms.date: 02/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, property functions
ms.assetid: 2253956e-3ae0-4bdc-9d3a-4881dfae4ddb
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7c4a6254f15a4108c525231d0e5e93c6fc71bfb3
ms.sourcegitcommit: d3577395cf016f2836eb5a3c1d496cca6d449baa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/25/2021
ms.locfileid: "110413341"
---
# <a name="property-functions"></a>Funkcje właściwości

Funkcje właściwości to wywołania metod .NET Framework, które pojawiają się w definicjach właściwości programu MSBuild. W przeciwieństwie do zadań, funkcje właściwości mogą być używane poza elementami docelowymi i są oceniane przed każdym przebiegem obiektu docelowego.

Bez korzystania z zadań programu MSBuild można odczytywać czas systemowy, porównywać ciągi, dorównać wyrażeń regularnych i wykonywać inne akcje w skrypcie kompilacji. MsBuild spróbuje przekonwertować ciąg na liczbę i liczbę na ciąg oraz wykonać inne konwersje zgodnie z potrzebami.

Wartości ciągów zwracane z funkcji właściwości mają znaki [specjalne ucieczki.](msbuild-special-characters.md) Jeśli chcesz, aby wartość była traktowana tak, jakby była umieszczana bezpośrednio w pliku projektu, użyj funkcji , aby usunąć znaki `$([MSBuild]::Unescape())` specjalne.

Funkcje właściwości są dostępne w wersji .NET Framework 4 i nowszych.

## <a name="property-function-syntax"></a>Składnia funkcji właściwości

Są to trzy rodzaje funkcji właściwości: Każda funkcja ma inną składnię:

- Funkcje właściwości ciągu (wystąpienia)
- Funkcje właściwości statycznych
- Funkcje właściwości programu MSBuild

### <a name="string-property-functions"></a>Funkcje właściwości ciągu

Wszystkie wartości właściwości kompilacji są po prostu wartościami ciągu. Metody ciągów (wystąpienia) mogą działać na dowolnej wartości właściwości. Na przykład można wyodrębnić nazwę dysku (pierwsze trzy znaki) z właściwości kompilacji, która reprezentuje pełną ścieżkę, przy użyciu tego kodu:

```
$(ProjectOutputFolder.Substring(0,3))
```

### <a name="static-property-functions"></a>Funkcje właściwości statycznych

W skrypcie kompilacji można uzyskać dostęp do statycznych właściwości i metod wielu klas systemowych. Aby uzyskać wartość właściwości statycznej, użyj następującej składni, gdzie to nazwa klasy systemowej i jest \<Class> \<Property> nazwą właściwości .

```
$([Class]::Property)
```

Na przykład można użyć następującego kodu, aby ustawić właściwość kompilacji na bieżącą datę i godzina.

```xml
<Today>$([System.DateTime]::Now)</Today>
```

Aby wywołać metodę statyczną, użyj następującej składni, gdzie jest nazwą klasy systemowej, jest nazwą metody, a ( ) jest listą parametrów \<Class> \<Method> dla metody \<Parameters> :

```
$([Class]::Method(Parameters))
```

Aby na przykład ustawić właściwość kompilacji na nowy identyfikator GUID, możesz użyć tego skryptu:

```xml
<NewGuid>$([System.Guid]::NewGuid())</NewGuid>
```

W funkcjach właściwości statycznych można użyć dowolnej metody statycznej lub właściwości tych klas systemowych:

- <xref:System.Byte?displayProperty=nameWithType>
- <xref:System.Char?displayProperty=nameWithType>
- <xref:System.Convert?displayProperty=nameWithType>
- <xref:System.DateTime?displayProperty=nameWithType>
- <xref:System.Decimal?displayProperty=nameWithType>
- <xref:System.Double?displayProperty=nameWithType>
- <xref:System.Enum?displayProperty=nameWithType>
- <xref:System.Guid?displayProperty=nameWithType>
- <xref:System.Int16?displayProperty=nameWithType>
- <xref:System.Int32?displayProperty=nameWithType>
- <xref:System.Int64?displayProperty=nameWithType>
- <xref:System.IO.Path?displayProperty=nameWithType>
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.OSPlatform?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.RuntimeInformation?displayProperty=nameWithType>
- <xref:System.UInt16?displayProperty=nameWithType>
- <xref:System.UInt32?displayProperty=nameWithType>
- <xref:System.UInt64?displayProperty=nameWithType>
- <xref:System.SByte?displayProperty=nameWithType>
- <xref:System.Single?displayProperty=nameWithType>
- <xref:System.String?displayProperty=nameWithType>
- <xref:System.StringComparer?displayProperty=nameWithType>
- <xref:System.TimeSpan?displayProperty=nameWithType>
- <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>
- <xref:System.UriBuilder?displayProperty=nameWithType>
- <xref:System.Version?displayProperty=nameWithType>
- <xref:Microsoft.Build.Utilities.ToolLocationHelper?displayProperty=nameWithType>

Ponadto można użyć następujących metod statycznych i właściwości:

- [System.Environment::CommandLine](xref:System.Environment.CommandLine*)
- [System.Environment::ExpandEnvironmentVariables](xref:System.Environment.ExpandEnvironmentVariables*)
- [System.Environment::GetEnvironmentVariable](xref:System.Environment.GetEnvironmentVariable*)
- [System.Environment::GetEnvironmentVariables](xref:System.Environment.GetEnvironmentVariables*)
- [System.Environment::GetFolderPath](xref:System.Environment.GetFolderPath*)
- [System.Environment::GetLogicalDrives](xref:System.Environment.GetLogicalDrives*)
- [System.IO.Directory::GetDirectories](xref:System.IO.Directory.GetDirectories*)
- [System.IO.Directory::GetFiles](xref:System.IO.Directory.GetFiles*)
- [System.IO.Directory::GetLastAccessTime](xref:System.IO.Directory.GetLastAccessTime*)
- [System.IO.Directory::GetLastWriteTime](xref:System.IO.Directory.GetLastWriteTime*)
- [System.IO.Directory::GetParent](xref:System.IO.Directory.GetParent*)
- [System.IO.File::Exists](xref:System.IO.File.Exists*)
- [System.IO.File::GetCreationTime](xref:System.IO.File.GetCreationTime*)
- [System.IO.File::GetAttributes](xref:System.IO.File.GetAttributes*)
- [System.IO.File::GetLastAccessTime](xref:System.IO.File.GetLastAccessTime*)
- [System.IO.File::GetLastWriteTime](xref:System.IO.File.GetLastWriteTime*)
- [System.IO.File::ReadAllText](xref:System.IO.File.ReadAllText*)

### <a name="calling-instance-methods-on-static-properties"></a>Wywoływanie metod wystąpień we właściwościach statycznych

Jeśli uzyskujesz dostęp do właściwości statycznej, która zwraca wystąpienie obiektu, możesz wywołać metody wystąpienia tego obiektu. Aby wywołać metodę wystąpienia, użyj następującej składni, gdzie to nazwa klasy systemowej, jest nazwą właściwości, jest nazwą metody, a ( ) jest listą parametrów dla \<Class> \<Property> \<Method> \<Parameters> metody:

```
$([Class]::Property.Method(Parameters))
```

Nazwa klasy musi być w pełni kwalifikowana za pomocą przestrzeni nazw .

Na przykład możesz użyć następującego kodu, aby ustawić właściwość kompilacji na bieżącą datę dzisiaj.

```xml
<Today>$([System.DateTime]::Now.ToString('yyyy.MM.dd'))</Today>
```

### <a name="msbuild-property-functions"></a>Funkcje właściwości programu MSBuild

Można uzyskać dostęp do kilku metod statycznych w kompilacji w celu zapewnienia obsługi znaków arytmetycznych, bitowych i ucieczki. Dostęp do tych metod uzyskuje się przy użyciu następującej składni, gdzie to nazwa metody, a ( ) jest listą \<Method> \<Parameters> parametrów dla metody.

```
$([MSBuild]::Method(Parameters))
```

Aby na przykład dodać dwie właściwości, które mają wartości liczbowe, użyj poniższego kodu.

```
$([MSBuild]::Add($(NumberOne), $(NumberTwo)))
```

Oto lista funkcji właściwości programu MSBuild:

|Podpis funkcji|Opis|
|------------------------|-----------------|
|double Add(double a, double b)|Dodaj dwa dublety.|
|long Add(long a, long b)|Dodaj dwie długości.|
|double Subtract(double a, double b)|Odejmij dwa podwójne liczby.|
|long Subtract(long a, long b)|Odejmij dwie długości.|
|double Multiply(double a, double b)|Pomnóż dwa dublety.|
|long Multiply(long a, long b)|Pomnóż dwie długości.|
|double Divide(double a, double b)|Podziel dwa dublety.|
|long Divide(long a, long b)|Podziel dwie długości.|
|double Modulo(double a, double b)|Modulo dwa podwójne.|
|long Modulo(long a, long b)|Modulo dwa długie.|
|string Escape(string unescaped)|Znak ucieczki dla ciągu zgodnie z regułami ucieczki programu MSBuild.|
|string Unescape(ciąg wymyka się)|Unescape ciągu zgodnie z regułami ucieczki MSBuild.|
|int BitwiseOr(int first, int second)|Wykonaj bitowe na `OR` pierwszej i drugiej (pierwsza &#124; sekundy).|
|int BitwiseAnd(int first, int second)|Wykonaj bitowe na `AND` pierwszej i drugiej (pierwsza & sekundy).|
|int BitwiseXor(int first, int second)|Wykonaj bitowe na `XOR` pierwszej i drugiej (pierwsza ^ sekunda).|
|int BitwiseNot(int first)|Wykonaj bitowe `NOT` (~first).|
|bool IsOsPlatform(string platformString)|Określ, czy bieżąca platforma systemu operacyjnego to `platformString` . `platformString` musi być członkiem <xref:System.Runtime.InteropServices.OSPlatform> .|
|bool IsOSUnixLike()|Wartość true, jeśli bieżący system operacyjny jest systemem Unix.|
|string NormalizePath(params string[] path)|Pobiera kanoniczną pełną ścieżkę podanej ścieżki i zapewnia, że zawiera ona poprawne znaki separatora katalogu dla bieżącego systemu operacyjnego.|
|string NormalizeDirectory(params string[] path)|Pobiera kanoniczną pełną ścieżkę podanego katalogu i zapewnia, że zawiera poprawne znaki separatora katalogu dla bieżącego systemu operacyjnego przy jednoczesnym upewnienie się, że ma końcowego ukośnika.|
|string EnsureTrailingSlash(ścieżka ciągu)|Jeśli podana ścieżka nie ma końcowego ukośnika, dodaj go. Jeśli ścieżka jest ciągiem pustym, element nie modyfikuje go.|
|string GetPathOfFileAbove(plik ciągu, ciąg startingDirectory)|Wyszukuje i zwraca pełną ścieżkę do pliku w strukturze katalogów powyżej bieżącej lokalizacji pliku kompilacji lub na podstawie `startingDirectory` wartości , jeśli została określona.|
|GetDirectoryNameOfFileAbove(ciąg startingDirectory, ciąg fileName)|Znajdź i zwróć katalog pliku w określonym katalogu lub lokalizacji w strukturze katalogów powyżej tego katalogu.|
|string MakeRelative(string basePath, ścieżka ciągu)|Sprawia, `path` że są względne względem `basePath` . `basePath` musi być katalogiem bezwzględnym. Jeśli `path` nie można zrobić względnie, jest zwracany dosłowny czas. Podobnie jak w przypadku . `Uri.MakeRelativeUri`|
|string ValueOrDefault(string conditionValue, string defaultValue)|Zwróć ciąg w parametrze "defaultValue" tylko wtedy, gdy parametr "conditionValue" jest pusty. W innym przypadku należy zwrócić wartość conditionValue.|

## <a name="nested-property-functions"></a>Funkcje właściwości zagnieżdżonych

Funkcje właściwości można łączyć w celu postaci bardziej złożonych funkcji, jak pokazano w poniższym przykładzie.

```
$([MSBuild]::BitwiseAnd(32, $([System.IO.File]::GetAttributes(tempFile))))
```

Ten przykład zwraca wartość <xref:System.IO.FileAttributes> `Archive` bitu (32 lub 0) pliku podanego przez ścieżkę `tempFile` . Zauważ, że wyliczane wartości danych nie mogą być wyświetlane według nazwy w funkcjach właściwości. Zamiast tego należy użyć wartości liczbowej (32).

Metadane mogą być również wyświetlane w funkcjach właściwości zagnieżdżonych. Aby uzyskać więcej informacji, zobacz [Batching (Przetwarzanie wsadowe).](../msbuild/msbuild-batching.md)

## <a name="msbuild-doestaskhostexist"></a>MSBuild DoesTaskHostExist

Funkcja właściwości w programie MSBuild zwraca, czy host zadań jest obecnie zainstalowany dla określonych wartości `DoesTaskHostExist` środowiska uruchomieniowego i architektury.

Ta funkcja właściwości ma następującą składnię:

```
$([MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture))
```

## <a name="msbuild-ensuretrailingslash"></a>MSBuild EnsureTrailingSlash

Funkcja property w programie MSBuild dodaje ukośnik na końcowej `EnsureTrailingSlash` trasie, jeśli jeszcze nie istnieje.

Ta funkcja właściwości ma następującą składnię:

```
$([MSBuild]::EnsureTrailingSlash('$(PathProperty)'))
```

## <a name="msbuild-getdirectorynameoffileabove"></a>MSBuild GetDirectoryNameOfFileAbove

Funkcja właściwości `GetDirectoryNameOfFileAbove` MSBuild wyszukuje plik w katalogach powyżej bieżącego katalogu w ścieżce .

 Ta funkcja właściwości ma następującą składnię:

```
$([MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile))
```

 Poniższy kod jest przykładem tej składni.

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />
```

## <a name="msbuild-getpathoffileabove"></a>MSBuild GetPathOfFileAbove

Funkcja property w programie MSBuild zwraca ścieżkę określonego pliku, jeśli znajduje się w strukturze `GetPathOfFileAbove` katalogów powyżej bieżącego katalogu. Jest funkcjonalnie odpowiednikiem wywołania

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />
```

Ta funkcja właściwości ma następującą składnię:

```
$([MSBuild]::GetPathOfFileAbove(dir.props))
```

## <a name="msbuild-getregistryvalue"></a>MSBuild GetRegistryValue

Funkcja właściwości `GetRegistryValue` MSBuild zwraca wartość klucza rejestru. Ta funkcja przyjmuje dwa argumenty: nazwę klucza i nazwę wartości i zwraca wartość z rejestru. Jeśli nie określisz nazwy wartości, zostanie zwrócona wartość domyślna.

W poniższych przykładach podano, jak ta funkcja jest używana:

```
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value
```

## <a name="msbuild-getregistryvaluefromview"></a>MSBuild GetRegistryValueFromView

Funkcja właściwości programu MSBuild pobiera dane rejestru systemu na podany klucz rejestru, wartość i co najmniej jeden `GetRegistryValueFromView` uporządkowany widok rejestru. Klucz i wartość są przeszukiwane w każdym widoku rejestru w kolejności do momentu ich wyszukania.

Składnia tej funkcji właściwości jest następująca:

```
[MSBuild]::GetRegistryValueFromView(string keyName, string valueName, object defaultValue, params object[] views)
```

64-bitowy system operacyjny Windows obsługuje klucz **rejestruHKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node,**  który przedstawiaHKEY_LOCAL_MACHINE\SOFTWARErejestru dla aplikacji 32-bitowych.

Domyślnie aplikacja 32-bitowa uruchomiona na platformie WOW64 uzyskuje dostęp do 32-bitowego widoku rejestru, a aplikacja 64-bitowa uzyskuje dostęp do widoku rejestru 64-bitowego.

Dostępne są następujące widoki rejestru:

|Widok rejestru|Definicja|
|-------------------|----------------|
|RegistryView.Registry32|32-bitowy widok rejestru aplikacji.|
|RegistryView.Registry64|64-bitowy widok rejestru aplikacji.|
|RegistryView.Default|Widok rejestru, który pasuje do procesu, w których jest uruchomiona aplikacja.|

Poniżej przedstawiono przykład.

 ```
$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))
```

pobiera **dane SLRuntimeInstallPath** klucza **ReferenceAssemblies,** najpierw w widoku rejestru 64-bitowego, a następnie w widoku rejestru 32-bitowego.

## <a name="msbuild-makerelative"></a>MSBuild MakeRelative

Funkcja właściwości `MakeRelative` MSBuild zwraca ścieżkę względną drugiej ścieżki względem pierwszej ścieżki. Każda ścieżka może być plikiem lub folderem.

Ta funkcja właściwości ma następującą składnię:

```
$([MSBuild]::MakeRelative($(FileOrFolderPath1), $(FileOrFolderPath2)))
```

Poniższy kod jest przykładem tej składni.

```xml
<PropertyGroup>
    <Path1>c:\users\</Path1>
    <Path2>c:\users\username\</Path2>
</PropertyGroup>

<Target Name = "Go">
    <Message Text ="$([MSBuild]::MakeRelative($(Path1), $(Path2)))" />
    <Message Text ="$([MSBuild]::MakeRelative($(Path2), $(Path1)))" />
</Target>

<!--
Output:
   username\
   ..\
-->
```

## <a name="msbuild-valueordefault"></a>MSBuild ValueOrDefault

Funkcja właściwości MSBuild zwraca pierwszy argument, chyba że jest `ValueOrDefault` pusty lub ma wartość null. Jeśli pierwszy argument ma wartość null lub jest pusty, funkcja zwraca drugi argument.

W poniższym przykładzie pokazano, jak ta funkcja jest używana.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <Value1>$([MSBuild]::ValueOrDefault('$(UndefinedValue)', 'a'))</Value1>
        <Value2>$([MSBuild]::ValueOrDefault('b', '$(Value1)'))</Value2>
    </PropertyGroup>

    <Target Name="MyTarget">
        <Message Text="Value1 = $(Value1)" />
        <Message Text="Value2 = $(Value2)" />
    </Target>
</Project>

<!--
Output:
  Value1 = a
  Value2 = b
-->
```

## <a name="msbuild-targetframework-and-targetplatform-functions"></a>Funkcje TargetFramework i TargetPlatform programu MSBuild

W msBuild 16.7 i wyższych definiuje się kilka funkcji do obsługi [właściwości TargetFramework i TargetPlatform.](msbuild-target-framework-and-target-platform.md)

|Podpis funkcji|Opis|
|------------------------|-----------------|
|GetTargetFrameworkIdentifier(string targetFramework)|Przeszukaj element TargetFrameworkIdentifier z obiektu TargetFramework.|
|GetTargetFrameworkVersion(string targetFramework)|Przeszukaj element TargetFrameworkVersion z obiektu TargetFramework.|
|GetTargetPlatformIdentifier(string targetFramework)|Prze analizuj element TargetPlatformIdentifier z obiektu TargetFramework.|
|GetTargetPlatformVersion(string targetFramework)|Prze analizuj targetPlatformVersion z TargetFramework.|
|IsTargetFrameworkCompatible(string targetFrameworkTarget, string targetFrameworkCandidate)|Zwróć wartość "True", jeśli docelowa docelowa platforma kandyduje, jest zgodna z tą platformą docelową, a w przeciwnym razie zwraca wartość false.|

W poniższym przykładzie pokazano, jak te funkcje są używane. 

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <Value1>$([MSBuild]::GetTargetFrameworkIdentifier('net5.0-windows7.0'))</Value1>
        <Value2>$([MSBuild]::GetTargetFrameworkVersion('net5.0-windows7.0'))</Value2>
        <Value3>$([MSBuild]::GetTargetPlatformIdentifier('net5.0-windows7.0'))</Value3>
        <Value4>$([MSBuild]::GetTargetPlatformVersion('net5.0-windows7.0'))</Value4>
        <Value5>$([MSBuild]::IsTargetFrameworkCompatible('net5.0-windows', 'net5.0'))</Value5>
    </PropertyGroup>

    <Target Name="MyTarget">
        <Message Text="Value1 = $(Value1)" />
        <Message Text="Value2 = $(Value2)" />
        <Message Text="Value3 = $(Value3)" />
        <Message Text="Value4 = $(Value4)" />
        <Message Text="Value5 = $(Value5)" />
    </Target>
</Project>
```

```output
Value1 = .NETCoreApp
Value2 = 5.0
Value3 = windows
Value4 = 7.0
Value5 = True
```

## <a name="msbuild-version-comparison-functions"></a>Funkcje porównania wersji programu MSBuild

W msBuild 16.5 i wyższych definiuje się kilka funkcji porównywania ciągów reprezentujących wersje.

> [!Note]
> Operatory porównania w warunkach [mogą porównywać `System.Version` ciągi, które](#msbuild-conditions.md#Comparing-versions)mogą być analizowane jako obiekty , ale porównanie może dawać nieoczekiwane wyniki. Preferuj funkcje właściwości.

|Podpis funkcji|Opis|
|------------------------|-----------------|
|VersionEquals(ciąg a, ciąg b)|Zwróć `true` , jeśli wersje są równoważne zgodnie z `a` `b` poniższymi regułami.|
|VersionGreaterThan(ciąg a, ciąg b)|Zwróć `true` wartość , jeśli wersja jest większa niż zgodnie z `a` `b` poniższymi regułami.|
|VersionGreaterThanOrEquals(ciąg a, ciąg b)|Zwróć `true` wartość , jeśli wersja jest większa lub równa zgodnie z `a` `b` poniższymi regułami.|
|VersionLessThan(ciąg a, ciąg b)|Zwróć, `true` jeśli wersja jest mniejsza niż zgodnie z `a` `b` poniższymi regułami.|
|VersionLessThanOrEquals(ciąg a, ciąg b)|Zwróć, `true` jeśli wersja jest mniejsza lub równa zgodnie z `a` `b` poniższymi regułami.|
|VersionNotEquals(ciąg a, ciąg b)|Zwróć `false` wartości , jeśli wersje i są równoważne zgodnie z `a` `b` poniższymi regułami.|

W tych metodach wersje są analizowane jak <xref:System.Version?displayProperty=fullName> , z następującymi wyjątkami:

* Wiodące `v` lub `V` są ignorowane, co umożliwia porównywanie z `$(TargetFrameworkVersion)` .

* Wszystko od pierwszego "-" lub "+" do końca ciągu wersji jest ignorowane. Umożliwia to przekazywanie wersji semantycznych (semver), chociaż kolejność nie jest taka sama jak w przypadku semver. Zamiast tego specyfikatory wytłaczania wstępnego i metadane kompilacji nie mają żadnej wagi sortowania. Może to być przydatne, na przykład włączenie funkcji dla elementu i włączenie `>= x.y` jej w funkcji `x.y.z-pre` .

* Nieokreślone części są takie same jak części o wartości zerowej. (`x == x.0 == x.0.0 == x.0.0.0`).

* Białe znaki nie są dozwolone w składnikach liczb całkowitych.

* Tylko wersja główna jest prawidłowa ( `3` jest równa `3.0.0.0` )

* `+` nie jest dozwolone jako składniki liczby całkowitej znaku dodatniego (jest traktowane jako metadane semver i ignorowane)

> [!TIP]
> Porównania właściwości [TargetFramework powinny zazwyczaj](msbuild-target-framework-and-target-platform.md) używać właściwości [IsTargetFrameworkCompatible](#MSBuild-TargetFramework-and-TargetPlatform-functions) zamiast wyodrębniania i porównywania wersji. Dzięki temu można porównać wersje, które różnią się `TargetFramework` `TargetFrameworkIdentifier` w zależności od wersji.

## <a name="msbuild-condition-functions"></a>Funkcje warunku programu MSBuild

Funkcje i `Exists` `HasTrailingSlash` nie są funkcjami właściwości. Są one dostępne do użycia z `Condition` atrybutem . Zobacz [warunki programu MSBuild.](msbuild-conditions.md)

## <a name="see-also"></a>Zobacz też

- [właściwości programu MSBuild](../msbuild/msbuild-properties.md)

- [Omówienie programu MSBuild](../msbuild/msbuild.md)
