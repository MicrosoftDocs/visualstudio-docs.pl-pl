---
title: IDebugMethodField::GetThis | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 426fc0c74b44b1f137752814f9b6aaeff150baa8
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66324069"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Pobiera `this` (`Me` w [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]) wskaźnik obiekt zawierający metodę.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetThis( 
   IDebugClassField** ppClass
);
```

```csharp
int GetThis(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>Parametry
`ppClass`\
[out] Zwraca [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) obiekt reprezentujący "to" wskaźnik.

## <a name="return-value"></a>Wartość zwracana
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 W językach obiektowych jest zazwyczaj dorozumianych wskaźnik do bieżącego wystąpienia klasy. Jest to nazywane `this` w języku C# / C++ i `Me` w [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)].

## <a name="see-also"></a>Zobacz także
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)