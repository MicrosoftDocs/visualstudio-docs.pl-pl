---
title: IDebugPortSupplier2::CanAddPort | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugPortSupplier2::CanAddPort
helpviewer_keywords:
- IDebugPortSupplier2::CanAddPort
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e29478d71b60376bbd396650935e6257d11a7d37
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769726"
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

