---
title: IDebugSettingsCallback2::GetEEMetricString | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricString
ms.assetid: 85e3c093-6a91-4101-ab32-d8ac6eed4918
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a2091cd052923fe375bf9ba90ffdad50c993f5b4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62868949"
---
# <a name="idebugsettingscallback2geteemetricstring"></a>IDebugSettingsCallback2::GetEEMetricString
Pobiera ciąg wartość metryki ewaluatora wyrażeń nadać jej nazwę.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetEEMetricString(
   REFGUID guidLang,
   REFGUID guidVendor,
   LPCWSTR pszMetric,
   BSTR*   pbstrValue
);
```

```csharp
private int GetEEMetricString(
   ref Guid   guidLang,
   ref Guid   guidVendor,
   string     pszMetric,
   out string pbstrValue
);
```

#### <a name="parameters"></a>Parametry
 `guidLang`

 [in] Unikatowy identyfikator języka programowania.

 `guidVendor`

 [in] Unikatowy identyfikator dostawcy.

 `pszMetric`

 [in] Nazwa metryki.

 `pbstrValue`

 [out] Zwraca ciąg wartość metryki.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz też
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)