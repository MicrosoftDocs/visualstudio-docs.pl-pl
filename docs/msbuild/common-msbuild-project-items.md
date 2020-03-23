---
title: Typowe elementy projektu MSBuild | Dokumenty firmy Microsoft
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
ms.openlocfilehash: c7725108fd71f4292a8d3fa4dfe68ca29d3dcd90
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634451"
---
# <a name="common-msbuild-project-items"></a>Typowe elementy projektu MSBuild

W MSBuild element jest nazwanym odwołaniem do jednego lub więcej plików. Elementy zawierają metadane, takie jak nazwy plików, ścieżki i numery wersji. Wszystkie typy projektów w programie Visual Studio mają kilka wspólnych elementów. Te elementy są zdefiniowane w pliku *Microsoft.Build.CommonTypes.xsd*.
## <a name="common-items"></a>Typowe przedmioty

 Poniżej znajduje się lista wszystkich typowych elementów projektu.
Poniżej znajduje się lista wszystkich typowych elementów projektu.

### <a name="reference"></a>Dokumentacja

 Reprezentuje odwołanie do zestawu (zarządzane) w projekcie.

|Nazwa metadanych elementu|Opis|
|---------------|-----------------|
|Ścieżka podpowiedzi|Opcjonalny ciąg znaków. Względna lub bezwzględna ścieżka złożenia.|
|Nazwa|Opcjonalny ciąg znaków. Wyświetlana nazwa zestawu, na przykład "System.Windows.Forms".|
|Nazwa fuzji|Opcjonalny ciąg znaków. Określa prostą lub silną nazwę fuzji dla elementu.<br /><br /> Gdy ten atrybut jest obecny, można zaoszczędzić czas, ponieważ plik zestawu nie musi być otwarty, aby uzyskać nazwę fuzji.|
|SpecificVersion (Specyfik)|Opcjonalny wartość logiczna. Określa, czy należy odwoływać się tylko do wersji w nazwie fuzji.|
|Aliasy|Opcjonalny ciąg znaków. Wszelkie aliasy dla odwołania.|
|Private|Opcjonalny wartość logiczna. Określa, czy odwołanie ma być kopiowane do folderu wyjściowego. Ten atrybut jest zgodny z właściwością **Kopiuj lokalną** odwołania, która znajduje się w programie Visual Studio IDE.|

### <a name="comreference"></a>Wniosek COM

 Reprezentuje odwołanie do składnika COM (niezarządzane) w projekcie. Ten element dotyczy tylko projektów platformy .NET.

|Nazwa metadanych elementu|Opis|
|---------------|-----------------|
|Nazwa|Opcjonalny ciąg znaków. Wyświetlana nazwa komponentu.|
|Guid (identyfikator GUID)|Wymagany ciąg. Identyfikator GUID dla składnika {12345678-1234-1234-1234-1234567891234}w formularzu .|
|WersjaMajor|Wymagany ciąg. Główna część numeru wersji składnika. Na przykład "5", jeśli pełny numer wersji to "5.46".|
|WersjaMinor|Wymagany ciąg. Pomocnicza część numeru wersji składnika. Na przykład "46", jeśli pełny numer wersji to "5.46".|
|Identyfikator LCID|Opcjonalny ciąg znaków. LocaleID dla składnika.|
|WrapperTool (WrapperTool)|Opcjonalny ciąg znaków. Nazwa narzędzia otoki używanego w komponencie, na przykład "tlbimp".|
|Izolowany|Opcjonalny wartość logiczna. Określa, czy komponent jest komponentem wolnym od reg.|

### <a name="comfilereference"></a>Wniosek COMFileReference

 Reprezentuje listę bibliotek typów, które są `TypeLibFiles` przekazywane do parametru obiektu docelowego [ResolveComReference.](resolvecomreference-task.md) Ten element dotyczy tylko projektów platformy .NET.

|Nazwa metadanych elementu|Opis|
|---------------|-----------------|
|WrapperTool (WrapperTool)|Opcjonalny ciąg znaków. Nazwa narzędzia otoki używanego w komponencie, na przykład "tlbimp".|

### <a name="nativereference"></a>NativeReference (NativeReference)

 Reprezentuje natywny plik manifestu lub odwołanie do takiego pliku.

