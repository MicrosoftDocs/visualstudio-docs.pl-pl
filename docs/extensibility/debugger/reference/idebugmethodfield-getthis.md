---
title: IDebugMethodField::GetThis | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b29252d1586d039084ec1d21f1fc4967aea68baf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727166"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Pobiera `this` (in)`Me` [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]wskaźnik obiektu zawierającego metodę.

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
[na zewnątrz] Zwraca obiekt [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) reprezentujący wskaźnik "this".

## <a name="return-value"></a>Wartość zwracana
 Jeśli się powiedzie, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 W językach obiektowych jest zazwyczaj dorozumiany wskaźnik do bieżącego wystąpienia klasy. Jest to `this` znane jako w języku C#/C++ i jak `Me` w [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)].

## <a name="see-also"></a>Zobacz też
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
