---
title: IDebugEnumField::GetUnderlyingSymbol | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetUnderlyingSymbol
helpviewer_keywords:
- IDebugEnumField::GetUnderlyingSymbol method
ms.assetid: c3b8a117-6708-4cfd-8ffc-5f007d706bc5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9b6b90f388f93bc7cfc2c246c529217bcdb00fa9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920275"
---
# <a name="idebugenumfieldgetunderlyingsymbol"></a>IDebugEnumField::GetUnderlyingSymbol
Ta metoda zwraca [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) reprezentujący nazwę wyliczenia.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetUnderlyingSymbol(
   IDebugField** ppField
);
```

```csharp
int GetUnderlyingSymbol(
   out IDebugField ppField
);
```

#### <a name="parameters"></a>Parametry
 `ppField`

 [out] Zwraca [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) opisujące nazwę tego wyliczenia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Nazwa wyliczenia zawiera także typem wyliczenia, który jest powiązany z lokalizacji w pamięci, za pomocą [powiązać](../../../extensibility/debugger/reference/idebugbinder-bind.md).

## <a name="see-also"></a>Zobacz też
- [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md)