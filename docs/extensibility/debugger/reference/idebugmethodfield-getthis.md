---
title: 'IDebugMethodField:: GetThis | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727166"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Pobiera `this` wskaźnik ( `Me` in [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] ) obiektu zawierającego metodę.

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
określoną Zwraca obiekt [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) reprezentujący wskaźnik "This".

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 W językach zorientowanych obiektowo jest zazwyczaj implikowany wskaźnik do bieżącego tworzenia wystąpienia klasy. Jest to tzw `this` . w języku C#/c + + i jako `Me` w [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] .

## <a name="see-also"></a>Zobacz też
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
