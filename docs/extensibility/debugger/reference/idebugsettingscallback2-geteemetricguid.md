---
title: IDebugSettingsCallback2::GetEEMetricGuid | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricGuid
ms.assetid: 3d70c19a-595d-44f1-a7b3-a0cf8f15e371
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d8829afadbd2f02b9b87f2beb84088aeeb447e66
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212103"
---
# <a name="idebugsettingscallback2geteemetricguid"></a>IDebugSettingsCallback2::GetEEMetricGuid
Pobiera unikatowy identyfikator dla metryki ewaluatora wyrażeń nadać jej nazwę.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetEEMetricGuid(
   REFGUID guidLang,
   REFGUID guidVendor,
   LPCWSTR pszMetric,
   GUID*   pguidValue
);
```

```csharp
HRESULT GetEEMetricGuid(
   ref Guid guidLang,
   ref Guid guidVendor,
   string   pszMetric,
   out Guid pguidValue
);
```

## <a name="parameters"></a>Parametry
`guidLang`\
[in] Unikatowy identyfikator języka programowania.

`guidVendor`\
[in] Unikatowy identyfikator dostawcy.

`pszMetric`\
[in] Nazwa metryki.

`pguidValue`\
[out] Zwraca unikatowy identyfikator metryki.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)