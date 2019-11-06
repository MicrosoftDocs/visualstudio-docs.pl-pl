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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0493e7d16a7c7ecb7a9cf7d414e3bd13cb9ad9a7
ms.sourcegitcommit: f9f389e72787de30eb869a55ef7725a10a4011f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/06/2019
ms.locfileid: "73636576"
---
# <a name="common-msbuild-project-items"></a>Wspólne elementy projektu MSBuild
W [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]element jest nazwanym odwołaniem do co najmniej jednego pliku. Elementy zawierają metadane, takie jak nazwy plików, ścieżki i numery wersji. Wszystkie typy projektów w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] mają kilka elementów wspólnych. Te elementy są zdefiniowane w pliku *Microsoft. Build. CommonTypes. xsd*.

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
|Private|Opcjonalna wartość logiczna. Określa, czy odwołanie ma być kopiowane do folderu wyjściowego. Ten atrybut jest zgodny z właściwością **copy lokalnego** odwołania, która znajduje się w środowisku IDE programu Visual Studio.|

### <a name="comreference"></a>COMReference
 Reprezentuje odwołanie do składnika COM (niezarządzane) w projekcie. Ten element ma zastosowanie tylko do projektów .NET.

|Nazwa metadanych elementu|Opis|
|---------------|-----------------|
|Nazwa|Opcjonalny ciąg. Nazwa wyświetlana składnika.|
|Ident|Wymagany ciąg. Identyfikator GUID składnika w postaci {12345678-1234-1234-1234-1234567891234}.|
|VersionMajor|Wymagany ciąg. Główna część numeru wersji składnika. Na przykład "5", jeśli pełny numer wersji to "5,46".|
|VersionMinor|Wymagany ciąg. Pomocnicza część numeru wersji składnika. Na przykład "46", jeśli pełny numer wersji to "5,46".|
|ISTNIEJĄCYCH|Opcjonalny ciąg. LocaleID dla składnika.|
|WrapperTool|Opcjonalny ciąg. Nazwa narzędzia otoki, które jest używane w składniku, na przykład "tlbimp".|
|Ogół|Opcjonalna wartość logiczna. Określa, czy składnik jest składnikiem bezpłatnym reg.|

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
 Reprezentuje odwołanie do innego projektu.

|Nazwa metadanych elementu|Opis|
|---------------|-----------------|
|Nazwa|Opcjonalny ciąg. Nazwa wyświetlana odwołania.|
|Projekt|Opcjonalny ciąg. Identyfikator GUID odwołania w formularzu {12345678-1234-1234-1234-1234567891234}.|
|Package|Opcjonalny ciąg. Ścieżka do pliku projektu, do którego istnieje odwołanie.|
|ReferenceOutputAssembly|Opcjonalna wartość logiczna. Jeśli ustawiona na `false`, program nie uwzględnia danych wyjściowych przywoływanego projektu jako [odwołania](#reference) do tego projektu, ale nadal zapewnia, że inny projekt zostanie skompilowany przed tym. Wartość domyślna to `true`.|

### <a name="compile"></a>Opracowania
 Reprezentuje pliki źródłowe kompilatora.

| Nazwa metadanych elementu | Opis |
|-----------------------| - |
| DependentUpon | Opcjonalny ciąg. Określa plik, od którego zależy plik, aby skompilować poprawnie. |
| AutoGen | Opcjonalna wartość logiczna. Wskazuje, czy plik został wygenerowany dla projektu przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE). |
| Łącze | Opcjonalny ciąg. Ścieżka zapisu, która ma być wyświetlana, gdy plik jest fizycznie zlokalizowany poza wpływem pliku projektu. |
| Widać | Opcjonalna wartość logiczna. Wskazuje, czy plik ma być wyświetlany w **Eksplorator rozwiązań** w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| CopyToOutputDirectory | Opcjonalny ciąg. Określa, czy plik ma być kopiowany do katalogu wyjściowego. Wartości to:<br /><br /> 1. nigdy nie<br />2. zawsze<br />3. PreserveNewest |

### <a name="embeddedresource"></a>EmbeddedResource
 Reprezentuje zasoby do osadzenia w wygenerowanym zestawie.

