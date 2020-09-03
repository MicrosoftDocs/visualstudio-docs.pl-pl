---
title: 'IDebugCustomAttribute:: GetName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 15d435d043d0e3863358628fa12016431a417918
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732775"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Pobiera nazwę atrybutu niestandardowego.

## <a name="syntax"></a>Składnia

```cpp
HRESULT GetName( 
   BSTR* bstrName
);
```

```csharp
int GetName(
   out string bstrName
);
```

## <a name="parameters"></a>Parametry
`bstrName`\
określoną Zwraca ciąg zawierający nazwę atrybutu niestandardowego.

## <a name="return-value"></a>Wartość zwracana
 Jeśli powiedzie się, zwraca S_OK; w przeciwnym razie zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Nazwa zwrócona przez tę metodę odpowiada nazwie klasy użytej do zadeklarowania atrybutu. Może to nie odpowiadać dokładnie nazwie klasy atrybutu niestandardowego, ponieważ C# umożliwia porzucenie sufiksu "Attribute" z nazwy atrybutu niestandardowego, gdy jest on używany w deklaracji.

## <a name="see-also"></a>Zobacz też
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
