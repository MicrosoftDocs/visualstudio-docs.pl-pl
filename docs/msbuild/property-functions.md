---
title: Funkcje właściwości | Dokumenty firmy Microsoft
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
ms.openlocfilehash: bb4c44b4e642ff1137df7f0afe02502224060a64
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79302911"
---
# <a name="property-functions"></a>Funkcje właściwości

Funkcje właściwości są wywołane do .NET Framework metody, które pojawiają się w definicje właściwości MSBuild. W przeciwieństwie do zadań, funkcje właściwości mogą być używane poza obiektami docelowymi i są oceniane przed przebiegiem dowolnego obiektu docelowego.

Bez użycia zadań MSBuild można odczytać czas systemowy, porównać ciągi, dopasować wyrażenia regularne i wykonać inne akcje w skrypcie kompilacji. MSBuild spróbuje przekonwertować ciąg na liczbę i liczbę na ciąg i w razie potrzeby dokonać innych konwersji.

Wartości ciągów zwracane z funkcji właściwości mają znaki specjalne wysunął. [special characters](msbuild-special-characters.md) Jeśli chcesz, aby wartość była traktowana tak, jakby została umieszczona bezpośrednio w pliku projektu, użyj `$([MSBuild]::Unescape())` unescape znaków specjalnych.

Funkcje właściwości są dostępne w ramach .NET Framework 4 i nowszych.

## <a name="property-function-syntax"></a>Składnia funkcji właściwości

Są to trzy rodzaje funkcji właściwości; każda funkcja ma inną składnię:

- Funkcje właściwości Ciąg (wystąpienie)
- Funkcje właściwości statycznych
- Funkcje właściwości MSBuild

### <a name="string-property-functions"></a>Funkcje właściwości string

Wszystkie wartości właściwości kompilacji są tylko wartościami ciągu. Metody ciągu (wystąpienia) można użyć do działania na dowolnej wartości właściwości. Na przykład można wyodrębnić nazwę dysku (pierwsze trzy znaki) z właściwości kompilacji, która reprezentuje pełną ścieżkę przy użyciu tego kodu:

```
$(ProjectOutputFolder.Substring(0,3))
```

### <a name="static-property-functions"></a>Funkcje właściwości statycznych

W skrypcie kompilacji można uzyskać dostęp do właściwości statycznych i metod wielu klas systemowych. Aby uzyskać wartość właściwości statycznej, należy użyć następującej \<składni, gdzie Class> jest \<nazwą klasy systemowej i właściwości> jest nazwą właściwości.

```
$([Class]::Property)
```

Na przykład można użyć następującego kodu, aby ustawić właściwość kompilacji do bieżącej daty i godziny.

```xml
<Today>$([System.DateTime]::Now)</Today>
```

Aby wywołać metodę statyczną, należy użyć \<następującej składni, gdzie Class> \<jest nazwą klasy systemowej, Metoda>\<jest nazwą metody i ( Parametry>) jest listą parametrów dla metody:

```
$([Class]::Method(Parameters))
```

Na przykład, aby ustawić właściwość kompilacji na nowy identyfikator GUID, można użyć tego skryptu:

```xml
<NewGuid>$([System.Guid]::NewGuid())</NewGuid>
```

W funkcjach właściwości statycznych można użyć dowolnej metody statycznej lub właściwości tych klas systemowych:

- System.Bajt
- System.char
- System.Convert
- System.datetime
- System.decimal
- System.double
- System.enum
- System.guid
- System.Int16
- System.Int32
- System.Int64
- Ścieżka system.io.path
- System.math
- System.Runtime.InteropServices.OSPlatform
- Informacje o czasie wykonywania systemu.Runtime.InteropServices.RuntimeInformation
- System.UInt16
- System.UInt32
- System.UInt64
- System.SByte
- System.Single
- System.string
- Układ systemowy.StringComparer
- System.timespan
- System.Text.RegularExpressions.Regex
- System.UriBuilder
- System.Wersja
- Microsoft.Build.Utilities.ToolLocationHelper

