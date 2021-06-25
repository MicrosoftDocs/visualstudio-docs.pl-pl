---
title: Include, element | Microsoft Docs
description: Include element określa plik, który może się znaleźć w podanej ścieżce dołączania do wstawienia do bieżącego pliku.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Include
helpviewer_keywords:
- Include element (VSCT XML schema)
- VSCT XML schema elements, Include
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d0005626c7fbb276775661a7cfb73d17f5e20d62
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899359"
---
# <a name="include-element"></a>Include, element
Include element określa plik, który może się znaleźć w podanej ścieżce dołączania do wstawienia do bieżącego pliku.  Wszystkie zdefiniowane symbole i typy staną się częścią skompilowanego wyniku.

## <a name="syntax"></a>Składnia

```csharp
<Include href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|Href|Wymagane. Ścieżka do pliku nagłówkowego:<br /><br /> href="stdidcmd.h"|
|Warunek|Opcjonalny. Zobacz [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|Brak.|Brak.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[CommandTable, element](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy reprezentujące polecenia — czyli elementy menu, menu, paski narzędzi i pola kombi — które pakiet VSPackage udostępnia ideom IDE.|

## <a name="example"></a>Przykład

```
<Include href="PackagePlacements.vsct"/>
```

## <a name="see-also"></a>Zobacz także
- [Visual Studio plików tabeli poleceń (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
