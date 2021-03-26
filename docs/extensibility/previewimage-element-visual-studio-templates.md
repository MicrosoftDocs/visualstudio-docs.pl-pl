---
title: PreviewImage, element (szablony Visual Studio) | Microsoft Docs
description: Dowiedz się więcej o elemencie PreviewImage i sposobie określania nazwy pliku dla obrazu podglądu, który będzie wyświetlany w oknie dialogowym Nowy projekt lub Dodaj nowy element.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <PreviewImage> Element (Visual Studio Templates)
- PreviewImage Element (Visual Studio Templates)
ms.assetid: d1796f20-523b-4e0d-8ac3-ca87f3b5a9b6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6fc7a370885d24a586262bebd4182daacd84a9b2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090229"
---
# <a name="previewimage-element-visual-studio-templates"></a>PreviewImage, element (szablony Visual Studio)
Określa obraz podglądu jako nazwę pliku dla obrazu podglądu, który będzie wyświetlany w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** .

 \<VSTemplate> \<TemplateData>
 \<PreviewImage>

## <a name="syntax"></a>Składnia

```
<PreviewImage>"filename"</PreviewImage>
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Element wymagany.<br /><br /> Klasyfikuje szablon i definiuje sposób jego wyświetlania w oknie dialogowym **Nowy projekt** lub **Dodaj nowy element** .|

## <a name="text-value"></a>Wartość tekstowa
 Wartość tekstowa jest wymagana.

 Tekst musi być ciągiem, który reprezentuje nazwę pliku.

## <a name="remarks"></a>Uwagi
 `PreviewImage` jest elementem opcjonalnym.

## <a name="see-also"></a>Zobacz też
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
