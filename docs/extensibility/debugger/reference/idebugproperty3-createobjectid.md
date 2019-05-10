---
title: IDebugProperty3::CreateObjectID | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c511922be4a1ff353d4efde01a74fc43e233cba0
ms.sourcegitcommit: 50f0c3f2763a05de8482b3579026d9c76c0e226c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/09/2019
ms.locfileid: "65458851"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Tworzy unikatowy identyfikator dla tej właściwości, aby upewnić się, że jest ona unikatowa wśród wszystkich innych właściwości.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CreateObjectID(
   void
);
```

```csharp
int CreateObjectID();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest wywoływana, gdy Menedżer debugowania sesji chce mieć pewność, ta właściwość jest unikatowo identyfikowana przez inne właściwości. Aparat debugowania (DE) obsługuje tę metodę, chyba że właściwości, które zajmuje się on już unikatowo zidentyfikować. Jeśli DE nie obsługuje tej metody, zwraca `E_NOTIMPL`.

 Wszelkie Unikatowy identyfikator utworzony za pomocą `CreateObjectID` jest niszczony, kiedy [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) wywoływana jest metoda; to również sygnalizuje koniec potrzebę unikatowo identyfikujący tę właściwość.

> [!NOTE]
> Nie istnieje metoda do pobrania to unikatowy identyfikator, więc DE można zrobić, niezależnie od rodzaju chce uzyskać unikatowe identyfikatory podczas `CreateObjectID` metoda jest wywoływana.

## <a name="see-also"></a>Zobacz także
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)