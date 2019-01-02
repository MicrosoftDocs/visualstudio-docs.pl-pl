---
title: IDebugProcessSecurity::GetUserName | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: fd3f7133652cf048bb1b4c7a2e7d4886b1c79a2b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53931093"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Pobiera nazwę użytkownika z dostawcy portu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetUserName(  
    BSTR *pbstrUserName  
);  
```  
  
```csharp  
int GetUserName (  
    string pbstrUserName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrUserName`  
 [out] Ciąg zawierający nazwę użytkownika.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda się powiedzie, zwraca `S_OK`. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 `GetUserName` Zwraca nazwę użytkownika, która jest wyświetlana w **nazwa_użytkownika** kolumny **dołączyć do procesu** okno dialogowe. Aby wyświetlić **dołączyć do procesu** okno dialogowe, kliknij przycisk **dołączyć do procesu** na **narzędzia** menu w [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] zintegrowanego środowiska programistycznego (IDE).  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)