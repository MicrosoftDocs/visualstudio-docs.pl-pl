---
title: IDebugPortSupplier2::CanAddPort | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e4ec078650446d3511ed9c5bdc8ee3ec0191487d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54784941"
---
# <a name="idebugportsupplier2canaddport"></a>IDebugPortSupplier2::CanAddPort
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Sprawdza, czy dostawca portu można dodawać nowych portów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT CanAddPort(   
   void   
);  
```  
  
```csharp  
int CanAddPort();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Można dodać portu, funkcja zwraca `S_OK`; w przeciwnym razie zwraca `S_FALSE` do wskazania żadnych portów mogą być dodawane do tego dostawcy portu.  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie tej metody, przed wywołaniem [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) metody, ponieważ druga metoda tworzy portu, a także dodawanie, co może być czasochłonna operacja.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
