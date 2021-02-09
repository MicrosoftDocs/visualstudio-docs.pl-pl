---
title: 'IDebugClassField:: EnumInterfacesImplemented | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumInterfacesImplemented
helpviewer_keywords:
- IDebugClassField::EnumInterfacesImplemented method
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b7283d8a2996d5ab4dfc52cde446170e7632c27c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99876085"
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
