---
title: '&lt;publisherIdentity —, &gt; element (wdrażanie ClickOnce) | Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 995b002784c1e76ceed36e51edb1ae893448f448
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62927542"
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
|`name`|Wymagany. Opisuje tożsamość strony, która opublikowała tę aplikację.|
|`issuerKeyHash`|Wymagany. Zawiera skrót SHA-1 klucza publicznego wystawcy certyfikatu.|

#### <a name="parameters"></a>Parametry

## <a name="property-valuereturn-value"></a>Wartość właściwości/zwracana wartość

## <a name="exceptions"></a>Wyjątki

## <a name="remarks"></a>Uwagi

## <a name="requirements"></a>Wymagania

## <a name="subhead"></a>Podnagłówek