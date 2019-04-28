---
title: IDebugApplication110::CallableWaitForHandles | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: f74e3faa57e9ee4a38f77110334383bc2c72fe2f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446397"
---
# <a name="idebugapplication110callablewaitforhandles"></a>IDebugApplication110::CallableWaitForHandles
W tym czasie czeka dla każdego określonego dojścia ma być zasygnalizowany pozwalając wywołania międzywątkowe wysyłany do tego wątku. Ta metoda musi zostać wywołana z wątku debugera.  
  
> [!IMPORTANT]
> [Interfejs IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md) jest implementowany przez program PDM w wersji 11.0 i nowszych. Znajduje się w zestawie activdbg100.h.  
  
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