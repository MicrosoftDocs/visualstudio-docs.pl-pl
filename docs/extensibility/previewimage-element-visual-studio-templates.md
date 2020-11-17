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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 326588259203224d3f70b505af8437af22930faa
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2020
ms.locfileid: "94672349"
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

## <a name="see-also"></a>Zobacz także
- [Odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Tworzenie szablonów projektów i elementów](../ide/creating-project-and-item-templates.md)