| Nazwa metadanych elementu | Opis |
|-----------------------| - |
| DependentUpon | Opcjonalny ciąg. Określa plik, od którego zależy plik, aby skompilować prawidłowo |
| Generator | Wymagany ciąg. Nazwa dowolnego generatora plików uruchamianego na tym elemencie. |
| LastGenOutput | Wymagany ciąg. Nazwa pliku, który został utworzony przez dowolny Generator plików uruchomiony na tym elemencie. |
| CustomToolNamespace | Wymagany ciąg. Przestrzeń nazw, w której każdy Generator plików uruchomiony na tym elemencie powinien utworzyć kod. |
| Łącze | Opcjonalny ciąg. Ścieżka notacji jest wyświetlana, jeśli plik jest fizycznie zlokalizowany poza wpływem projektu. |
| Widać | Opcjonalna wartość logiczna. Wskazuje, czy plik ma być wyświetlany w **Eksplorator rozwiązań** w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
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
| Łącze | Opcjonalny ciąg. Ścieżka notacji, która ma być wyświetlana, jeśli plik jest fizycznie zlokalizowany poza wpływem projektu. |
| PublishState | Wymagany ciąg. Stan publikowania zawartości:<br /><br /> -Domyślne<br />-Uwzględnione<br />-Wykluczone<br />-Plik<br />-Wymaganie wstępne |
| IsAssembly | Opcjonalna wartość logiczna. Określa, czy plik jest zestawem. |
| Widać | Opcjonalna wartość logiczna. Wskazuje, czy plik ma być wyświetlany w **Eksplorator rozwiązań** w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| CopyToOutputDirectory | Opcjonalny ciąg. Określa, czy plik ma być kopiowany do katalogu wyjściowego. Wartości to:<br /><br /> 1. nigdy nie<br />2. zawsze<br />3. PreserveNewest |

### <a name="none"></a>Brak
 Reprezentuje pliki, które nie powinny mieć roli w procesie kompilacji.

| Nazwa metadanych elementu | Opis |
|-----------------------| - |
| DependentUpon | Opcjonalny ciąg. Określa plik, od którego zależy plik, aby skompilować poprawnie. |
| Generator | Wymagany ciąg. Nazwa dowolnego generatora plików uruchamianego na tym elemencie. |
| LastGenOutput | Wymagany ciąg. Nazwa pliku, który został utworzony przez dowolny Generator plików uruchomiony na tym elemencie. |
| CustomToolNamespace | Wymagany ciąg. Przestrzeń nazw, w której każdy Generator plików uruchomiony na tym elemencie powinien utworzyć kod. |
| Łącze | Opcjonalny ciąg. Ścieżka notacji, która ma być wyświetlana, jeśli plik jest fizycznie zlokalizowany poza wpływem projektu. |
| Widać | Opcjonalna wartość logiczna. Wskazuje, czy plik ma być wyświetlany w **Eksplorator rozwiązań** w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| CopyToOutputDirectory | Opcjonalny ciąg. Określa, czy plik ma być kopiowany do katalogu wyjściowego. Wartości to:<br /><br /> 1. nigdy nie<br />2. zawsze<br />3. PreserveNewest |

### <a name="assemblymetadata"></a>AssemblyMetadata
 Reprezentuje atrybuty zestawu, które mają zostać wygenerowane jako `[AssemblyMetadata(key, value)]`.

| Nazwa metadanych elementu | Opis |
|-----------------------| - |
| Uwzględnij | Staną się pierwszym parametrem (kluczem) w konstruktorze atrybutów `AssemblyMetadataAttribute`. |
| Wartość | Wymagany ciąg. Zostanie drugim parametrem (wartość) w konstruktorze atrybutu `AssemblyMetadataAttribute`. |

> [!NOTE]
> Dotyczy to projektów korzystających tylko z zestaw .NET Core SDK.
### <a name="baseapplicationmanifest"></a>BaseApplicationManifest
 Reprezentuje podstawowy manifest aplikacji dla kompilacji i zawiera [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] informacje o zabezpieczeniach wdrożenia.

### <a name="codeanalysisimport"></a>CodeAnalysisImport
 Reprezentuje projekt FxCop do zaimportowania.

### <a name="import"></a>Zaimportować
 Reprezentuje zestawy, których przestrzenie nazw powinny być importowane przez kompilator [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].

## <a name="see-also"></a>Zobacz także
- [Wspólne właściwości projektu MSBuild](../msbuild/common-msbuild-project-properties.md)
