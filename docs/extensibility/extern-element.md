---
title: Element extern | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 2cf6f9db77abaa7034af8d074b9833a4c1560f07
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711488"
---
# <a name="extern-element"></a>Element Extern
Element Extern odwołuje się do wszystkich plików nagłówka zewnętrznego (*.h*) do scalenia z plikiem *vsct* w czasie kompilacji. Pliki, które mają zostać scalone, muszą znajdować się na ścieżce Dołącz, danej kompilatorze VSCT lub do których odwołuje się [element Include](../extensibility/include-element.md). Pliki mogą być inne pliki *vsct* lub C++ plików nagłówkowych.

 Definicje w plikach nagłówkowych muszą mieć formę "#define [Symbol] [Value]" Wartość może być innym symbolem, jeśli jest wcześniej zdefiniowana. Definicje mogą być używane w instrukcjach warunkowych elementów poleceń. Każdy symbol, który nie został faktycznie użyty, zostanie odrzucony.

 Element Extern tabeli polecenia

## <a name="syntax"></a>Składnia

```xml
<Extern href="stdidcmd.h" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|Href|Wymagany. Ścieżka do pliku nagłówka:<br /><br /> href="stdidcmd.h"|
|Warunek|Element opcjonalny. Zobacz [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|
|language|Element opcjonalny. Domyślny język wszystkich [ \<ciągów>](../extensibility/strings-element.md) elementów w tabeli poleceń:<br /><br /> language="en-us"|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|Brak.|Brak.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CommandTable](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy, które reprezentują polecenia — czyli elementy menu, menu, paski narzędzi i pola kombi — które vspackage zapewnia IDE.|

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

## <a name="see-also"></a>Zobacz też
- [Pliki tabeli poleceń programu Visual Studio (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Jak vspackages dodać elementy interfejsu użytkownika](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Polecenia, menu i paski narzędzi](../extensibility/internals/commands-menus-and-toolbars.md)
