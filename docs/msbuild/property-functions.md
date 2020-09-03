---
title: Funkcje właściwości | Microsoft Docs
ms.date: 02/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, property functions
ms.assetid: 2253956e-3ae0-4bdc-9d3a-4881dfae4ddb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d98d4069ca510cfbb288b88e0ab52b9cd1eb275d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "84183655"
---
# <a name="property-functions"></a>Funkcje właściwości

Funkcje właściwości to wywołania metod .NET Framework, które są wyświetlane w definicjach właściwości programu MSBuild. W przeciwieństwie do zadań, funkcji właściwości można używać poza obiektami docelowymi i są oceniane przed dowolnymi uruchomieniami docelowym.

Bez używania zadań programu MSBuild można odczytać czas systemowy, porównać ciągi, dopasować wyrażenia regularne i wykonać inne akcje w skrypcie kompilacji. Program MSBuild podejmie próbę przekonwertowania ciągu na liczbę i liczbę na ciąg, a następnie wprowadzi inne konwersje zgodnie z wymaganiami.

Wartości ciągu zwracane z funkcji właściwości mają [znaki specjalne](msbuild-special-characters.md) . Jeśli wartość ma być traktowana tak, jakby była umieszczona bezpośrednio w pliku projektu, należy użyć `$([MSBuild]::Unescape())` do wyznaczenia znaków specjalnych.

Funkcje właściwości są dostępne w .NET Framework 4 i nowszych.

## <a name="property-function-syntax"></a>Składnia funkcji właściwości

Są to trzy rodzaje funkcji właściwości; Każda funkcja ma inną składnię:

- Funkcje właściwości String (Instance)
- Statyczne funkcje właściwości
- Funkcje właściwości programu MSBuild

### <a name="string-property-functions"></a>Funkcje właściwości ciągu

Wszystkie wartości właściwości kompilacji są tylko wartościami ciągu. Można użyć metod String (Instance) do działania na dowolnej wartości właściwości. Na przykład można wyodrębnić nazwę dysku (pierwsze trzy znaki) z właściwości build, która reprezentuje pełną ścieżkę przy użyciu tego kodu:

```
$(ProjectOutputFolder.Substring(0,3))
```

### <a name="static-property-functions"></a>Statyczne funkcje właściwości

W skrypcie kompilacji można uzyskać dostęp do właściwości statycznych i metod wielu klas systemowych. Aby uzyskać wartość właściwości statycznej, należy użyć następującej składni, gdzie \<Class> jest nazwą klasy systemowej i \<Property> jest nazwą właściwości.

```
$([Class]::Property)
```

Na przykład można użyć poniższego kodu, aby ustawić właściwość kompilacji na bieżącą datę i godzinę.

```xml
<Today>$([System.DateTime]::Now)</Today>
```

Aby wywołać metodę statyczną, należy użyć następującej składni, gdzie \<Class> jest nazwą klasy systemowej, \<Method> jest nazwą metody, a ( \<Parameters> ) jest listą parametrów dla metody:

```
$([Class]::Method(Parameters))
```

Na przykład, aby ustawić właściwość kompilacja na nowy identyfikator GUID, można użyć tego skryptu:

```xml
<NewGuid>$([System.Guid]::NewGuid())</NewGuid>
```

W funkcjach właściwości statycznych można użyć dowolnej statycznej metody lub właściwości tych klas systemu:

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

