---
title: IEnumDebugCustomAttributes::Clone | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes::Clone
helpviewer_keywords:
- IEnumDebugCustomAttributes::Clone
ms.assetid: e6825000-e195-42b4-b296-bfe1e533d79b
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a0cabc640329ffd6cb070cdd7550b88119185692
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54781804"
---
# <a name="ienumdebugcustomattributesclone"></a>IEnumDebugCustomAttributes::Clone
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tworzy moduł wyliczający, który zawiera ten sam stan wyliczenia jako bieżącego modułu wyliczającego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT Clone (   
   IEnumCustomAttributes** ppEnum  
);  
```  
  
```csharp  
int Clone(  
   out IEnumDebugCustomAttributes ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 ppEnum  
 [out] Zwraca kopię tego wyliczenia jako oddzielny obiekt.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Kopię wyliczenia ma ten sam stan, co oryginalny w czasie, którego ta metoda jest wywoływana. Jednak stany kopiowania i oryginalne są niezależne i można zmieniać indywidualnie.  
  
## <a name="see-also"></a>Zobacz też  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
