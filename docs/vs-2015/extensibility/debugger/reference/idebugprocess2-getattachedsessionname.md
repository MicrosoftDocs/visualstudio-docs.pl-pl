---
title: 'IDebugProcess2:: GetAttachedSessionName | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetAttachedSessionName
helpviewer_keywords:
- IDebugProcess2::GetAttachedSessionName
ms.assetid: 7e5e116f-2c0c-4bc8-ad3f-e9fd2318a7e4
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3acc40e2b906bd46b832d9fa11578de346014042
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64787770"
---
# <a name="idebugprocess2getattachedsessionname"></a>IDebugProcess2::GetAttachedSessionName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera nazwę sesji debugowania tego procesu. IDE może wyświetlić te informacje dla użytkownika, który debuguje określony proces na konkretnym komputerze.  
  
> [!NOTE]
> Ta metoda jest przestarzała i jej implementacja powinna zawsze zwrócić `E_NOTIMPL` .  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetAttachedSessionName(  
   BSTR* pbstrSessionName  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbstrSessionName`  
  
## <a name="return-value"></a>Wartość zwracana  
 Ta metoda powinna zawsze zwracać `E_NOTIMPL` .  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
