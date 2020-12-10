---
title: Element extern | Microsoft Docs
description: Element extern odwołuje się do wszystkich plików zewnętrznego nagłówka (. h) do scalenia z plikiem. vsct w czasie kompilacji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- Extern
helpviewer_keywords:
- VSCT XML schema elements, Extern
- Extern element (VSCT XML schema)
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e975c3f721d65b64fc7994824406b0c9af13022
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994527"
---
# <a name="extern-element"></a>Element extern
Element extern odwołuje się do wszystkich plików zewnętrznego nagłówka (*. h*) do scalenia z plikiem *. vsct* w czasie kompilacji. Pliki, które mają zostać scalone, muszą znajdować się na ścieżce dołączania do kompilatora VSCT lub odwołania do [elementu include](../extensibility/include-element.md). Pliki mogą być innymi plikami *. vsct* lub plikami nagłówkowe języka C++.

 Definicje w plikach nagłówkowych muszą mieć postać "#define [symbol] [Value]" wartość może być innym symbolem, jeśli jest wcześniej zdefiniowana. Definicje mogą być używane w instrukcjach warunkowych elementów poleceń. Wszelkie symbole, które nie są faktycznie używane, zostaną odrzucone.

 Element extern elementu

## <a name="syntax"></a>Składnia

```xml
<Extern href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|Tag|Wymagane. Ścieżka do pliku nagłówkowego:<br /><br /> href = "Stdidcmd. h"|
|Warunek|Opcjonalny. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|
|language|Opcjonalny. Język domyślny wszystkich [\<Strings>](../extensibility/strings-element.md) elementów w tabeli poleceń:<br /><br /> Language = "pl-US"|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|Brak.|Brak.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element polecenia](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy, które reprezentują polecenia — czyli elementy menu, menu, paski narzędzi i pola kombi, które pakietu VSPackage zapewnia IDE.|

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
- [Pliki tabeli poleceń programu Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Jak pakietów VSPackage Dodawanie elementów interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
