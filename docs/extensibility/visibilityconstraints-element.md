---
title: VisibilityConstraints, element | Microsoft Docs
description: Element VisibilityConstraints określa statyczną widoczność grup poleceń i pasków narzędzi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VisibilityConstraints
helpviewer_keywords:
- VSCT XML schema elements, VisibilityConstraints
- VisibilityConstraints element (VSCT XML schema)
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 160a3950e31567aafc2d675971fd7263adb2ad5b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905465"
---
# <a name="visibilityconstraints-element"></a>VisibilityConstraints, element
Element VisibilityConstraints określa statyczną widoczność grup poleceń i pasków narzędzi. Widoczność jest najpierw kontrolowana przez zintegrowane [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] środowisko projektowe (IDE) bez ładowania pakietów VSPackage.

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
|Warunek|Opcjonalny. Zobacz [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|[VisibilityItem, element](../extensibility/visibilityitem-element.md)|Określa statyczną widoczność poleceń i pasków narzędzi.|
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Określa statyczną widoczność grup poleceń i pasków narzędzi.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[CommandTable, element](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy reprezentujące polecenia (na przykład elementy menu, menu, paski narzędzi i pola kombi) zapewniane przez pakiet VSPackage dla środowiska IDE.|

## <a name="example"></a>Przykład

```xml
<VisibilityConstraints>
  <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget"
    context="guidNotViewSourceMode"/>
</VisibilityConstraints>
```

## <a name="see-also"></a>Zobacz także
- [VisibilityItem, element](../extensibility/visibilityitem-element.md)
- [Visual Studio tabeli poleceń (. Pliki Vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