Ponadto można użyć następujących metod statycznych i właściwości:

- System.Environment::Linia poleceń
- System.Environment::ExpandEnvironmentVariables
- System.Environment::GetEnvironmentVariable
- System.Environment::GetEnvironmentVariables
- System.Environment::GetFolderPath
- System.Environment::GetLogicalDrives
- Katalog system.IO.Directory::Katalogi get
- Katalog system.IO.Directory::GetFiles
- Katalog system.IO.Directory::GetLastAccessTime
- Katalog system.IO.Directory::GetLastWriteTime
- Katalog system.IO.Directory::GetParent
- Plik System.IO.File::Exists
- Plik system.IO.File::GetCreationTime
- Plik System.IO.File::GetAttributes
- Plik System.IO.File::GetLastAccessTime
- Plik system.IO.File::GetLastWriteTime
- Plik system.IO.File::ReadAllText

### <a name="calling-instance-methods-on-static-properties"></a>Wywoływanie metod wystąpienia właściwości statycznych

Jeśli dostęp do właściwości statycznej, która zwraca wystąpienie obiektu, można wywołać metody wystąpienia tego obiektu. Aby wywołać metodę wystąpienia, należy użyć następującej składni, \<gdzie Class> jest \<nazwą klasy systemowej, Właściwość \<> jest nazwą właściwości, Metoda>\<jest nazwą metody i ( Parametry>) jest listą parametrów dla metody:

```
$([Class]::Property.Method(Parameters))
```

Nazwa klasy musi być w pełni kwalifikowana z przestrzenią nazw.

Na przykład można użyć następującego kodu, aby ustawić właściwość kompilacji do bieżącej daty dzisiaj.

```xml
<Today>$([System.DateTime]::Now.ToString('yyyy.MM.dd'))</Today>
```

### <a name="msbuild-property-functions"></a>Funkcje właściwości MSBuild

Kilka metod statycznych w kompilacji można uzyskać dostęp do zapewnienia obsługi znaków arytmetycznych, logicznych bitowych i escape. Dostęp do tych metod można uzyskać przy \<użyciu następującej składni, gdzie Metoda\<> jest nazwą metody i ( Parametry>) jest lista parametrów dla metody.

```
$([MSBuild]::Method(Parameters))
```

Na przykład, aby dodać razem dwie właściwości, które mają wartości liczbowe, należy użyć następującego kodu.

```
$([MSBuild]::Add($(NumberOne), $(NumberTwo)))
```

Oto lista funkcji właściwości MSBuild:

