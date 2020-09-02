---
title: 'IEnumDebugCodeContexts2:: GetCount | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2::GetCount
helpviewer_keywords:
- IEnumDebugCodeContexts2::GetCount
ms.assetid: 74c52fcf-688c-40df-9acd-29b3b84e6216
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e32a0d47fc1f07c3858b056d4483c762853bb428
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62551760"
---
# <a name="ienumdebugcodecontexts2getcount"></a>IEnumDebugCodeContexts2::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Zwraca liczbę elementów w wyliczeniu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcelt`  
 określoną Zwraca liczbę elementów w wyliczeniu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda nie jest częścią niestandardowego interfejsu wyliczenia modelu COM, który określa, że należy `Next` `Clone` zaimplementować tylko metody,, `Skip` i `Reset` .  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)
