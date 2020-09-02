---
title: 'IDebugClassField:: EnumConstructors | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 607f4f4af3021389628fcc1be446ebbe95628b7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80734459"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
Tworzy moduł wyliczający dla konstruktorów tej klasy.

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

## <a name="parameters"></a>Parametry
`cMatch`\
podczas Wartość z wyliczenia [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) , która określa typ konstruktorów do wyliczenia.

`ppEnum`\
określoną Zwraca obiekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) reprezentujący listę konstruktorów. Zwraca wartość null, jeśli nie ma konstruktorów.

## <a name="return-value"></a>Wartość zwracana
 Jeśli to się powiedzie, zwraca S_OK lub zwraca S_FALSE, jeśli nie ma konstruktorów. W przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Każdy element wyliczenia jest obiektem [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) opisującym metodę konstruktora.

 Lista konstruktorów zazwyczaj nie obejmuje konstruktorów domyślnych dostarczanych przez kompilator.

## <a name="see-also"></a>Zobacz też
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)