- [System. Environment:: CommandLine](xref:System.Environment.CommandLine*)
- [System. Environment:: ExpandEnvironmentVariables](xref:System.Environment.ExpandEnvironmentVariables*)
- [System. Environment:: GetEnvironmentVariable](xref:System.Environment.GetEnvironmentVariable*)
- [System. Environment:: GetEnvironmentVariables](xref:System.Environment.GetEnvironmentVariables*)
- [System. Environment:: GetFolderPath](xref:System.Environment.GetFolderPath*)
- [System. Environment:: GetLogicalDrives](xref:System.Environment.GetLogicalDrives*)
- [System. IO. Directory:: getreżysers](xref:System.IO.Directory.GetDirectories*)
- [System. IO. Directory:: GetFiles](xref:System.IO.Directory.GetFiles*)
- [System. IO. Directory:: GetLastAccessTime](xref:System.IO.Directory.GetLastAccessTime*)
- [System. IO. Directory:: GetLastWriteTime](xref:System.IO.Directory.GetLastWriteTime*)
- [System. IO. Directory:: GetParent](xref:System.IO.Directory.GetParent*)
- [System. IO. File:: istnieje](xref:System.IO.File.Exists*)
- [System. IO. File:: GetCreationTime](xref:System.IO.File.GetCreationTime*)
- [System. IO. File:: GetAttributes](xref:System.IO.File.GetAttributes*)
- [System. IO. File:: GetLastAccessTime](xref:System.IO.File.GetLastAccessTime*)
- [System. IO. File:: GetLastWriteTime](xref:System.IO.File.GetLastWriteTime*)
- [System. IO. File:: ReadAllText obiektu](xref:System.IO.File.ReadAllText*)

### <a name="calling-instance-methods-on-static-properties"></a>Wywoływanie metod wystąpienia właściwości statycznych

Jeśli uzyskujesz dostęp do właściwości statycznej, która zwraca wystąpienie obiektu, można wywołać metody instancji tego obiektu. Aby wywołać metodę wystąpienia, użyj następującej składni, gdzie \<Class> jest nazwą klasy systemowej, \<Property> jest nazwą właściwości, \<Method> jest nazwą metody, a ( \<Parameters> ) jest listą parametrów dla metody:

```
$([Class]::Property.Method(Parameters))
```

Nazwa klasy musi być w pełni kwalifikowana z przestrzenią nazw.

Na przykład można użyć poniższego kodu, aby ustawić właściwość kompilacja na bieżącą datę dzisiejszą.

```xml
<Today>$([System.DateTime]::Now.ToString('yyyy.MM.dd'))</Today>
```

### <a name="msbuild-property-functions"></a>Funkcje właściwości programu MSBuild

Można uzyskać dostęp do kilku metod statycznych w kompilacji, aby zapewnić obsługę znaków arytmetycznych, koniunkcji logicznej i ucieczki. Dostęp do tych metod uzyskuje się za pomocą następującej składni, gdzie \<Method> jest nazwą metody i ( \<Parameters> ) jest listą parametrów dla metody.

```
$([MSBuild]::Method(Parameters))
```

Aby na przykład dodać dwa właściwości, które mają wartości liczbowe, użyj poniższego kodu.

```
$([MSBuild]::Add($(NumberOne), $(NumberTwo)))
```

Poniżej znajduje się lista funkcji właściwości programu MSBuild:

