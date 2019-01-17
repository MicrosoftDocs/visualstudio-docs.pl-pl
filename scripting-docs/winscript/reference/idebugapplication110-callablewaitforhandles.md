---
title: IDebugApplication110::CallableWaitForHandles | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110::CallableWaitForHandles
ms.assetid: 02e79b60-0d67-47f9-bf78-b65a02c9c014
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 31802d8b86f007139959f3ece3bd1a0260599181
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54350027"
---
# <a name="idebugapplication110callablewaitforhandles"></a>IDebugApplication110::CallableWaitForHandles
W tym czasie czeka dla każdego określonego dojścia ma być zasygnalizowany pozwalając wywołania międzywątkowe wysyłany do tego wątku. Ta metoda musi zostać wywołana z wątku debugera.  
  
> [!IMPORTANT]
>  [Interfejs IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md) jest implementowany przez program PDM w wersji 11.0 i nowszych. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
```  
  
#### <a name="parameters"></a>Parametry  
 `handleCount`  
 Liczba dojść oczekiwania.  
  
 `pHandles`  
 Zestaw dojścia oczekiwania.  
  
 `pIndex`  
 Po wartość HRESULT S_OK, Indeksuj do `pHandles` na uchwyt, który zostało zasygnalizowane.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugApplication110, interfejs](../../winscript/reference/idebugapplication110-interface.md)