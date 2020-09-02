---
title: 'IEnumDebugCustomAttributes:: Next | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Next
helpviewer_keywords:
- IEnumDebugCustomAttributes::Next
ms.assetid: e36f856b-2619-42d1-b73e-4f2390fc22bd
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f6ce0a8199bfb279c8f8d628de0b174d7f03369
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62551406"
---
# <a name="ienumdebugcustomattributesnext"></a>IEnumDebugCustomAttributes::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera określoną liczbę atrybutów niestandardowych w sekwencji wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Next (   
   ULONG      celt,  
   CODE_PATH* rgelt,  
   ULONG*     pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint                        celt,   
   out IDebugCustomAttribute[] rgelt,   
   ref uint                    pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 podczas Liczba elementów do pobrania. Określa również maksymalny rozmiar `rgelt` tablicy.  
  
 `rgelt`  
 określoną Tablica obiektów [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) do wypełnienia.  
  
 `pceltFetched`  
 określoną Zwraca liczbę elementów faktycznie zwracanych w elemencie `rgelt` .  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` . Zwraca wartość `S_FALSE` , jeśli nie można zwrócić wymaganej liczby elementów; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)   
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
