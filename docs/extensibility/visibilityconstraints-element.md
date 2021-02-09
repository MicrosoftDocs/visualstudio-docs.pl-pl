---
title: VisibilityConstraints — Element | Microsoft Docs
description: Element VisibilityConstraints określa statyczną widoczność grup poleceń i pasków narzędzi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bb6047c98031c484f6a0a51ab2a393a2a46bb2a2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926096"
---
# <a name="visibilityconstraints-element"></a>VisibilityConstraints, element
Element VisibilityConstraints określa statyczną widoczność grup poleceń i pasków narzędzi. Widoczność jest najpierw kontrolowana przez [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zintegrowane środowisko programistyczne (IDE) bez ładowania pakietu VSPackage.

## <a name="syntax"></a>Składnia

```xml
<VisibilityConstraints>
  <VisibilityItem />
  <VisibilityItem />
</VisibilityConstraints>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|Warunek|Opcjonalny. Zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[VisibilityItem, element](../extensibility/visibilityitem-element.md)|Określa statyczną widoczność poleceń i pasków narzędzi.|
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Określa statyczną widoczność grup poleceń i pasków narzędzi.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element polecenia](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy, które reprezentują polecenia (na przykład elementy menu, menu, paski narzędzi i pola kombi), które pakietu VSPackage zapewnia IDE.|

## <a name="example"></a>Przykład

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Zobacz także
- [VisibilityItem, element](../extensibility/visibilityitem-element.md)
- [Tabela poleceń programu Visual Studio (. Vsct) — pliki](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
