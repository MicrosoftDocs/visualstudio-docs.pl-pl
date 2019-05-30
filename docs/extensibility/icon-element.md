---
title: Icon, Element | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Icon
- Icon element (VSCT XML schema)
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd56391084788729c0f8439728f9afffd59da946
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66311251"
---
# <a name="icon-element"></a>Icon, element
Atrybut guid tagu ikona jest identyfikatorem guid zdefiniowanych mapy bitowej. `id` Atrybut wybiera gniazda na pasku mapy bitowej. Ten element jest opcjonalny. Jeśli ten element nie jest uwzględniony wartość **guidOfficeIcon:msotcidNoIcon** będzie wynikać.

## <a name="syntax"></a>Składnia

```xml
<Icon guid="guidImages" id="bmpPic1" />
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

|Atrybut|Opis|
|---------------|-----------------|
|Identyfikator GUID|Wymagana. Identyfikator guid zdefiniowanych mapy bitowej.|
|identyfikator|Wymagana. Wybiera gniazda na pasku mapy bitowej.|

### <a name="child-elements"></a>Elementy podrzędne

|Element|Opis|
|-------------|-----------------|
|Brak.|Brak.|

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[Buttons, element](../extensibility/buttons-element.md)||

## <a name="see-also"></a>Zobacz także
- [Pliki tabeli (vsct) polecenia programu Visual Studio](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)