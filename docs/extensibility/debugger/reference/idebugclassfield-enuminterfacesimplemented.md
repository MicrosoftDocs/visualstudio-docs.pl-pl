---
description: Tworzy moduł wyliczający dla interfejsów implementowanych przez tę klasę.
title: 'IDebugClassField:: EnumInterfacesImplemented | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1763cbcd0a1c61150a054752c94a42f10127251a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105088617"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
Tworzy moduł wyliczający dla interfejsów implementowanych przez tę klasę.

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
określoną Zwraca obiekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) reprezentujący listę zaimplementowanych interfejsów. Zwraca wartość null, jeśli nie ma żadnych interfejsów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca S_OK lub zwraca S_FALSE, jeśli nie ma żadnych interfejsów zaimplementowanych w tej klasie. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Każdy element wyliczenia to obiekt [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) opisujący interfejs. Należy zauważyć, że kod niezarządzany nie [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] używa interfejsów jako jednostki dyskretnej, dlatego ta metoda zawsze zwraca wartość null dla niezarządzanego [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] kodu.

## <a name="see-also"></a>Zobacz też
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
