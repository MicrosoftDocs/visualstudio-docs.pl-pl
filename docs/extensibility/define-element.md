---
title: Definiowanie elementu | Microsoft Docs
description: Zdefiniuj element definiuje nazwę symbolu i parę wartości. Ten symbol może być oceniany przez atrybuty warunkowe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 409621410db727f933e41bae894f125dc877b4c2
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898048"
---
# <a name="define-element"></a>Define, element
Definiuje parę nazwa symbolu i wartość. Ten symbol może być oceniany przez atrybuty warunkowe. Aby uzyskać więcej informacji, zobacz [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md). Zobacz też [element Symbols](../extensibility/symbols-element.md).

## <a name="syntax"></a>Składnia

```
<Define name="Mode" value="Standard" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|name|Wymagane. Nazwa symbolu:<br /><br /> name="Mode"|
|wartość|Wymagane. Wartość symbolu:<br /><br /> value="Standardowa"|
|Warunek|Opcjonalny. Aby uzyskać więcej informacji, zobacz [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[CommandTable, element](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy reprezentujące polecenia, które pakiet VSPackage zapewnia zintegrowanemu środowisku projektowemu (IDE). Na przykład elementy menu, menu, paski narzędzi i pola kombi.|

## <a name="example"></a>Przykład

```
<Define name="DEMO_UI"/>
<Define name="MODE" value="Standard"/>
```

## <a name="see-also"></a>Zobacz także
- [Visual Studio plików tabeli poleceń (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
