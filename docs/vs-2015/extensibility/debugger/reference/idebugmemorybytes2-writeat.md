---
title: 'IDebugMemoryBytes2:: WriteAt | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMemoryBytes2::WriteAt
helpviewer_keywords:
- IDebugMemoryBytes2::WriteAt method
- WriteAt method
ms.assetid: 61cc3704-47fa-4d9b-aa62-bb4585ac8fb1
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2479ac3948f81769ba2e73c746fd1811652aa239
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180569"
---
# <a name="idebugmemorybytes2writeat"></a>IDebugMemoryBytes2::WriteAt
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Zapisuje określoną liczbę bajtów pamięci, rozpoczynając od podanego adresu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT WriteAt(   
   IDebugMemoryContext2* pStartContext,  
   DWORD                 dwCount,  
   BYTE*                 rgbMemory  
);  
```  
  
```csharp  
int WriteAt(  
   IDebugMemoryContext2 pStartContext,  
   uint                 dwCount,  
   byte[]               rgbMemory  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStartContext`  
 podczas Obiekt [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md) , który określa, gdzie zaczynać pisać bajty.  
  
 `dwCount`  
 podczas Liczba bajtów do zapisania.  
  
 `rgbMemory`  
 podczas Bajty do zapisania. Przyjęto, że ta tablica ma rozmiar co najmniej `dwCount` bajtów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca `S_OK` ; w przeciwnym razie zwraca wartość, `S_FALSE` Jeśli nie wszystkie bajty mogą być zapisywane lub zwracają kod błędu (zazwyczaj `E_FAIL` ).  
  
## <a name="remarks"></a>Uwagi  
 Jeśli adres początkowy nie należy do okna pamięci reprezentowanego przez ten obiekt [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md) , nie nastąpi zapis i zwrócony kod błędu `E_FAIL` — nawet wtedy, gdy wielkość zapisu nakłada się na przestrzeń pamięci.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)   
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)
