---
title: IDebugProperty3::CreateObjectID | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::CreateObjectID
helpviewer_keywords:
- IDebugProperty3::CreateObjectID
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d3993d674f029260dbe32d16c576cb239ff8d6d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721173"
---
# <a name="idebugproperty3createobjectid"></a>IDebugProperty3::CreateObjectID
Tworzy unikatowy identyfikator dla tej właściwości, aby upewnić się, że jest unikatowy wśród wszystkich innych właściwości.

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
 Jeśli się `S_OK`powiedzie, zwraca ; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda jest wywoływana, gdy menedżer debugowania sesji chce upewnić się, że ta właściwość jest jednoznacznie identyfikowana między wszystkimi innymi właściwościami. Aparat debugowania (DE) obsługuje tę metodę, chyba że właściwości, które zajmuje się są już jednoznacznie zidentyfikowane. Jeśli DE nie obsługuje tej metody, zwraca `E_NOTIMPL`.

 Każdy unikatowy identyfikator `CreateObjectID` utworzony za pomocą jest niszczony, gdy [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) metoda jest wywoływana; to również sygnalizuje koniec potrzeby jednoznacznej identyfikacji tej właściwości.

> [!NOTE]
> Nie ma metody, aby pobrać ten unikatowy identyfikator, więc DE można zrobić, `CreateObjectID` co chce dla unikatowych identyfikatorów, gdy metoda jest wywoływana.

## <a name="see-also"></a>Zobacz też
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
