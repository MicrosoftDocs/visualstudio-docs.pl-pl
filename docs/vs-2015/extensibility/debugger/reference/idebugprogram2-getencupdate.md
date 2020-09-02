---
title: 'IDebugProgram2:: GetENCUpdate | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetENCUpdate
helpviewer_keywords:
- IDebugProgram2::GetENCUpdate
ms.assetid: 9832aac8-6320-4fd8-91dd-2a0852febb00
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ac976232f2e92a7af1c8e0fabb7907e7164ba08a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64833321"
---
# <a name="idebugprogram2getencupdate"></a>IDebugProgram2::GetENCUpdate
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta metoda pobiera aktualizację Edytuj i Kontynuuj (ENC) dla tego programu. Niestandardowy aparat debugowania zawsze zwraca wartość `E_NOTIMPL` .  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetENCUpdate(   
   IUnknown** ppUpdate  
);  
```  
  
```csharp  
int GetENCUpdate(  
   out object ppUpdate  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppUpdate`  
 określoną Zwraca wewnętrzny interfejs, którego można użyć do zaktualizowania tego programu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
> [!NOTE]
> Niestandardowy aparat debugowania powinien zawsze zwrócić `E_NOTIMPL` .  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
