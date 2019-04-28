---
title: Umieść Element | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Include
helpviewer_keywords:
- Include element (VSCT XML schema)
- VSCT XML schema elements, Include
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d77cca0b197f939170fc92f4d7d07bcadae8b53d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62861804"
---
# <a name="include-element"></a>Umieść element
Include element Określa plik, który może znajdować się w podanym ścieżkę załączania dla wstawiania do bieżącego pliku.  Wszystkie symbole i typy zdefiniowane staną się częścią wynik.

## <a name="syntax"></a>Składnia

```csharp
<Include href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|{1&gt;href&lt;1}|Wymagana. Ścieżka do pliku nagłówka:<br /><br /> href="stdidcmd.h"|
|Warunek|Opcjonalna. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|Brak.|Brak.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[CommandTable, element](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy, które reprezentują poleceń — czyli elementy menu, menu, paski narzędzi i pola kombi — zapewniającej pakietu VSPackage IDE.|

## <a name="example"></a>Przykład

```
<Include href="PackagePlacements.vsct"/>
```

## <a name="see-also"></a>Zobacz także
- [Pliki tabeli (vsct) polecenia programu Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)