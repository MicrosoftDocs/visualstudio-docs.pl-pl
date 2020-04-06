---
title: IDebugObject2::GetBackingFieldForProperty | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b5b9fed9b071f34c119c8e4a5af12c1df7990f4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726242"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Pobiera pole lub zmienną (jeśli istnieje), które mogą być kopii zapasowej właściwości reprezentowane przez ten obiekt.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetBackingFieldForProperty(
   IDebugObject2** ppObject
);
```

```csharp
int GetBackingFieldForProperty(
   out IDebugObject2 ppObject
);
```

## <a name="parameters"></a>Parametry
`ppObject`\
[na zewnątrz] [Obiekt IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) opisujący pole zapasowe.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) obiekt reprezentuje właściwość klasy kodu zarządzanego, czyli metodę z get i/lub set akcesor. Takie właściwości zazwyczaj wymagają zmiennej, aby zawierać wartość manipulowane przez właściwość. Ta zmienna jest znana jako pole zapasowe. Jeśli nie ma pola zapasowego dla obiektu, upewnij się, że zwraca wartość null: niektórzy obiekt wywołujący mogą nie zwracać `ppObject`uwagi na wartość zwracaną, ale zamiast tego będą patrzeć, czy wartość null została zwrócona w programie .

## <a name="see-also"></a>Zobacz też
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
