---
description: Pobiera wskaźnik this (Me in Visual Basic) obiektu zawierającego metodę.
title: 'IDebugMethodField:: GetThis | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 662555ec4552aa016b40c1e9c8222992e6cdfd66
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076657"
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
