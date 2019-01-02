---
title: IDebugPortSupplier3::CanPersistPorts | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5d9038663bd74b5dabeda92d8b6b9e4e31d092de
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53939969"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Ta metoda określa, czy dostawca portu można utrwalić portów (zapisując je na dysku) między wywołań debugera.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```csharp  
int CanPersistPorts();  
```  
  
#### <a name="parameters"></a>Parametry  
 Brak.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK` Jeśli porty mogą zostać utrwalone, lub `S_FALSE` do wskazania, czy porty nie może zostać utrwalona.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli dostawcy portu można utrwalić portów, należy to zrobić, kiedy niszczony jest i ponownie załadować, gdy zostanie uruchomiony ponownie.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)