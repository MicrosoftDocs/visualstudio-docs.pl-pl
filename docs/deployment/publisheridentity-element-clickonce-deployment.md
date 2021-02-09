---
title: '&lt;publisherIdentity —, &gt; element (wdrażanie ClickOnce) | Microsoft Docs'
description: Element publisherIdentity — zawiera informacje o wydawcy, który podpisał manifest wdrożenia. Element jest wymagany dla podpisanych manifestów.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publisherIdentity Element [ClickOnce deployment manifest], introduction
- required element for signed manifests [ClickOnce], publisherIdentity Element
- publisherIdentity Element [ClickOnce deployment manifest], syntax, elements, and attributes
ms.assetid: 34c579db-d2f2-4b66-b9c8-47207f33d950
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 65f225f8e3dd3f6d2b3afb2d2a5284d172d4fab1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99891296"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisherIdentity —, &gt; element (wdrażanie ClickOnce)
Zawiera informacje o wydawcy, który podpisał ten manifest wdrożenia.

## <a name="syntax"></a>Składnia

```xml
<publisherIdentity
   name
   issuerKeyHash
/>
```

## <a name="elements-and-attributes"></a>Elementy i atrybuty
 `publisherIdentity`Element jest wymagany dla podpisanych manifestów. W poniższej tabeli przedstawiono atrybuty `publisherIdentity` obsługiwane przez element.

|Atrybut|Opis|
|---------------|-----------------|
|`name`|Wymagane. Opisuje tożsamość strony, która opublikowała tę aplikację.|
|`issuerKeyHash`|Wymagane. Zawiera skrót SHA-1 klucza publicznego wystawcy certyfikatu.|

#### <a name="parameters"></a>Parametry

## <a name="property-valuereturn-value"></a>Wartość właściwości/zwracana wartość

## <a name="exceptions"></a>Wyjątki

## <a name="remarks"></a>Uwagi

## <a name="requirements"></a>Wymagania

## <a name="subhead"></a>Podnagłówek