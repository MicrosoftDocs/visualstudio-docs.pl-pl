---
title: IDebugProgramEx2::Attach | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5b4cbdefbefb2668191d37aa25ecc1f6dbb5232d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54785011"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Sesję należy dołączyć do programu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason,  
   IDebugSession2*       pSession  
);  
```  
  
```  
[C#]  
int Attach(   
   IDebugEventCallback2 pCallback,  
   uint                 dwReason,  
   IDebugSession2       pSession  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pCallback`  
 [in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) obiekt, który reprezentuje aparat debugowania dołączonych wysyła zdarzenia do funkcja wywołania zwrotnego.  
  
 `dwReason`  
 [in] Wartość z zakresu od [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) wyliczenie opisujące przyczynę operacji dołączania.  
  
 `pSession`  
 [in] Wartość, która jednoznacznie identyfikuje sesji, która jest dołączenie do programu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu. Ta metoda powinna zwracać `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` Jeśli program jest już dołączony.  
  
## <a name="remarks"></a>Uwagi  
 Port, który zawiera program można użyć wartości w `pSession` ustalenie, który sesja próbuje dołączyć do programu. Na przykład jeśli port umożliwia sesję debugowania tylko jeden, aby dołączyć do procesu w czasie, numer portu można określić, jeśli ta sama sesja jest już dołączony do innych programów w procesie.  
  
> [!NOTE]
>  Przekazanego interfejsu `pSession` jest traktowane tylko jako plik cookie, a wartość, która jednoznacznie identyfikuje Menedżer debugowania sesji, dołączenie do tego programu; Brak metody w interfejsie podane są funkcjonalne.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
