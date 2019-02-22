---
title: Elementy wspólne projektu MSBuild | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 394a986963ad1d1690535aecbb3355bdbe382516
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56610349"
---
# <a name="common-msbuild-project-items"></a>Wspólne elementy projektów MSBuild
W [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], element jest nazwane odwołanie do jednego lub więcej plików. Elementy zawierają metadane, takie jak nazwy plików, ścieżek i numery wersji. Wszystkich typów projektów w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] są wspólne dla kilku elementów. Te elementy są zdefiniowane w pliku *Microsoft.Build.CommonTypes.xsd*.

## <a name="common-items"></a>Wspólne elementy
 Oto lista wszystkie wspólne elementy projektów.

### <a name="reference"></a>Tematy pomocy
 Reprezentuje odwołanie do zestawu (zarządzane) w projekcie.

|Nazwa metadanych elementu|Opis|
|---------------|-----------------|
|HintPath|Opcjonalny ciąg. Względna lub bezwzględna ścieżka zestawu.|
|Nazwa|Opcjonalny ciąg. Nazwa wyświetlana zestawu, na przykład, "przestrzeń nazw System.Windows.Forms."|
|FusionName|Opcjonalny ciąg. Określa nazwę fusion prostej lub silne dla elementu.<br /><br /> Jeśli ten atrybut jest obecny, można zaoszczędzić czas, ponieważ plik zestawu nie ma zostać otwarty, można uzyskać nazwy fusion.|
|SpecificVersion|Opcjonalny atrybut typu wartość logiczna. Określa, czy tylko do wersji w nazwie połączenia powinny istnieć odwołania.|
|Aliasy|Opcjonalny ciąg. Aliasy dla odwołania.|
|Private|Opcjonalny atrybut typu wartość logiczna. Określa, czy odwołania powinny zostać skopiowane do folderu wyjściowego. Ten atrybut jest zgodna **Kopiuj lokalnie** właściwość odniesienia, który znajduje się w środowisku IDE programu Visual Studio.|

### <a name="comreference"></a>COMReference
 Reprezentuje com. (niezarządzany) odwoływać się w projekcie.

|Nazwa metadanych elementu|Opis|
|---------------|-----------------|
|Nazwa|Opcjonalny ciąg. Nazwa wyświetlana składnika.|
|Guid|Opcjonalny ciąg. Identyfikator GUID dla składnika w formularzu {12345678-1234-1234-1234-1234567891234}.|
|VersionMajor|Opcjonalny ciąg. Główna część numeru wersji składnika. Na przykład "5" Jeśli pełny numer wersji jest "5.46".|
|VersionMinor|Opcjonalny ciąg. Pomocnicza część numeru wersji składnika. Na przykład "46" Jeśli pełny numer wersji jest "5.46".|
|LCID|Opcjonalny ciąg. Identyfikator ustawień regionalnych dla składnika.|
|WrapperTool|Opcjonalny ciąg. Nazwa narzędzia otoki, która jest używana w składniku, na przykład, "tlbimp".|
|Izolowany|Opcjonalny atrybut typu wartość logiczna. Określa, czy składnik jest składnik bezpłatne reg.|

### <a name="comfilereference"></a>COMFileReference
 Reprezentuje listę bibliotek typów, które źródła danych do obiektu docelowego ResolvedComreference.

|Nazwa metadanych elementu|Opis|
|---------------|-----------------|
|WrapperTool|Opcjonalny ciąg. Nazwa narzędzia otoki, która jest używana w składniku, na przykład, "tlbimp".|

### <a name="nativereference"></a>NativeReference
 Reprezentuje natywnego pliku manifestu lub odwołanie do tego pliku.

|Nazwa metadanych elementu|Opis|
|---------------|-----------------|
|Nazwa|Wymagany ciąg. Podstawowa nazwa pliku manifestu.|
|HintPath|Wymagany ciąg. Ścieżka względna pliku manifestu.|

### <a name="projectreference"></a>Elementu ProjectReference
 Reprezentuje odwołanie do innego projektu.

|Nazwa metadanych elementu|Opis|
|---------------|-----------------|
|Nazwa|Opcjonalny ciąg. Nazwa wyświetlana odwołania.|
|Projekt|Opcjonalny ciąg. Identyfikator GUID odwołania, w postaci {12345678-1234-1234-1234-1234567891234}.|
|Package|Opcjonalny ciąg. Ścieżka pliku projektu, do którego prowadzi odwołanie.|
|ReferenceOutputAssembly|Opcjonalny atrybut typu wartość logiczna. Jeśli ustawiono `false`, nie zawiera danych wyjściowych przywoływanego projektu jako [odwołania](#Reference) tego projektu, ale zapewnia, że inne projekt zostanie skompilowany przed ten zestaw. Wartość domyślna to `true`.|

### <a name="compile"></a>Kompilacji
 Reprezentuje pliki źródłowe dla kompilatora.


| Nazwa metadanych elementu | Opis |
|-----------------------| - |
| DependentUpon | Opcjonalny ciąg. Określa plik, który zależy od tego pliku do poprawnej kompilacji. |
| AutoGen | Opcjonalny atrybut typu wartość logiczna. Wskazuje, czy plik został wygenerowany dla projektu, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE). |
| Łącze | Opcjonalny ciąg. Ścieżka notational wyświetlany, gdy plik znajduje się fizycznie poza wpływają na pliku projektu. |
| Widoczne | Opcjonalny atrybut typu wartość logiczna. Wskazuje, czy mają być wyświetlane w pliku w **Eksploratora rozwiązań** w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| CopyToOutputDirectory | Opcjonalny ciąg. Określa, czy należy skopiować plik do katalogu wyjściowego. Dostępne są następujące wartości:<br /><br /> 1.  nigdy nie<br />2.  zawsze<br />3.  PreserveNewest |

