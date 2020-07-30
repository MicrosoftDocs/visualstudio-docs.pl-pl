---
title: Wspólne elementy projektów MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, common project items
ms.assetid: 1eba3721-cc12-4b80-9987-84923ede5e2e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 99ed79b1654057c4114ceb171b5cb1e1dfdb439f
ms.sourcegitcommit: dda98068c0f62ccd1a19fdfde4bdb822428d0125
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2020
ms.locfileid: "87425397"
---
# <a name="common-msbuild-project-items"></a>Wspólne elementy projektów MSBuild

W programie MSBuild element jest nazwanym odwołaniem do co najmniej jednego pliku. Elementy zawierają metadane, takie jak nazwy plików, ścieżki i numery wersji. Wszystkie typy projektów w programie Visual Studio mają kilka elementów wspólnych. Te elementy są zdefiniowane w pliku *Microsoft. Build. CommonTypes. xsd*.

## <a name="common-items"></a>Elementy wspólne

Poniżej znajduje się lista wszystkich wspólnych elementów projektu.

### <a name="reference"></a>Tematy pomocy

Reprezentuje odwołanie zestawu (zarządzanego) w projekcie.

|Nazwa metadanych elementu|Opis|
|---------------|-----------------|
|HintPath|Opcjonalny ciąg. Ścieżka względna lub bezwzględna zestawu.|
|Nazwa|Opcjonalny ciąg. Nazwa wyświetlana zestawu, na przykład "System. Windows. Forms".|
|FusionName|Opcjonalny ciąg. Określa prostą lub silną nazwę syntezy dla elementu.<br /><br /> Gdy ten atrybut jest obecny, może zaoszczędzić czas, ponieważ plik zestawu nie musi być otwarty w celu uzyskania nazwy Fusion.|
|Ustawienie SpecificVersion|Opcjonalna wartość logiczna. Określa, czy należy odwoływać się tylko do wersji w nazwie Fusion.|
|Aliasy|Opcjonalny ciąg. Wszelkie aliasy odwołania.|
|Prywatne|Opcjonalna wartość logiczna. Określa, czy odwołanie ma być kopiowane do folderu wyjściowego. Ten atrybut jest zgodny z właściwością **copy lokalnego** odwołania, która znajduje się w środowisku IDE programu Visual Studio.|

### <a name="comreference"></a>COMReference

Reprezentuje odwołanie do składnika COM (niezarządzane) w projekcie. Ten element ma zastosowanie tylko do projektów .NET.

|Nazwa metadanych elementu|Opis|
|---------------|-----------------|
|Nazwa|Opcjonalny ciąg. Nazwa wyświetlana składnika.|
|Guid (identyfikator GUID)|Wymagany ciąg. Identyfikator GUID składnika w formularzu {12345678-1234-1234-1234-1234567891234} .|
|VersionMajor|Wymagany ciąg. Główna część numeru wersji składnika. Na przykład "5", jeśli pełny numer wersji to "5,46".|
|VersionMinor|Wymagany ciąg. Pomocnicza część numeru wersji składnika. Na przykład "46", jeśli pełny numer wersji to "5,46".|
|Identyfikator LCID|Opcjonalny ciąg. LocaleID dla składnika.|
|WrapperTool|Opcjonalny ciąg. Nazwa narzędzia otoki, które jest używane w składniku, na przykład "tlbimp".|
|Izolowana|Opcjonalna wartość logiczna. Określa, czy składnik jest składnikiem bezpłatnym reg.|

### <a name="comfilereference"></a>COMFileReference

Reprezentuje listę bibliotek typów, które są przesyłane do `TypeLibFiles` parametru elementu docelowego [ResolveComReference —](resolvecomreference-task.md) . Ten element ma zastosowanie tylko do projektów .NET.

|Nazwa metadanych elementu|Opis|
|---------------|-----------------|
|WrapperTool|Opcjonalny ciąg. Nazwa narzędzia otoki, które jest używane w składniku, na przykład "tlbimp".|

### <a name="nativereference"></a>NativeReference

Reprezentuje natywny plik manifestu lub odwołanie do takiego pliku.