|Nazwa metadanych elementu|Opis|
|---------------|-----------------|
|Nazwa|Wymagany ciąg. Nazwa podstawowa pliku manifestu.|
|Ścieżka podpowiedzi|Wymagany ciąg. Ścieżka względna pliku manifestu.|

### <a name="projectreference"></a>Wniosek projektowy

 Reprezentuje odwołanie do innego projektu.

|Nazwa metadanych elementu|Opis|
|---------------|-----------------|
|Nazwa|Opcjonalny ciąg znaków. Wyświetlana nazwa odwołania.|
|Project|Opcjonalny ciąg znaków. Identyfikator GUID dla odwołania, {12345678-1234-1234-1234-1234567891234}w formularzu .|
|Pakiet|Opcjonalny ciąg znaków. Ścieżka pliku projektu, do którego się odwołuje.|
|ReferenceOutputAssembly|Opcjonalny wartość logiczna. Jeśli jest `false`ustawiona na , nie obejmuje dane wyjściowe projektu, do którego istnieje odwołanie, jak [odwołanie do](#reference) tego projektu, ale nadal zapewnia, że inny projekt jest budowany przed tym projektem. Wartość domyślna to `true`.|

### <a name="compile"></a>Skompilować

 Reprezentuje pliki źródłowe dla kompilatora.

| Nazwa metadanych elementu | Opis |
|-----------------------| - |
| ZależnePo | Opcjonalny ciąg znaków. Określa plik, od który plik zależy od poprawnego skompilowania. |
| AutoGen (AutoGen) | Opcjonalny wartość logiczna. Wskazuje, czy plik został wygenerowany dla projektu przez zintegrowane środowisko programistyczne programu Visual Studio (IDE). |
| Link | Opcjonalny ciąg znaków. Ścieżka notacyjna, która ma być wyświetlana, gdy plik fizycznie znajduje się poza wpływem pliku projektu. |
| Widoczne | Opcjonalny wartość logiczna. Wskazuje, czy plik ma być wyświetlany w **Eksploratorze rozwiązań** w programie Visual Studio. |
| CopyToOutputDirectory (CopyToOutputDirectory) | Opcjonalny ciąg znaków. Określa, czy plik ma być kopiowany do katalogu wyjściowego. Wartości to:<br /><br /> 1. Nigdy<br />2. Zawsze<br />3. ZachowaćZachód |

### <a name="embeddedresource"></a>Zasoby wbudowaneSerekseźródło

 Reprezentuje zasoby, które mają być osadzone w wygenerowanym zestawie.

| Nazwa metadanych elementu | Opis |
|-----------------------| - |
| ZależnePo | Opcjonalny ciąg znaków. Określa plik, od który zależy ten plik, aby skompilować poprawnie |
| Generator | Wymagany ciąg. Nazwa dowolnego generatora plików, który jest uruchamiany na tym elemencie. |
| LastGenOutput (LastGenOutput) | Wymagany ciąg. Nazwa pliku, który został utworzony przez dowolnego generatora plików, który działał na tym elemencie. |
| Obszar CustomToolNamespace | Wymagany ciąg. Obszar nazw, w którym każdy generator plików, który działa na tym elemencie, powinien utworzyć kod. |
| Link | Opcjonalny ciąg znaków. Ścieżka notacyjna jest wyświetlana, jeśli plik fizycznie znajduje się poza wpływem projektu. |
| Widoczne | Opcjonalny wartość logiczna. Wskazuje, czy plik ma być wyświetlany w **Eksploratorze rozwiązań** w programie Visual Studio. |
| CopyToOutputDirectory (CopyToOutputDirectory) | Opcjonalny ciąg znaków. Określa, czy plik ma być kopiowany do katalogu wyjściowego. Wartości to:<br /><br /> 1. Nigdy<br />2. Zawsze<br />3. ZachowaćZachód |
| Nazwa logiczna | Wymagany ciąg. Logiczna nazwa osadzonego zasobu. |

### <a name="content"></a>Zawartość

 Reprezentuje pliki, które nie są kompilowane do projektu, ale mogą być osadzone lub opublikowane razem z nim.

| Nazwa metadanych elementu | Opis |
|-----------------------| - |
| ZależnePo | Opcjonalny ciąg znaków. Określa plik, od który plik zależy od poprawnego skompilowania. |
| Generator | Wymagany ciąg. Nazwa dowolnego generatora plików, który działa na tym elemencie. |
| LastGenOutput (LastGenOutput) | Wymagany ciąg. Nazwa pliku, który został utworzony przez dowolnego generatora plików, który został uruchomiony na tym elemencie. |
| Obszar CustomToolNamespace | Wymagany ciąg. Obszar nazw, w którym każdy generator plików, który działa na tym elemencie, powinien utworzyć kod. |
| Link | Opcjonalny ciąg znaków. Ścieżka notacyjna, która ma być wyświetlana, jeśli plik fizycznie znajduje się poza wpływem projektu. |
| Stan publikacji | Wymagany ciąg. Stan publikacji treści:<br /><br /> - Domyślnie<br />- W zestawie<br />- Wykluczone<br />- Plik danych<br />- Warunek wstępny |
| Isassembly (izmont) | Opcjonalny wartość logiczna. Określa, czy plik jest złożeniem. |
| Widoczne | Opcjonalny wartość logiczna. Wskazuje, czy plik ma być wyświetlany w **Eksploratorze rozwiązań** w programie Visual Studio. |
| CopyToOutputDirectory (CopyToOutputDirectory) | Opcjonalny ciąg znaków. Określa, czy plik ma być kopiowany do katalogu wyjściowego. Wartości to:<br /><br /> 1. Nigdy<br />2. Zawsze<br />3. ZachowaćZachód |

### <a name="none"></a>Brak

 Reprezentuje pliki, które powinny mieć żadną rolę w procesie kompilacji.

| Nazwa metadanych elementu | Opis |
|-----------------------| - |
| ZależnePo | Opcjonalny ciąg znaków. Określa plik, od który plik zależy od poprawnego skompilowania. |
| Generator | Wymagany ciąg. Nazwa dowolnego generatora plików, który jest uruchamiany na tym elemencie. |
| LastGenOutput (LastGenOutput) | Wymagany ciąg. Nazwa pliku, który został utworzony przez dowolnego generatora plików, który działał na tym elemencie. |
| Obszar CustomToolNamespace | Wymagany ciąg. Obszar nazw, w którym każdy generator plików, który działa na tym elemencie, powinien utworzyć kod. |
| Link | Opcjonalny ciąg znaków. Ścieżka notacyjna, która ma być wyświetlana, jeśli plik fizycznie znajduje się poza wpływem projektu. |
| Widoczne | Opcjonalny wartość logiczna. Wskazuje, czy plik ma być wyświetlany w **Eksploratorze rozwiązań** w programie Visual Studio. |
| CopyToOutputDirectory (CopyToOutputDirectory) | Opcjonalny ciąg znaków. Określa, czy plik ma być kopiowany do katalogu wyjściowego. Wartości to:<br /><br /> 1. Nigdy<br />2. Zawsze<br />3. ZachowaćZachód |

### <a name="assemblymetadata"></a>AssemblyMetadata (Meada zestawu)

 Reprezentuje atrybuty zestawu, `[AssemblyMetadata(key, value)]`które mają być generowane jako .

| Nazwa metadanych elementu | Opis |
|-----------------------| - |
| Uwzględnij | Staje się pierwszym parametrem (kluczem) w konstruktorze atrybutów. `AssemblyMetadataAttribute` |
| Wartość | Wymagany ciąg. Staje się drugim parametrem (wartością) w konstruktorze atrybutów. `AssemblyMetadataAttribute` |

> [!NOTE]
> Dotyczy to projektów przy użyciu tylko sdk .NET Core.

### <a name="baseapplicationmanifest"></a>BaseApplicationManifest

 Reprezentuje manifest aplikacji podstawowej dla kompilacji i zawiera informacje o zabezpieczeniach wdrażania ClickOnce.

### <a name="codeanalysisimport"></a>Analiza koduWziomanie

 Reprezentuje projekt FxCop do zaimportowania.

### <a name="import"></a>Import

 Reprezentuje zestawy, których przestrzenie nazw powinny być importowane przez kompilator języka Visual Basic.

## <a name="see-also"></a>Zobacz też

- [Typowe właściwości projektu MSBuild](../msbuild/common-msbuild-project-properties.md)
