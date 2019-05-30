---
title: IDebugSettingsCallback2::GetEEMetricDword | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricDword
ms.assetid: c5f8f417-0ef0-4fd0-a779-b0a8ead4effe
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 17ba8b4410b42b6369831c1be075042121b84170
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322166"
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