|Nazwa metadanych elementu|Opis|
|---------------|-----------------|
|Nazwa|Wymagany ciąg. Podstawowa nazwa pliku manifestu.|
|HintPath|Wymagany ciąg. Ścieżka względna pliku manifestu.|

### <a name="projectreference"></a>Elementu ProjectReference

Reprezentuje odwołanie do innego projektu. `ProjectReference`elementy są przekształcane w elementy [odniesienia](#reference) przez `ResolveProjectReferences` obiekt docelowy, więc wszystkie prawidłowe metadane w odwołaniu mogą być prawidłowe w `ProjectReference` przypadku, gdy proces transformacji nie zastąpi tego elementu.

|Nazwa metadanych elementu|Opis|
|---------------|-----------------|
|Nazwa|Opcjonalny ciąg. Nazwa wyświetlana odwołania.|
|Project|Opcjonalny ciąg. Identyfikator GUID odwołania w formularzu {12345678-1234-1234-1234-1234567891234} .|
|Pakiet|Opcjonalny ciąg. Ścieżka do pliku projektu, do którego istnieje odwołanie.|
|ReferenceOutputAssembly|Opcjonalna wartość logiczna. Jeśli jest ustawiona na `false` , program nie uwzględnia danych wyjściowych przywoływanego projektu jako [odwołania](#reference) do tego projektu, ale nadal zapewnia, że inny projekt zostanie skompilowany przed tym. Wartość domyślna to `true` .|

### <a name="compile"></a>Opracowania

Reprezentuje pliki źródłowe kompilatora.

| Nazwa metadanych elementu | Opis |
|-----------------------| - |
| DependentUpon | Opcjonalny ciąg. Określa plik, od którego zależy plik, aby skompilować poprawnie. |
| AutoGen | Opcjonalna wartość logiczna. Wskazuje, czy plik został wygenerowany dla projektu przez zintegrowane środowisko programistyczne (IDE) programu Visual Studio. |
| Link | Opcjonalny ciąg. Ścieżka zapisu, która ma być wyświetlana, gdy plik jest fizycznie zlokalizowany poza wpływem pliku projektu. |
| Widoczne | Opcjonalna wartość logiczna. Wskazuje, czy plik ma być wyświetlany w **Eksplorator rozwiązań** w programie Visual Studio. |
| CopyToOutputDirectory | Opcjonalny ciąg. Określa, czy plik ma być kopiowany do katalogu wyjściowego. Wartości to:<br /><br /> 1. nigdy nie<br />2. zawsze<br />3. PreserveNewest |

### <a name="embeddedresource"></a>EmbeddedResource

Reprezentuje zasoby do osadzenia w wygenerowanym zestawie.

| Nazwa metadanych elementu | Opis |
|-----------------------| - |
| DependentUpon | Opcjonalny ciąg. Określa plik, od którego zależy plik, aby skompilować prawidłowo |
| Generator | Wymagany ciąg. Nazwa dowolnego generatora plików uruchamianego na tym elemencie. |
| LastGenOutput | Wymagany ciąg. Nazwa pliku, który został utworzony przez dowolny Generator plików uruchomiony na tym elemencie. |
| CustomToolNamespace | Wymagany ciąg. Przestrzeń nazw, w której każdy Generator plików uruchomiony na tym elemencie powinien utworzyć kod. |
| Link | Opcjonalny ciąg. Ścieżka notacji jest wyświetlana, jeśli plik jest fizycznie zlokalizowany poza wpływem projektu. |
| Widoczne | Opcjonalna wartość logiczna. Wskazuje, czy plik ma być wyświetlany w **Eksplorator rozwiązań** w programie Visual Studio. |
| CopyToOutputDirectory | Opcjonalny ciąg. Określa, czy plik ma być kopiowany do katalogu wyjściowego. Wartości to:<br /><br /> 1. nigdy nie<br />2. zawsze<br />3. PreserveNewest |
| Logicznaname | Wymagany ciąg. Nazwa logiczna zasobu osadzonego. |

### <a name="content"></a>Zawartość

Reprezentuje pliki, które nie są kompilowane do projektu, ale mogą być osadzone lub opublikowane razem z nim.

| Nazwa metadanych elementu | Opis |
|-----------------------| - |
| DependentUpon | Opcjonalny ciąg. Określa plik, od którego zależy plik, aby skompilować poprawnie. |
| Generator | Wymagany ciąg. Nazwa dowolnego generatora plików uruchamianego na tym elemencie. |
| LastGenOutput | Wymagany ciąg. Nazwa pliku, który został utworzony przez dowolny Generator plików uruchomiony na tym elemencie. |
| CustomToolNamespace | Wymagany ciąg. Przestrzeń nazw, w której każdy Generator plików uruchomiony na tym elemencie powinien utworzyć kod. |
| Link | Opcjonalny ciąg. Ścieżka notacji, która ma być wyświetlana, jeśli plik jest fizycznie zlokalizowany poza wpływem projektu. |
| PublishState | Wymagany ciąg. Stan publikowania zawartości:<br /><br /> -Domyślne<br />-Uwzględnione<br />-Wykluczone<br />-Plik<br />-Wymaganie wstępne |
| IsAssembly | Opcjonalna wartość logiczna. Określa, czy plik jest zestawem. |
| Widoczne | Opcjonalna wartość logiczna. Wskazuje, czy plik ma być wyświetlany w **Eksplorator rozwiązań** w programie Visual Studio. |
| CopyToOutputDirectory | Opcjonalny ciąg. Określa, czy plik ma być kopiowany do katalogu wyjściowego. Wartości to:<br /><br /> 1. nigdy nie<br />2. zawsze<br />3. PreserveNewest |

### <a name="none"></a>Brak

Reprezentuje pliki, które nie powinny mieć roli w procesie kompilacji.

| Nazwa metadanych elementu | Opis |
|-----------------------| - |
| DependentUpon | Opcjonalny ciąg. Określa plik, od którego zależy plik, aby skompilować poprawnie. |
| Generator | Wymagany ciąg. Nazwa dowolnego generatora plików uruchamianego na tym elemencie. |
| LastGenOutput | Wymagany ciąg. Nazwa pliku, który został utworzony przez dowolny Generator plików uruchomiony na tym elemencie. |
| CustomToolNamespace | Wymagany ciąg. Przestrzeń nazw, w której każdy Generator plików uruchomiony na tym elemencie powinien utworzyć kod. |
| Link | Opcjonalny ciąg. Ścieżka notacji, która ma być wyświetlana, jeśli plik jest fizycznie zlokalizowany poza wpływem projektu. |
| Widoczne | Opcjonalna wartość logiczna. Wskazuje, czy plik ma być wyświetlany w **Eksplorator rozwiązań** w programie Visual Studio. |
| CopyToOutputDirectory | Opcjonalny ciąg. Określa, czy plik ma być kopiowany do katalogu wyjściowego. Wartości to:<br /><br /> 1. nigdy nie<br />2. zawsze<br />3. PreserveNewest |

### <a name="assemblymetadata"></a>AssemblyMetadata

Reprezentuje atrybuty zestawu, które mają zostać wygenerowane `[AssemblyMetadata(key, value)]` .

| Nazwa metadanych elementu | Opis |
|-----------------------| - |
| Uwzględnij | Staną się pierwszym parametrem (kluczem) w `AssemblyMetadataAttribute` konstruktorze atrybutu. |
| Wartość | Wymagany ciąg. Jest drugim parametrem (wartość) w `AssemblyMetadataAttribute` konstruktorze atrybutu. |

> [!NOTE]
> Dotyczy to projektów korzystających tylko z zestaw .NET Core SDK.

### <a name="baseapplicationmanifest"></a>BaseApplicationManifest

Reprezentuje podstawowy manifest aplikacji dla kompilacji i zawiera informacje o zabezpieczeniach wdrażania ClickOnce.

### <a name="codeanalysisimport"></a>CodeAnalysisImport

Reprezentuje projekt FxCop do zaimportowania.

### <a name="import"></a>Importuj

Reprezentuje zestawy, których przestrzenie nazw powinny być importowane przez kompilator Visual Basic.

## <a name="see-also"></a>Zobacz też

- [Wspólne właściwości projektów MSBuild](../msbuild/common-msbuild-project-properties.md)
- [Właściwości programu MSBuild dla projektów zestaw .NET Core SDK](/dotnet/core/project-sdk/msbuild-props)
- [Typowe metadane elementu MSBuild](common-msbuild-item-metadata.md)