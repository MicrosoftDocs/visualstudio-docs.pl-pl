---
title: 'IDebugApplication110:: CallableWaitForHandles | Microsoft Docs'
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
ms.openlocfilehash: 22af0e9dcf548bbd2f0f8c179b4889d5294eb284
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575084"
---
# <a name="idebugapplication110callablewaitforhandles"></a>IDebugApplication110::CallableWaitForHandles
Czeka na zasygnalizowanie któregokolwiek z określonych dojść, przy jednoczesnym umożliwieniu ogłaszania wywołań między wątkami w tym wątku. Ta metoda musi zostać wywołana z wątku debugera.  
  
> [!IMPORTANT]
> [Interfejs IDebugApplication110](../../winscript/reference/idebugapplication110-interface.md) jest implementowany przez PDM v 11.0 i nowsze. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CallableWaitForHandles([in] DWORD handleCount, [in, size_is(handleCount)] const HANDLE* pHandles, [out] DWORD* pIndex);  
```  
  
#### <a name="parameters"></a>Parametry  
 `handleCount`  
 Liczba dojść do oczekiwania.  
  
 `pHandles`  
 Zestaw dojść do oczekiwania.  
  
 `pIndex`  
 Gdy wartość HRESULT to S_OK, indeks do `pHandles` dla uchwytu, który został zasygnalizowani.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugApplication110, interfejs](../../winscript/reference/idebugapplication110-interface.md)