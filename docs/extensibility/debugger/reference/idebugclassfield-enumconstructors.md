---
title: IDebugClassField::EnumConstructors | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5ecc2e2fba9dbddc12a58866c7edcde51b148af1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62922703"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
Tworzy moduł wyliczający dla konstruktorów dla tej klasy.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumConstructors( 
   CONSTRUCTOR_ENUM   cMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumConstructors(
   CONSTRUCTOR_ENUM     cMatch,
   out IEnumDebugFields ppEnum
);
```

#### <a name="parameters"></a>Parametry
 `cMatch`

 [in] Wartość z zakresu od [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) wyliczenie, który określa typ konstruktorów do wyliczenia.

 `ppEnum`

 [out] Zwraca [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) obiekt reprezentujący listę konstruktorów. Zwraca wartość null, jeśli nie ma żadnych konstruktorów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca wartość S_OK lub zwraca wartość S_FALSE, jeśli nie ma żadnych konstruktorów. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Każdy element wyliczenia jest [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) Obiekt opisujący metodę konstruktora.

 Lista konstruktory zwykle nie ma konstruktory domyślne, dostarczone przez kompilator.

## <a name="see-also"></a>Zobacz też
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)