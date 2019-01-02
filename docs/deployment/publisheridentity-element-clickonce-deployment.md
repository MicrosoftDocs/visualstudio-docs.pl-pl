---
title: '&lt;publisheridentity —&gt; — Element (wdrażanie ClickOnce) | Dokumentacja firmy Microsoft'
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: c9c54b539945093e55aa770f07acc54b589f0c70
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950095"
---
# <a name="ltpublisheridentitygt-element-clickonce-deployment"></a>&lt;publisheridentity —&gt; — element (wdrażanie ClickOnce)
Zawiera informacje o wydawcy, który podpisał tego manifestu wdrażania.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<publisherIdentity  
   name  
   issuerKeyHash  
/>  
```  
  
## <a name="elements-and-attributes"></a>Atrybuty i elementy  
 `publisherIdentity` Element jest wymagany dla podpisanych manifestów. W poniższej tabeli przedstawiono atrybuty `publisherIdentity` obsługuje element.  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`name`|Wymagana. W tym artykule opisano tożsamości innych firm, która opublikowała tę aplikację.|  
|`issuerKeyHash`|Wymagana. Zawiera skrót SHA-1 wystawca certyfikatu klucza publicznego.|  
  
#### <a name="parameters"></a>Parametry  
  
## <a name="property-valuereturn-value"></a>Właściwość wartości/zwracana wartość  
  
## <a name="exceptions"></a>Wyjątki  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="requirements"></a>Wymagania  
  
## <a name="subhead"></a>Podnagłówek