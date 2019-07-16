---
title: IDebugSettingsCallback2::GetMetricGuid | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetMetricGuid
ms.assetid: 91092763-3362-4857-adf0-231bc1254206
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5699e6ca88a91776dee79f9c2c9dae73476a146a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68187923"
---
# <a name="idebugsettingscallback2getmetricguid"></a>IDebugSettingsCallback2::GetMetricGuid
Pobiera unikatowy identyfikator metryki nadać jej nazwę.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetMetricGuid(
   LPCWSTR pszType,
   REFGUID guidSection,
   LPCWSTR pszMetric,
   GUID*   pguidValue
);
```

```csharp
private int GetMetricGuid(
   string   pszType,
   ref Guid guidSection,
   string   pszMetric,
   out Guid pguidValue
);
```

#### <a name="parameters"></a>Parametry
 `pszType`

 [in] Typ metryki.

 `guidSection`

 [in] Unikatowy identyfikator sekcji.

 `pszMetric`

 [in] Nazwa metryki.

 `pguidValue`

 [out] Zwraca unikatowy identyfikator metryki.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)