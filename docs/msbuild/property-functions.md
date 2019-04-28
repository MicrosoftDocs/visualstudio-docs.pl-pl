---
title: Funkcje właściwości | Dokumentacja firmy Microsoft
ms.date: 02/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, property functions
ms.assetid: 2253956e-3ae0-4bdc-9d3a-4881dfae4ddb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c94b33fad50cb5e271615629641ea7307f669255
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62788545"
---
# <a name="property-functions"></a>Funkcje właściwości

W wersjach programu .NET Framework 4 i 4.5 funkcji właściwości może służyć do oceny, skryptów programu MSBuild. Funkcje właściwości może służyć wszędzie tam, gdzie są wyświetlane właściwości. W przeciwieństwie do zadań funkcji właściwości mogą być używane poza celów i są sprawdzane przed wszystkie przebiegi docelowego.

 Bez używania zadań programu MSBuild, może odczytywanie godziny systemowej, porównywanie ciągów, porównywanie wyrażeń regularnych i wykonywać inne czynności w skrypcie kompilacji. Program MSBuild podejmie próbę konwertowanie ciągu na liczbę i liczbę na ciąg i innych konwersji zgodnie z potrzebami.
 
Ciąg wartości zwracane przez funkcje właściwości mają [znaki specjalne](msbuild-special-characters.md) poprzedzone znakiem zmiany znaczenia. Jeśli wartość, które ma być traktowany tak, jakby został umieszczony bezpośrednio w pliku projektu, użyj `$([MSBuild]::Unescape())` do unescape znaków specjalnych.

## <a name="property-function-syntax"></a>Składnia funkcji właściwości

Oto trzy rodzaje funkcji właściwości; Każda funkcja ma inną składnię:

- Funkcje właściwości ciągów (tekstowych wystąpień)
- Funkcje statyczne właściwości
- Funkcje właściwości programu MSBuild

### <a name="string-property-functions"></a>Funkcje właściwości ciągu

Wszystkie wartości właściwości kompilacji są tylko ciągi. Za pomocą metod ciągów (tekstowych wystąpień) do działania na dowolnych wartościach właściwości. Na przykład można wyodrębnić nazwy dysku (pierwsze trzy znaki) z właściwości kompilacji, który reprezentuje pełną ścieżkę przy użyciu tego kodu:

```fundamental
$(ProjectOutputFolder.Substring(0,3))
```

### <a name="static-property-functions"></a>Funkcje statyczne właściwości

W skrypcie kompilacji można uzyskać dostęp do właściwości i metod statycznych wielu klas systemowych. Można pobrać wartości właściwości statycznej, należy użyć następującej składni, gdzie \<klasy > jest nazwą klasa systemu i \<właściwości > jest nazwą właściwości.

```fundamental
$([Class]::Property)
```

Na przykład można użyć poniższego kodu do ustawiania właściwości kompilacji do bieżącej daty i godziny.

```xml
<Today>$([System.DateTime]::Now)</Today>
```

Wywołać statyczną metodę, należy użyć następującej składni, gdzie \<klasy > jest nazwą klasa systemu \<metody > to nazwa metody, i (\<parametrów >) jest lista parametrów dla metody:

```fundamental
$([Class]::Method(Parameters))
```

Na przykład aby ustawić właściwości kompilacji nowego identyfikatora GUID, służy ten skrypt:

```xml
<NewGuid>$([System.Guid]::NewGuid())</NewGuid>
```

W funkcji właściwość statyczna można użyć dowolnej metody statycznej właściwości tych klas systemowych:

- System.Byte
- System.Char
- System.Convert
- System.DateTime
- System.Decimal
- System.Double
- System.Enum
- System.Guid
- System.Int16
- System.Int32
- System.Int64
- System.IO.Path
- System.Math
- System.Runtime.InteropServices.OSPlatform
- System.Runtime.InteropServices.RuntimeInformation
- System.UInt16
- System.UInt32
- System.UInt64
- System.SByte
- System.Single
- System.String
- System.StringComparer
- System.TimeSpan
- System.Text.RegularExpressions.Regex
- System.UriBuilder
- System.Version
- Microsoft.Build.Utilities.ToolLocationHelper

Ponadto można użyć następujących metod statycznych i właściwości:

- System.Environment::CommandLine
- System.Environment::ExpandEnvironmentVariables
- System.Environment::GetEnvironmentVariable
- System.Environment::GetEnvironmentVariables
- System.Environment::GetFolderPath
- System.Environment::GetLogicalDrives
- System.IO.Directory::GetDirectories
- System.IO.Directory::GetFiles
- System.IO.Directory::GetLastAccessTime
- System.IO.Directory::GetLastWriteTime
- System.IO.Directory::GetParent
- System.IO.File::Exists
- System.IO.File::GetCreationTime
- System.IO.File::GetAttributes
- System.IO.File::GetLastAccessTime
- System.IO.File::GetLastWriteTime
- System.IO.File::ReadAllText

### <a name="calling-instance-methods-on-static-properties"></a>Wywołanie metody wystąpienia w statycznej właściwości

Jeśli uzyskujesz dostęp do właściwości statycznej, która zwraca wystąpienie obiektu, można wywołać metody wystąpienia tego obiektu. Wywołania metody wystąpienia, należy użyć następującej składni, gdzie \<klasy > jest nazwą klasa systemu \<właściwości > jest nazwą właściwości \<— metoda > to nazwa metody, i (\<parametrów >) jest lista parametrów dla metody:

```fundamental
$([Class]::Property.Method(Parameters))
```

Nazwa klasy musi być w pełni kwalifikowaną nazwą zawierającą przestrzeń nazw.

Na przykład można użyć poniższego kodu do ustawiania właściwości kompilacji do bieżącej daty już dziś.

```xml
<Today>$([System.DateTime]::Now.ToString('yyyy.MM.dd'))</Today>
```

### <a name="msbuild-property-functions"></a>Funkcje właściwości programu MSBuild

Kilka metod statycznych w kompilacji możliwy jest zapewnienie operacje arytmetyczne, bitowe logicznej i obsługi znaków ucieczki. Możesz uzyskać dostęp do tych metod przy użyciu następującej składni, gdzie \<metody > jest nazwą metody i (\<parametrów >) jest lista parametrów dla metody.

```fundamental
$([MSBuild]::Method(Parameters))
```

Na przykład aby dodać ze sobą dwie właściwości, które mają wartości liczbowe, należy użyć następującego kodu.

```fundamental
$([MSBuild]::Add($(NumberOne), $(NumberTwo)))
```

Poniżej przedstawiono listę funkcji właściwości programu MSBuild:

|Sygnatura funkcji|Opis|
|------------------------|-----------------|
|dwukrotnie Dodaj (double, podwójne b)|Dodaj dwie wartości podwójnej precyzji.|
|czas dodawania (long, długie b)|Dodaj dwa wyroby długie.|
|Double odejmowania (double, podwójne b)|Odjąć dwie wartości podwójnej precyzji.|
|długi odejmowania (long, długie b)|Odejmij dwóch wyroby długie.|
|Double mnożenie (double, podwójne b)|Mnożenie dwóch wartości podwójnej precyzji.|
|długi mnożenie (long, długi b)|Mnożenie dwóch wyroby długie.|
|Podziel Double (double, podwójne b)|Dzieli dwie wartości podwójnej precyzji.|
|czas podzielić (long, długi b)|Dzielenie dwóch wyroby długie.|
|podwójne Modulo (double, podwójne b)|Modulo dwie wartości podwójnej precyzji.|
|długi Modulo (long, długi b)|Modulo dwóch wyroby długie.|
|ciąg Escape(string unescaped)|Znak ucieczki ciągu zgodnie z regułami ucieczki w MSBuild.|
|ciąg (string, poprzedzone znakiem zmiany znaczenia) Unescape|Unescape — ciągu zgodnie z regułami ucieczki w MSBuild.|
|int BitwiseOr (int, int pierwszego, drugiego)|Wykonania bitowej `OR` pierwszego i drugiego (pierwszy &#124; drugiego).|
|int BitwiseAnd (int, int pierwszego, drugiego)|Wykonania bitowej `AND` na pierwszym i drugim (pierwszy i drugi).|
|int BitwiseXor (int, int pierwszego, drugiego)|Wykonania bitowej `XOR` pierwszego i drugiego (pierwszy ^ drugiego).|
|int BitwiseNot(int first)|Wykonaj bitowej `NOT` (~ pierwszy).|
|wartość logiczna IsOsPlatform (platformString ciągu)|Określ, czy bieżąca Platforma systemu operacyjnego jest `platformString`. `platformString` Musisz być członkiem <xref:System.Runtime.InteropServices.OSPlatform>.|
|bool IsOSUnixLike()|Wartość true, jeśli bieżący system operacyjny jest systemu Unix.|
|ciąg NormalizePath (ścieżka params ciąg [])|Pobiera pełną ścieżkę postaci kanonicznej podana ścieżka i gwarantuje, że zawiera ona znaki separatora katalogu poprawny w bieżącym systemie operacyjnym.|
|ciąg NormalizeDirectory (ścieżka params ciąg [])|Pobiera pełną ścieżkę postaci kanonicznej podany katalog i zapewnia zawiera znaki separatora katalogu poprawny dla bieżącego systemu operacyjnego, przy jednoczesnym zapewnieniu jej posiada na końcu ukośnik.|
|ciąg EnsureTrailingSlash(string path)|Jeśli w podanej ścieżce nie ma ukośnika, dodać go. Jeśli ścieżka jest ciągiem pustym, nie powoduje modyfikacji go.|
|ciąg GetPathOfFileAbove (plik ciąg, ciąg startingDirectory)|Wyszukiwanie plików na podstawie pliku kompilacji bieżącego lokalizacji lub na podstawie `startingDirectory`, jeśli określony.|
|GetDirectoryNameOfFileAbove (string startingDirectory, string, nazwa_pliku)|Lokalizuje plik w katalogu wskazanym lub lokalizacji w strukturze katalogów powyżej tego katalogu.|
|ciąg MakeRelative (basePath ciąg, ciąg ścieżki)|Sprawia, że `path` względem `basePath`. `basePath` musi być bezwzględna katalogu. Jeśli `path` nie mogą być wprowadzane względną, jest zwracana verbatim. Podobnie jak `Uri.MakeRelativeUri`.|
|ciąg ValueOrDefault (conditionValue ciąg, ciąg defaultValue)|Zwraca ciąg w parametrze "defaultValue" tylko wtedy, gdy parametr "conditionValue" jest pusta, w przeciwnym razie, zwraca conditionValue wartość.|

## <a name="nested-property-functions"></a>Funkcje zagnieżdżonych właściwości

Można łączyć funkcje właściwości formularza bardziej złożone funkcje, co ilustruje poniższy przykład.

```fundamental
$([MSBuild]::BitwiseAnd(32, $([System.IO.File]::GetAttributes(tempFile))))
```

W tym przykładzie zwraca wartość <xref:System.IO.FileAttributes> `Archive` bitowych (32 lub 0) plik, na podstawie przez ścieżkę `tempFile`. Należy zauważyć, że wartości wyliczenia danych nie może występować według nazwy w obrębie funkcji właściwości. Zamiast tego należy użyć wartości liczbowej (32).

Metadane mogą również zostać wyświetlony w funkcjach zagnieżdżonych właściwości. Aby uzyskać więcej informacji, zobacz [przetwarzania wsadowego](../msbuild/msbuild-batching.md).

## <a name="msbuild-doestaskhostexist"></a>MSBuild DoesTaskHostExist

`DoesTaskHostExist` Właściwości w programie MSBuild:: gettotalsize() zwróciło czy hosta zadań jest obecnie zainstalowany dla określonych wartości środowiska uruchomieniowego i architektura.

Funkcja ta właściwość ma następującą składnię:

```fundamental
$([MSBuild]::DoesTaskHostExist(string theRuntime, string theArchitecture))
```

## <a name="msbuild-ensuretrailingslash"></a>MSBuild EnsureTrailingSlash

`EnsureTrailingSlash` Funkcja właściwości w programie MSBuild dodaje znaku ukośnika na końcu, jeśli jeszcze nie istnieje.

Funkcja ta właściwość ma następującą składnię:

```fundamental
$([MSBuild]::EnsureTrailingSlash('$(PathProperty)'))
```

## <a name="msbuild-getdirectorynameoffileabove"></a>MSBuild GetDirectoryNameOfFileAbove

MSBuild `GetDirectoryNameOfFileAbove` funkcji właściwości szuka plików w katalogach powyżej bieżącego katalogu w ścieżce.

 Funkcja ta właściwość ma następującą składnię:

```fundamental
$([MSBuild]::GetDirectoryNameOfFileAbove(string ThePath, string TheFile))
```

 Poniższy kod jest przykładem tej składni.

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))\EnlistmentInfo.props" Condition=" '$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), EnlistmentInfo.props))' != '' " />
```

## <a name="msbuild-getpathoffileabove"></a>MSBuild GetPathOfFileAbove

`GetPathOfFileAbove` Właściwości w programie MSBuild:: gettotalsize() zwróciło ścieżkę do pliku bezpośrednio po tym. Jest funkcjonalnym odpowiednikiem wywołania

```xml
<Import Project="$([MSBuild]::GetDirectoryNameOfFileAbove($(MSBuildThisFileDirectory), dir.props))\dir.props" />
```

Funkcja ta właściwość ma następującą składnię:

```fundamental
$([MSBuild]::GetPathOfFileAbove(dir.props))
```

## <a name="msbuild-getregistryvalue"></a>MSBuild GetRegistryValue

MSBuild `GetRegistryValue` właściwość:: gettotalsize() zwróciło wartość klucza rejestru. Ta funkcja przyjmuje dwa argumenty, nazwę klucza i nazwę wartości i zwraca wartość z rejestru. Jeśli nie określisz nazwy wartości jest zwracana wartość domyślna.

W poniższych przykładach pokazano, jak ta funkcja jest używana:

```fundamental
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, ``))                                  // default value
$([MSBuild]::GetRegistryValue(`HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\10.0\Debugger`, `SymbolCacheDir`))
$([MSBuild]::GetRegistryValue(`HKEY_LOCAL_MACHINE\SOFTWARE\(SampleName)`, `(SampleValue)`))             // parens in name and value
```

## <a name="msbuild-getregistryvaluefromview"></a>MSBuild GetRegistryValueFromView

MSBuild `GetRegistryValueFromView` właściwość funkcja pobiera dane rejestru systemu podanej w kluczu rejestru, wartości oraz jeden lub więcej uporządkowane widoków rejestru. Klucz i wartość są przeszukiwane w każdym widoku rejestru w kolejności dopóki nie zostały znalezione.

Składnia dla tej funkcji właściwości jest następująca:

```fundamental
[MSBuild]::GetRegistryValueFromView(string keyName, string valueName, object defaultValue, params object[] views)
```

Windows 64-bitowy system operacyjny obsługuje **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node** klucz rejestru, który przedstawia **HKEY_LOCAL_MACHINE\SOFTWARE** widok rejestru dla aplikacji 32-bitowych.

Domyślnie 32-bitowej aplikacji uruchomionych na WOW64 uzyskuje dostęp do widoku 32-bitowego rejestru, a aplikacją 64-bitową uzyskuje dostęp do widoku 64-bitowego rejestru.

Dostępne są następujące widoki rejestru:

|Widok rejestru|Definicja|
|-------------------|----------------|
|RegistryView.Registry32|Widok rejestru 32-bitowej aplikacji.|
|RegistryView.Registry64|Widok rejestru 64-bitowych aplikacji.|
|RegistryView.Default|Widok rejestru, który pasuje do procesu, który aplikacja jest uruchomiona na.|

Oto przykład.

 ```fundamental
