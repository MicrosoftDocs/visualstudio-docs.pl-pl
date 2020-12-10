---
title: Zdefiniuj element | Microsoft Docs
description: Element define definiuje nazwę symbolu i parę wartości. Ten symbol może być oceniany przez atrybuty warunkowe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a427371afe55b6ea4ee20f658e683b9dcdb8fbe2
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996243"
---
# <a name="define-element"></a>Zdefiniuj element
Definiuje nazwę symbolu i parę wartości. Ten symbol może być oceniany przez atrybuty warunkowe. Aby uzyskać więcej informacji, zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md). Zobacz również [element Symbols](../extensibility/symbols-element.md).

## <a name="syntax"></a>Składnia

```
<Define name="Mode" value="Standard" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|name|Wymagane. Nazwa symbolu:<br /><br /> Nazwa = "tryb"|
|wartość|Wymagane. Wartość symbolu:<br /><br /> wartość = "Standardowa"|
|Warunek|Opcjonalny. Aby uzyskać więcej informacji, zobacz [atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element polecenia](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy, które reprezentują polecenia, które pakietu VSPackage zapewnia zintegrowane środowisko programistyczne (IDE). Na przykład elementy menu, menu, paski narzędzi i pola kombi.|

## <a name="example"></a>Przykład

```
<Define name="DEMO_UI"/>
<Define name="MODE" value="Standard"/>
```

## <a name="see-also"></a>Zobacz także
- [Pliki tabeli poleceń programu Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
