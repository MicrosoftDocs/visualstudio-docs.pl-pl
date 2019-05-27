---
title: IDebugSettingsCallback2::GetEEMetricDword | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricDword
ms.assetid: c5f8f417-0ef0-4fd0-a779-b0a8ead4effe
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e3661186357e82170cc67f6e3744e8662ebae76c
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212137"
---
# <a name="idebugsettingscallback2geteemetricdword"></a>IDebugSettingsCallback2::GetEEMetricDword
Pobiera wartość, która odnosi się do określonej metryki Ewaluator wyrażeń.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetEEMetricDword(
   REFGUID guidLang,
   REFGUID guidVendor,
   LPCWSTR pszMetric,
   DWORD*  pdwValue
);
```

```csharp
private int GetEEMetricDword(
   ref Guid guidLang,
   ref Guid guidVendor,
   string   pszMetric,
   out uint pdwValue
);
```

## <a name="parameters"></a>Parametry
`guidLang`\
[in] Unikatowy identyfikator języka programowania.

`guidVendor`\
[in] Unikatowy identyfikator dostawcy.

`pszMetric`\
[in] Nazwa metryki.

`pdwValue`\
[out] Zwraca wartość, która odpowiada ciągowi metryki.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="see-also"></a>Zobacz także
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)