$([MSBuild]::GetRegistryValueFromView('HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SDKs\Silverlight\v3.0\ReferenceAssemblies', 'SLRuntimeInstallPath', null, RegistryView.Registry64, RegistryView.Registry32))
```

pobiera **SLRuntimeInstallPath** danych **ReferenceAssemblies** klucza wyszukiwania pierwsze, w widoku 64-bitowego rejestru, a następnie w widoku rejestrów 32-bitowych.

## <a name="msbuild-makerelative"></a>MSBuild MakeRelative

MSBuild `MakeRelative` właściwość funkcja zwraca ścieżkę względną ścieżkę drugiego względem ścieżki pierwszego. Każda ścieżka może być pliku lub folderu.

Funkcja ta właściwość ma następującą składnię:

```fundamental
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

MSBuild `ValueOrDefault` właściwość funkcja zwraca pierwszy argument, chyba że jest to wartość null lub jest pusty. Jeśli pierwszy argument ma wartość null lub pusty, funkcja zwraca wartość drugiego argumentu.

Poniższy przykład pokazuje, jak ta funkcja jest używana.

```xml
<Project ToolsVersion="4.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <Value1>$([MSBuild]::ValueOrDefault(`$(UndefinedValue)`, `a`))</Value1>
        <Value2>$([MSBuild]::ValueOrDefault(`b`, `$(Value1)`))</Value2>
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

## <a name="see-also"></a>Zobacz także

- [Właściwości programu MSBuild](../msbuild/msbuild-properties.md)

- [Przegląd MSBuild](../msbuild/msbuild.md)
