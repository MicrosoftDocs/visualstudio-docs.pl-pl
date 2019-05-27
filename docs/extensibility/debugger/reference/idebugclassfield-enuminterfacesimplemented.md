---
title: IDebugClassField::EnumInterfacesImplemented | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 74a1de38344b8570df0b5381842be508e45c5fdb
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/24/2019
ms.locfileid: "66203198"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
Tworzy moduł wyliczający interfejsy implementowane przez tę klasę.

## <a name="syntax"></a>Składnia

```cpp
HRESULT EnumInterfacesImplemented( 
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumInterfacesImplemented(
   out IEnumDebugFields ppEnum
);
```

## <a name="parameters"></a>Parametry
`ppEnum`\
[out] Zwraca [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) obiekt reprezentujący listy interfejsów implementowanych. Zwraca wartość null, jeśli brak interfejsów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca wartość S_OK lub zwraca wartość S_FALSE, jeśli żadne interfejsy implementowane w tej klasie. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Każdy element wyliczenia jest [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) Obiekt opisujący interfejs. Należy zauważyć, że niezarządzane [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] kod nie używa interfejsów jako osobne jednostki, ta metoda zawsze zwraca wartość null dla niezarządzanych [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] kodu.

## <a name="see-also"></a>Zobacz także
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)