---
title: 'IEnumDebugPortSuppliers2:: Reset | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPortSuppliers2::Next
helpviewer_keywords:
- IEnumDebugPortSuppliers2::Next
ms.assetid: f69cbacf-da9d-4b22-b8a2-abd9b8c131f2
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f34b73bbdd36dbf7d98885b48b0cd8fdf8dc4d7c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164685"
---
# <a name="ienumdebugportsuppliers2reset"></a>IEnumDebugPortSuppliers2::Reset
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Resetuje Wyliczenie do pierwszego elementu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Reset(  
   void  
);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Po wywołaniu tej metody następne wywołanie do [następnej](../../../extensibility/debugger/reference/ienumdebugportsuppliers2-next.md) metody zwraca pierwszy element wyliczenia.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)
