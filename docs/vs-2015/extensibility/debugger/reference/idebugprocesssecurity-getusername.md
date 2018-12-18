---
title: IDebugProcessSecurity::GetUserName | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
caps.latest.revision: 5
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 45e9bb46a26191c7722657033ece7d1e83867711
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755928"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera nazwę użytkownika z dostawcy portu.  
  
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
 [out] Ciąg zawierający nazwę użytkownika.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli metoda się powiedzie, zwraca `S_OK`. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 `GetUserName` Zwraca nazwę użytkownika, która jest wyświetlana w **nazwa_użytkownika** kolumny **dołączyć do procesu** okno dialogowe. Aby wyświetlić **dołączyć do procesu** okno dialogowe, kliknij przycisk **dołączyć do procesu** na **narzędzia** menu w [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE).  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)

