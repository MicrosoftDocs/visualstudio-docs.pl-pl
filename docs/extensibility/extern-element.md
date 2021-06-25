---
title: Extern, element | Microsoft Docs
description: Extern element odwołuje się do wszystkich zewnętrznych plików nagłówka (h) w celu scalenia z plikiem vsct w czasie kompilacji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 502b93f18aacfed26d3ea440c017e6de5281a35d
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900190"
---
# <a name="extern-element"></a>Extern, element
Extern element odwołuje się do wszystkich zewnętrznych plików nagłówka *(.h)* w celu scalenia z *plikiem .vsct* w czasie kompilacji. Pliki, które mają zostać scalone, muszą znajdować się w ścieżce Dołączania nadanej kompilatorowi VSCT lub przywołynej przez [element Include](../extensibility/include-element.md). Pliki mogą być innymi *plikami vsct* lub plikami nagłówków C++.

 Definicje w plikach nagłówkowych muszą mieć postać "#define [Symbol] [Wartość]" Wartość może być innym symbolem, jeśli została wcześniej zdefiniowana. Definicje mogą być używane w instrukcjach warunkowych elementów poleceń. Każdy symbol, który nie jest faktycznie używany, zostanie odrzucony.

 CommandTable, element Extern, element

## <a name="syntax"></a>Składnia

```xml
<Extern href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|Href|Wymagane. Ścieżka do pliku nagłówkowego:<br /><br /> href="stdidcmd.h"|
|Warunek|Opcjonalny. Zobacz [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|
|language|Opcjonalny. Domyślny język wszystkich elementów [\<Strings>](../extensibility/strings-element.md) w tabeli poleceń:<br /><br /> language="en-us"|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|Brak.|Brak.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[CommandTable, element](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy reprezentujące polecenia — czyli elementy menu, menu, paski narzędzi i pola kombi — które pakiet VSPackage udostępnia ideom IDE.|

## <a name="example"></a>Przykład

```xml
<?xml version="1.0" encoding="utf-8"?>
<CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-
  18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema">
    <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/>
    ...
  <Commands package="guidMyPackage">
</CommandTable>
```

## <a name="see-also"></a>Zobacz także
- [Visual Studio plików tabeli poleceń (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Jak pakiet VSPackages dodaje elementy interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
