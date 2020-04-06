---
title: IDebugEvent2::GetAttributes | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ffc3fc1b7988401611190fdf09e8041bf0dc5b1a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729954"
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

## <a name="parameters"></a>Parametry
`pdwAttrib`\
[na zewnątrz] Kombinacja flag z wyliczenia [EVENTATTRIBUTES.](../../../extensibility/debugger/reference/eventattributes.md)

## <a name="return-value"></a>Wartość zwracana
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Interfejs [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) jest wspólny dla wszystkich zdarzeń. Ta metoda opisuje typ zdarzenia; na przykład jest zdarzenie synchroniczne lub asynchroniczne i jest to zdarzenie zatrzymania.

## <a name="see-also"></a>Zobacz też
- [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)
- [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
