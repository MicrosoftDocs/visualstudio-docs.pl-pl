---
title: IDebugProcess3::DisableENC | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess3::DisableENC
helpviewer_keywords:
- IDebugProcess3::DisableENC
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c8d440783dbd6112e6f9918cd22388b4b8efbff0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53921194"
---
# <a name="idebugprocess3disableenc"></a>IDebugProcess3::DisableENC
Ta metoda jawnie wyłącza Edytuj i Kontynuuj na temat tego procesu (i wszystkie programy zawiera). Dostawcy niestandardowego portu powinna zawsze zwracać `E_NOTIMPL`.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DisableENC(  
   EncUnavailableReason reason  
);  
```  
  
```csharp  
   EncUnavailableReason reason  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `reason`  
 [in] Wartość z zakresu od [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) wyliczenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
> [!NOTE]
>  Dostawcy niestandardowego portu powinna zawsze zwracać `E_NOTIMPL`.  
  
## <a name="remarks"></a>Uwagi  
 Raz Edytuj i Kontynuuj jest wyłączona dla procesu, można ją ponownie włączyć tylko przez ponowne uruchomienie procesu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)