|Podpis funkcji|Opis|
|------------------------|-----------------|
|podwójne dodawanie (podwójne a, podwójne b)|Dodaj dwa dublety.|
|długi Add (długi a, długi b)|Dodaj dwie długości.|
|podwójne odejmowanie (podwójne a, podwójne b)|Odejmij dwa podwójne.|
|długie odejmowanie (długie a, długie b)|Odejmij dwie długości.|
|podwójne pomnożenie(podwójne a, podwójne b)|Pomnóż dwa dublety.|
|long Multiply (długi a, długi b)|Pomnóż dwie długości.|
|podwójne dzielenie(podwójne a, podwójne b)|Podziel dwa dublety.|
|długi Podział (długi a, długi b)|Podziel dwie długie.|
|podwójne Modulo (podwójne a, podwójne b)|Modulo dwa podwójne.|
|long Modulo (długi a, długi b)|Modulo dwie longs.|
|ciąg Ucieczka(ciąg bez ograniczeń)|Ucieczka ciąg zgodnie z MSBuild uciekających reguł.|
|ciąg Unescape(ciąg zmieniony)|Unescape ciąg zgodnie z MSBuild uciekających reguł.|
|int BitwiseOr (int pierwszy, int drugi)|Wykonaj bitowy `OR` na pierwszym i drugim (pierwszy &#124; drugi).|
|int BitwiseAnd (int pierwszy, int drugi)|Wykonaj bitowy `AND` na pierwszym i drugim (pierwszy & drugi).|
|int BitwiseXor (int pierwszy, int drugi)|Wykonaj bitowy `XOR` na pierwszym i drugim (pierwszy ^ drugi).|
|int BitwiseNot(int pierwszy)|Wykonaj bitowy `NOT` (~pierwszy).|
|bool IsOsPlatform(string platformString)|Określ, czy bieżąca `platformString`platforma systemu operacyjnego jest . `platformString`musi być członkiem <xref:System.Runtime.InteropServices.OSPlatform>.|
|bool IsOSunixLike()|Prawda, jeśli obecny system operacyjny jest systemem Unix.|
|ciąg NormalizePath(params string[] ścieżka)|Pobiera kanonicznie pełną ścieżkę podanej ścieżki i zapewnia, że zawiera poprawne znaki separatora katalogu dla bieżącego systemu operacyjnego.|
|ciąg NormalizeDirectory(params string[] path)|Pobiera kanonicznie pełną ścieżkę dostarczonego katalogu i zapewnia, że zawiera poprawne znaki separatora katalogu dla bieżącego systemu operacyjnego, zapewniając jednocześnie, że ma ukośnik.|
|ciąg EnsureTrailingSlash(ścieżka ciągu)|Jeśli dana ścieżka nie ma końcowego ukośnika, a następnie dodaj jeden. Jeśli ścieżka jest pusty ciąg, nie modyfikuje go.|
|ciąg GetPathOfFileAbove(plik ciągu, uruchamianie ciąguKatalog)|Wyszukuje i zwraca pełną ścieżkę do pliku w strukturze katalogów powyżej `startingDirectory`lokalizacji bieżącego pliku kompilacji lub na podstawie , jeśli określono.|
|GetDirectoryNameOfFileAbove(ciąg startingDirectory, plik ciąguName)|Zlokalizuj i zwróć katalog pliku w określonym katalogu lub lokalizacji w strukturze katalogów powyżej tego katalogu.|
|ciąg MakeRelative(ciąg basePath, ścieżka ciągu)|Sprawia, `path` `basePath`że w stosunku do . `basePath`musi być katalogiem absolutnym. Jeśli `path` nie można zrobić względne, jest zwracany dosłownie. Podobnie `Uri.MakeRelativeUri`jak w .|
|ciąg ValueOrDefault(warunek ciąguWartość, domyślna wartość ciągu)|Zwraca ciąg w parametrze "defaultValue" tylko wtedy, gdy parametr "conditionValue" jest pusty, w przeciwnym razie zwraca wartość conditionValue.|

## <a name="nested-property-functions"></a>Funkcje właściwości zagnieżdżonych

Można połączyć funkcje właściwości, tworząc bardziej złożone funkcje, jak pokazano w poniższym przykładzie.

```
$([MSBuild]::BitwiseAnd(32, $([System.IO.File]::GetAttributes(tempFile))))
```

W tym przykładzie <xref:System.IO.FileAttributes> `Archive` zwraca wartość bitu (32 lub 0) pliku podanego przez ścieżkę `tempFile`. Należy zauważyć, że wyliczone wartości danych nie mogą być wyświetlane według nazwy w ramach funkcji właściwości. Zamiast tego należy użyć wartości liczbowej (32).

Metadane mogą również pojawić się w funkcjach właściwości zagnieżdżonych. Aby uzyskać więcej informacji, zobacz [Batching](../msbuild/msbuild-batching.md).

## <a name="msbuild-doestaskhostexist"></a>MSBuild DoesTaskHostExist

Funkcja `DoesTaskHostExist` właściwości w MSBuild zwraca, czy host zadań jest obecnie zainstalowany dla określonych wartości środowiska wykonawczego i architektury.

Ta funkcja właściwości ma następującą składnię:

```
$([MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture))
```

## <a name="msbuild-ensuretrailingslash"></a>MSBuild EnsureTrailingSlash

Funkcja `EnsureTrailingSlash` właściwości w MSBuild dodaje ukośnik końcowego, jeśli jeszcze nie istnieje.

Ta funkcja właściwości ma następującą składnię:

```
$([MSBuild]::EnsureTrailingSlash('$(PathProperty)'))
```

## <a name="msbuild-getdirectorynameoffileabove"></a>MSBuild GetDirectoryNameOfFileAbove

Funkcja właściwości MSBuild `GetDirectoryNameOfFileAbove` wyszukuje plik w katalogach powyżej bieżącego katalogu w ścieżce.

 Ta funkcja właściwości ma następującą składnię:

```
$([MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile))
```

 Poniższy kod jest przykładem tej składni.

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />
```

## <a name="msbuild-getpathoffileabove"></a>MSBuild GetPathOfFileAbove

Funkcja `GetPathOfFileAbove` właściwości w MSBuild zwraca ścieżkę określonego pliku, jeśli znajduje się w strukturze katalogów powyżej bieżącego katalogu. Jest to funkcjonalnie równoważne

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />
```

Ta funkcja właściwości ma następującą składnię:

```
$([MSBuild]::GetPathOfFileAbove(dir.props))
```

## <a name="msbuild-getregistryvalue"></a>MSBuild GetRegistryValue

Funkcja właściwości MSBuild `GetRegistryValue` zwraca wartość klucza rejestru. Ta funkcja przyjmuje dwa argumenty, nazwę klucza i nazwę wartości i zwraca wartość z rejestru. Jeśli nie określisz nazwy wartości, zwracana jest wartość domyślna.

Poniższe przykłady pokazują, jak ta funkcja jest używana:

```
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value
```

## <a name="msbuild-getregistryvaluefromview"></a>MSBuild GetRegistryValueFromView

Funkcja właściwości MSBuild `GetRegistryValueFromView` pobiera dane rejestru systemowego, biorąc pod uwagę klucz rejestru, wartość i jeden lub więcej uporządkowanych widoków rejestru. Klucz i wartość są przeszukiwane w każdym widoku rejestru w kolejności, aż zostaną znalezione.

Składnia tej funkcji właściwości jest:

```
[MSBuild]::GetRegistryValueFromView(string keyName, string valueName, object defaultValue, params object[] views)
```

64-bitowy system operacyjny Windows zachowuje klucz rejestru **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node,** który przedstawia widok rejestru **HKEY_LOCAL_MACHINE\SOFTWARE** dla aplikacji 32-bitowych.

Domyślnie 32-bitowa aplikacja działająca na WOW64 uzyskuje dostęp do widoku rejestru 32-bitowego, a 64-bitowa aplikacja uzyskuje dostęp do widoku rejestru 64-bitowego.

Dostępne są następujące widoki rejestru:

|Widok rejestru|Definicja|
|-------------------|----------------|
|RegistryView.Registry32|Widok rejestru aplikacji 32-bitowych.|
|RegistryView.Registry64|64-bitowy widok rejestru aplikacji.|
|RegistryView.Default|Widok rejestru, który pasuje do procesu, w który jest uruchomiona aplikacja.|

Poniżej przedstawiono przykład.

 ```
$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))
```

pobiera dane **SLRuntimeInstallPath** **klucza ReferenceAssemblies,** patrząc najpierw w 64-bitowym widoku rejestru, a następnie w widoku rejestru 32-bitowego.

## <a name="msbuild-makerelative"></a>MSBuild MakeRelative

Funkcja właściwości MSBuild `MakeRelative` zwraca względną ścieżkę drugiej ścieżki względem pierwszej ścieżki. Każda ścieżka może być plikiem lub folderem.

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

Funkcja właściwości MSBuild `ValueOrDefault` zwraca pierwszy argument, chyba że jest null lub pusty. Jeśli pierwszy argument ma wartość null lub jest pusty, funkcja zwraca drugi argument.

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

## <a name="see-also"></a>Zobacz też

- [Właściwości MSBuild](../msbuild/msbuild-properties.md)

- [Omówienie usługi MSBuild](../msbuild/msbuild.md)
