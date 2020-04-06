---
title: IDebugClassField::EnumInterfacesImplemented | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 91d9cac6b695ba2a0d34da776fa79ba62ba2e015
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80734486"
---
# <a name="idebugclassfieldenuminterfacesimplemented"></a>IDebugClassField::EnumInterfacesImplemented
Tworzy moduł wyliczający dla interfejsów zaimplementowanych przez tę klasę.

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
[na zewnątrz] Zwraca obiekt [IEnumDebugFields reprezentujący](../../../extensibility/debugger/reference/ienumdebugfields.md) listę zaimplementowanych interfejsów. Zwraca wartość null, jeśli nie ma żadnych interfejsów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK lub zwraca S_FALSE jeśli nie ma żadnych interfejsów zaimplementowanych w tej klasie. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Każdy element wyliczenia jest [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) obiektu opisujące interfejs. Należy zauważyć, [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] że kod niezarządzany nie używa interfejsów jako jednostki dyskretnej, więc ta metoda zawsze zwraca wartość null dla kodu niezarządzanego. [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)]

## <a name="see-also"></a>Zobacz też
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