### <a name="embeddedresource"></a>EmbeddedResource
 Reprezentuje zasoby do osadzenia w wygenerowanym zestawie.


| Nazwa metadanych elementu | Opis |
|-----------------------| - |
| DependentUpon | Opcjonalny ciąg. Określa plik który zależy od tego pliku do poprawnej kompilacji |
| Generator | Wymagany ciąg. Nazwa dowolnego generatora plików uruchamianego na tym elemencie. |
| LastGenOutput | Wymagany ciąg. Nazwa pliku, który został utworzony przez dowolny generator plików, który uruchomił ten element. |
| CustomToolNamespace | Wymagany ciąg. Przestrzeń nazw, w którym każdy plik, generator, który działa na tym elemencie, powinien utworzyć kod. |
| Łącze | Opcjonalny ciąg. Ścieżka notational jest wyświetlana, jeśli plik znajduje się fizycznie poza wpływ projektu. |
| Widoczne | Opcjonalny atrybut typu wartość logiczna. Wskazuje, czy mają być wyświetlane w pliku w **Eksploratora rozwiązań** w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| CopyToOutputDirectory | Opcjonalny ciąg. Określa, czy należy skopiować plik do katalogu wyjściowego. Dostępne są następujące wartości:<br /><br /> 1.  nigdy nie<br />2.  zawsze<br />3.  PreserveNewest |
| LogicalName | Wymagany ciąg. Nazwa logiczna zasobu osadzonego. |

### <a name="content"></a>Zawartość
 Reprezentuje pliki, które nie są kompilowane do projektu, ale mogą być osadzone lub opublikowane wraz z jej.


| Nazwa metadanych elementu | Opis |
|-----------------------| - |
| DependentUpon | Opcjonalny ciąg. Określa plik, który zależy od tego pliku do poprawnej kompilacji. |
| Generator | Wymagany ciąg. Nazwa dowolnego generatora plików uruchamianego na tym elemencie. |
| LastGenOutput | Wymagany ciąg. Nazwa pliku, który został utworzony przez dowolny generator plików, która została uruchomiona na tym elemencie. |
| CustomToolNamespace | Wymagany ciąg. Przestrzeń nazw, w którym każdy plik, generator, który działa na tym elemencie, powinien utworzyć kod. |
| Łącze | Opcjonalny ciąg. Ścieżka notational mają być wyświetlane, jeśli plik znajduje się fizycznie poza wpływ projektu. |
| PublishState | Wymagany ciąg. Stan publikowania zawartości, albo:<br /><br /> -Domyślnie<br />— Włączone<br />— Wyłączone<br />-Pliku danych<br />-Wymagań wstępnych |
| IsAssembly | Opcjonalny atrybut typu wartość logiczna. Określa, czy plik jest zestawem. |
| Widoczne | Opcjonalny atrybut typu wartość logiczna. Wskazuje, czy mają być wyświetlane w pliku w **Eksploratora rozwiązań** w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| CopyToOutputDirectory | Opcjonalny ciąg. Określa, czy należy skopiować plik do katalogu wyjściowego. Dostępne są następujące wartości:<br /><br /> 1.  nigdy nie<br />2.  zawsze<br />3.  PreserveNewest |

### <a name="none"></a>Brak
 Reprezentuje pliki, które powinny mieć żadnej roli w procesie kompilacji.


| Nazwa metadanych elementu | Opis |
|-----------------------| - |
| DependentUpon | Opcjonalny ciąg. Określa plik, który zależy od tego pliku do poprawnej kompilacji. |
| Generator | Wymagany ciąg. Nazwa dowolnego generatora plików uruchamianego na tym elemencie. |
| LastGenOutput | Wymagany ciąg. Nazwa pliku, który został utworzony przez dowolny generator plików, który uruchomił ten element. |
| CustomToolNamespace | Wymagany ciąg. Przestrzeń nazw, w którym każdy plik, generator, który działa na tym elemencie, powinien utworzyć kod. |
| Łącze | Opcjonalny ciąg. Ścieżka notational mają być wyświetlane, jeśli plik znajduje się fizycznie poza wpływ projektu. |
| Widoczne | Opcjonalny atrybut typu wartość logiczna. Wskazuje, czy mają być wyświetlane w pliku w **Eksploratora rozwiązań** w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. |
| CopyToOutputDirectory | Opcjonalny ciąg. Określa, czy należy skopiować plik do katalogu wyjściowego. Dostępne są następujące wartości:<br /><br /> 1.  nigdy nie<br />2.  zawsze<br />3.  PreserveNewest |

### <a name="baseapplicationmanifest"></a>BaseApplicationManifest
 Reprezentuje podstawowy manifest aplikacji dla kompilacji i zawiera [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] informacji o zabezpieczeniach wdrożenia.

### <a name="codeanalysisimport"></a>CodeAnalysisImport
 Reprezentuje projekt programu FxCop, aby zaimportować.

### <a name="import"></a>Import
 Reprezentuje zestawy, których przestrzenie nazw powinny być importowane przez [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kompilatora.

## <a name="see-also"></a>Zobacz także
- [Wspólne właściwości projektów MSBuild](../msbuild/common-msbuild-project-properties.md)
