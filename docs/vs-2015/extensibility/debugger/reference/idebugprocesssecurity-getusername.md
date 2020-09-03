---
title: 'IDebugProcessSecurity:: GetUserName | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 17a6ef52d7df1c60b0cb6581a7e15eeaf67e7875
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202789"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera nazwę użytkownika z dostawcy portów.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
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
 określoną Ciąg zawierający nazwę użytkownika.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda się powiedzie, zwraca wartość `S_OK` . W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 `GetUserName` Zwraca nazwę użytkownika, która jest wyświetlana w kolumnie **Nazwa użytkownika** w oknie dialogowym **Dołącz do procesu** . Aby wyświetlić okno dialogowe **dołączanie do procesu** , kliknij przycisk **Dołącz do procesu** w menu **Narzędzia** w [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] zintegrowanym środowisku programistycznym (IDE).  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
