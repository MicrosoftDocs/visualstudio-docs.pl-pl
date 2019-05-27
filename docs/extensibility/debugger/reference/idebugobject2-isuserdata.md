---
title: IDebugObject2::IsUserData | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c9d791a181227b481f27f9347897fce4dda158a2
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66209783"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
Określa, czy obiekt reprezentuje dane użytkownika.

## <a name="syntax"></a>Składnia

```cpp
HRESULT IsUserData(
   BOOL* pfUser
);
```

```csharp
int IsUserData(
   out int pfUser
);
```

## <a name="parameters"></a>Parametry
`pfUser`\
[out] Zwraca wartość różną od zera (`TRUE`) obiekt reprezentuje dane użytkownika; wartość zero (`FALSE`) Jeśli nie jest.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Dane użytkownika są dowolnego obiektu, który jest częścią modułu wyznaczony jako JustMyCode (konfigurowanych przez użytkownika opcji oznaczający moduł jako kod użytkownika i dlatego są widoczne w śladzie stosu).

## <a name="see-also"></a>Zobacz także
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)