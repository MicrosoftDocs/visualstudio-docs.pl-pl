---
title: Zdefiniuj element | Dokumenty firmy Microsoft
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
ms.openlocfilehash: fc09de1d822f41b25397c7a56c7cce4449a9e551
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712272"
---
# <a name="define-element"></a>Zdefiniuj element
Definiuje nazwę symbolu i parę wartości. Ten symbol można ocenić za pomocą atrybutów warunkowych. Aby uzyskać więcej informacji, zobacz [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md). Zobacz też [symbole elementu](../extensibility/symbols-element.md).

## <a name="syntax"></a>Składnia

```
<Define name="Mode" value="Standard" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|name|Wymagany. Nazwa symbolu:<br /><br /> name="Tryb"|
|value|Wymagany. Wartość symbolu:<br /><br /> wartość="Standard"|
|Warunek|Element opcjonalny. Aby uzyskać więcej informacji, zobacz [Atrybuty warunkowe](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Element CommandTable](../extensibility/commandtable-element.md)|Definiuje wszystkie elementy, które reprezentują polecenia, które VSPackage zapewnia zintegrowanemu środowisku programistycznemu (IDE). Na przykład elementy menu, menu, paski narzędzi i pola kombi.|

## <a name="example"></a>Przykład

```
<Define name="DEMO_UI"/>
<Define name="MODE" value="Standard"/>
```

## <a name="see-also"></a>Zobacz też
- [Pliki tabeli poleceń programu Visual Studio (vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
