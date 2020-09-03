---
title: 'IDebugPortSupplier2:: CanAddPort | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5d0c67d62f57076f29f2c2ef60d456f517ae97fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80724747"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
Sprawdza, czy dostawca portu może dodawać nowe porty.

## <a name="syntax"></a>Składnia

```cpp
HRESULT CanAddPort( 
   void 
);
```

```csharp
int CanAddPort();
```

## <a name="return-value"></a>Wartość zwracana
 Jeśli port może być dodany, zwraca `S_OK` ; w przeciwnym razie zwraca wartość wskazującą, że `S_FALSE` nie można dodać portów do tego dostawcy portów.

## <a name="remarks"></a>Uwagi
 Wywołaj tę metodę przed wywołaniem metody [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) , ponieważ druga metoda tworzy port i dodaje go, co może być czasochłonną operacją.

## <a name="see-also"></a>Zobacz też
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
- [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
