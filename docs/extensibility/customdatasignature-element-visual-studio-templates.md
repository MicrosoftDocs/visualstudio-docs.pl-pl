---
title: CustomDataSignature, Element (szablony Visual Studio) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <CustomDataSignature> Element (Visual Studio Templates)
- CustomDataSignature Element (Visual Studio Templates)
ms.assetid: 8c3db51d-7014-4484-802a-15aa1353dbdb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db2b4d089495245d1a37469df1dc43a19be31866
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66351978"
---
# <a name="customdatasignature-element-visual-studio-templates"></a>CustomDataSignature, element (szablony Visual Studio)
Określa podpis tekstowy do lokalizowania danych niestandardowych.

 \<VSTemplate> \<TemplateData> \<CustomDataSignature>

## <a name="syntax"></a>Składnia

```
<CustomDataSignature>"string"</CustomDataSignature>
```

## <a name="attributes-and-elements"></a>Atrybuty i elementy
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty
 Brak.

### <a name="child-elements"></a>Elementy podrzędne
 Brak.

### <a name="parent-elements"></a>Elementy nadrzędne

|Element|Opis|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób wyświetlania albo **nowy projekt** lub **Dodaj nowy element** okno dialogowe.|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Tekst jest ciąg, który ma podpis tekst, który jest wymagany do zlokalizowania danych niestandardowych.

## <a name="remarks"></a>Uwagi
 `CustomDataSignature` element jest opcjonalny.

## <a name="see-also"></a>Zobacz także
- [Visual Studio Template schema reference](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)