|Sygnatura funkcji|Opis|
|------------------------|-----------------|
|podwójne dodanie (podwójne a, podwójne b)|Dodaj dwa podwojone.|
|długie dodanie (Long a, Long b)|Dodaj dwa długie.|
|podwójne odejmowanie (podwójne a, podwójne b)|Odejmij dwa podwójnej precyzji.|
|Długa odejmowanie (Long a, Long b)|Odejmij dwie długości.|
|Podwójna pomnóż (podwójna a, Double b)|Pomnóż dwa podwojone.|
|Long pomnóż (Long a, Long b)|Pomnóż dwie długości.|
|podwójne dzielenie (podwójne a, podwójne b)|Podziel dwa podwojone.|
|Długa dzielenie (Long a, Long b)|Podziel dwie długości.|
|podwójne modulo (Double a, Double b)|Dwukrotne dzielenie modulo.|
|długie modulo (Long a, Long b)|Modulo dwa długie.|
|ciąg ucieczki (ciąg niezmieniony)|Wypróbowanie ciągu zgodnie z regułami ucieczki MSBuild.|
|ciąg Unescape (ciąg ucieczki)|Usuń znak ucieczki, zgodnie z regułami ucieczki MSBuild.|
|int bitowego (int First, int Second)|Wykonaj bitowe `OR` od pierwszego i drugiego (pierwszy &#124; sekundę).|
|int BitwiseAnd (int First, int Second)|Wykonaj bitowe `AND` od pierwszego i drugiego (pierwszy & sekundę).|
|int BitwiseXor (int First, int Second)|Wykonaj bitowe `XOR` od pierwszego i drugiego (pierwszy ^ s).|
|int BitwiseNot (najpierw int)|Wykonaj wartość bitową `NOT` (po pierwszej).|
|bool IsOsPlatform (ciąg platformString)|Określ, czy bieżąca platforma systemu operacyjnego to `platformString` . `platformString` musi być członkiem <xref:System.Runtime.InteropServices.OSPlatform> .|
|bool IsOSUnixLike ()|Ma wartość true, jeśli bieżący system operacyjny jest systemem UNIX.|
|String NormalizePath (ciąg parametrów [] ścieżka)|Pobiera kanoniczną pełną ścieżkę podanej ścieżki i zapewnia, że zawiera poprawne znaki separatora katalogów dla bieżącego systemu operacyjnego.|
|String NormalizeDirectory (ciąg parametrów [] ścieżka)|Pobiera kanoniczną pełną ścieżkę do podanego katalogu i zapewnia, że zawiera poprawne znaki separatora katalogów dla bieżącego systemu operacyjnego, przy zapewnieniu, że ma końcowy ukośnik.|
|ciąg EnsureTrailingSlash (ścieżka ciągu)|Jeśli dana ścieżka nie ma końcowego ukośnika, Dodaj ją. Jeśli ścieżka jest pustym ciągiem, nie modyfikuje go.|
|ciąg GetPathOfFileAbove (plik String, ciąg startingDirectory)|Wyszukuje i zwraca pełną ścieżkę do pliku w strukturze katalogów powyżej bieżącej lokalizacji pliku kompilacji lub w zależności od tego `startingDirectory` , czy jest określony.|
|GetDirectoryNameOfFileAbove (ciąg startingDirectory, ciąg fileName)|Znajdź i zwróć katalog pliku w określonym katalogu lub lokalizacji w strukturze katalogów powyżej tego katalogu.|
|String MakeRelative (ciąg basePath, ścieżka ciągu)|Ustawia `path` względem `basePath` . `basePath` musi być katalogiem bezwzględnym. Jeśli `path` nie można nawiązać względem, zostanie zwrócony Verbatim. Podobnie jak w przypadku programu `Uri.MakeRelativeUri` .|
|String ValueOrDefault (ciąg conditionValue, String DefaultValue)|Zwróć ciąg w parametrze "DefaultValue" tylko wtedy, gdy parametr "conditionValue" jest pusty, w przeciwnym razie Zwróć wartość conditionValue.|

## <a name="nested-property-functions"></a>Funkcje właściwości zagnieżdżonych

Można połączyć funkcje właściwości, aby tworzyć bardziej złożone funkcje, jak pokazano w poniższym przykładzie.

```
$([MSBuild]::BitwiseAnd(32, $([System.IO.File]::GetAttributes(tempFile))))
```

Ten przykład zwraca wartość <xref:System.IO.FileAttributes> `Archive` bitu (32 lub 0) pliku dostarczonego przez ścieżkę `tempFile` . Zauważ, że wartości wyliczane danych nie mogą występować według nazwy w ramach funkcji właściwości. Zamiast tego należy użyć wartości liczbowej (32).

Metadane mogą być również wyświetlane w zagnieżdżonych funkcjach właściwości. Aby uzyskać więcej informacji, zobacz Tworzenie [pakietów wsadowych](../msbuild/msbuild-batching.md).

## <a name="msbuild-doestaskhostexist"></a>DoesTaskHostExist MSBuild

`DoesTaskHostExist`Funkcja właściwości w programie MSBuild zwraca, czy host zadania jest aktualnie zainstalowany dla określonych wartości środowiska uruchomieniowego i architektury.

Ta funkcja właściwości ma następującą składnię:

```
$([MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture))
```

## <a name="msbuild-ensuretrailingslash"></a>EnsureTrailingSlash MSBuild

`EnsureTrailingSlash`Funkcja Property w MSBuild dodaje końcowy ukośnik, jeśli jeszcze nie istnieje.

Ta funkcja właściwości ma następującą składnię:

```
$([MSBuild]::EnsureTrailingSlash('$(PathProperty)'))
```

## <a name="msbuild-getdirectorynameoffileabove"></a>GetDirectoryNameOfFileAbove MSBuild

`GetDirectoryNameOfFileAbove`Funkcja właściwości programu MSBuild szuka pliku w katalogach znajdujących się powyżej bieżącego katalogu w ścieżce.

 Ta funkcja właściwości ma następującą składnię:

```
$([MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile))
```

 Poniższy kod jest przykładem tej składni.

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />
```

## <a name="msbuild-getpathoffileabove"></a>GetPathOfFileAbove MSBuild

`GetPathOfFileAbove`Funkcja Property w MSBuild zwraca ścieżkę do określonego pliku, jeśli znajduje się w strukturze katalogów powyżej bieżącego katalogu. Jest on funkcjonalnie równoważny z wywołaniem

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />
```

Ta funkcja właściwości ma następującą składnię:

```
$([MSBuild]::GetPathOfFileAbove(dir.props))
```

## <a name="msbuild-getregistryvalue"></a>GetRegistryValue MSBuild

`GetRegistryValue`Funkcja właściwości programu MSBuild zwraca wartość klucza rejestru. Ta funkcja przyjmuje dwa argumenty, nazwę klucza i nazwę wartości oraz zwraca wartość z rejestru. Jeśli nie określisz nazwy wartości, zwracana jest wartość domyślna.

W poniższych przykładach pokazano, jak ta funkcja jest używana:

```
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value
```

## <a name="msbuild-getregistryvaluefromview"></a>GetRegistryValueFromView MSBuild

`GetRegistryValueFromView`Funkcja właściwości programu MSBuild pobiera dane rejestru systemowego, uwzględniając klucz rejestru, wartość i co najmniej jeden uporządkowany widok rejestru. Klucz i wartość są przeszukiwane w każdym widoku rejestru w kolejności, aż zostaną znalezione.

Składnia tej funkcji właściwości to:

```
[MSBuild]::GetRegistryValueFromView(string keyName, string valueName, object defaultValue, params object[] views)
```

System operacyjny Windows 64-bitowy HKEY_LOCAL_MACHINE obsługuje klucz rejestru **\software\wow6432node** , który przedstawia HKEY_LOCAL_MACHINE widok rejestru **\software** dla aplikacji 32-bitowych.

Domyślnie aplikacja 32-bitowa działająca w emulatorze WOW64 uzyskuje dostęp do widoku rejestru 32-bitowego, a aplikacja 64-bit uzyskuje dostęp do widoku rejestru 64-bitowego.

Dostępne są następujące widoki rejestru:

|Widok rejestru|Definicja|
|-------------------|----------------|
|RegistryView.Registry32|Widok rejestru aplikacji 32-bitowych.|
|RegistryView.Registry64|Widok rejestru aplikacji 64-bitowych.|
|RegistryView. default|Widok rejestru, który jest zgodny z procesem, w którym działa aplikacja.|

Poniżej przedstawiono przykład.

 ```
$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))
```

Pobiera dane **SLRuntimeInstallPath** klucza **ReferenceAssemblies** , najpierw szukając w widoku rejestru 64-bitowego, a następnie w widoku rejestru 32-bitowego.

## <a name="msbuild-makerelative"></a>MakeRelative MSBuild

`MakeRelative`Funkcja właściwości programu MSBuild zwraca ścieżkę względną drugiej ścieżki względem pierwszej ścieżki. Każda ścieżka może być plikiem lub folderem.

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

## <a name="msbuild-valueordefault"></a>ValueOrDefault MSBuild

`ValueOrDefault`Funkcja właściwości programu MSBuild zwraca pierwszy argument, chyba że jest to wartość zerowa lub pusta. Jeśli pierwszy argument ma wartość null lub jest pusty, funkcja zwraca drugi argument.

Poniższy przykład pokazuje, jak ta funkcja jest używana.

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

## <a name="msbuild-condition-functions"></a>Funkcje warunku programu MSBuild

Funkcje `Exists` i `HasTrailingSlash` nie są funkcjami właściwości. Są one dostępne do użycia z `Condition` atrybutem. Zobacz [warunki programu MSBuild](msbuild-conditions.md).

## <a name="see-also"></a>Zobacz też

- [właściwości programu MSBuild](../msbuild/msbuild-properties.md)

- [Omówienie programu MSBuild](../msbuild/msbuild.md)
