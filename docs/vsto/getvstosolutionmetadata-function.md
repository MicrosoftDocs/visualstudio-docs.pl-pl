---
title: GetVstoSolutionMetadata, funkcja
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: aebbedaab7e7ac342f6d6ace191d820f6a0c8090
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85520188"
---
# <a name="getvstosolutionmetadata-function"></a>GetVstoSolutionMetadata, funkcja
  Ten interfejs API obsługuje infrastrukturę pakietu Office i nie jest przeznaczony do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```csharp
HRESULT WINAPI GetVstoSolutionMetadata(
    LPCWSTR lpwszSolutionMetadataKey,
    ISolutionMetadata** ppSolutionInfo
);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*lpwszSolutionMetadataKey*|Nie używaj.|
|*ppSolutionInfo*|Nie używaj.|

## <a name="return-value"></a>Wartość zwracana
 Jeśli funkcja się powiedzie, zwraca **S_OK**. Jeśli funkcja nie powiedzie się, zwraca kod błędu.
