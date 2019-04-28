---
title: IDebugEvent2::GetAttributes | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 140b47af958e8f4623dd5921aa6046926737cf38
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62920076"
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
Pobiera atrybuty dla tego zdarzenia debugowania.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetAttribute( 
   DWORD* pdwAttrib
);
```

```csharp
int GetAttribute( 
   out uint pdwAttrib
);
```

#### <a name="parameters"></a>Parametry
 `pdwAttrib`

 [out] Kombinacja flag z [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) wyliczenia.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) interfejs jest wspólne dla wszystkich zdarzeń. Metoda opisuje typ zdarzenia; na przykład jest to zdarzenie synchronicznego lub asynchronicznego i zatrzymywania zdarzenie jest.

## <a name="see-also"></a>Zobacz też
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)