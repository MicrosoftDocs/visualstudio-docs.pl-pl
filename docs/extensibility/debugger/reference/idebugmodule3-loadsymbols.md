---
description: Ładuje symbole dla bieżącego modułu.
title: 'IDebugModule3:: LoadSymbols | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::LoadSymbols
helpviewer_keywords:
- IDebugModule3::LoadSymbols
ms.assetid: 7548c8c1-cbc6-48aa-a845-19058d4a85bb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2e8a9c34c85263ab538bf07b10b87f12fddf12db
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105065518"
---
# <a name="idebugmodule3loadsymbols"></a>IDebugModule3::LoadSymbols
Ładuje symbole dla bieżącego modułu.

## <a name="syntax"></a>Składnia

```cpp
HRESULT LoadSymbols(
   void
);
```

```csharp
int LoadSymbols();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli metoda się powiedzie, zwraca wartość `S_OK` . Jeśli to się nie powiedzie, zwraca kod błędu.

## <a name="remarks"></a>Uwagi
 Ta metoda ładuje symbole z bieżącej ścieżki wyszukiwania (którą można zmienić, wywołując metodę [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md) ).

 Ta metoda jest preferowana przez metodę [ReloadSymbols_Deprecated](../../../extensibility/debugger/reference/idebugmodule2-reloadsymbols-deprecated.md) .

## <a name="see-also"></a>Zobacz też
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
