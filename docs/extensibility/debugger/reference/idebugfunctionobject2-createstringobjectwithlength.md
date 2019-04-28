---
title: IDebugFunctionObject2::CreateStringObjectWithLength | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- CreateStringObjectWithLength
- IDebugFunctionObject2::CreateStringObjectWithLength
ms.assetid: 1f43ec66-1615-4a4c-8b9d-e933f549f96d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 02ee13b62a2238624f1c6d42c52bf67db2ceaae4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62873788"
---
# <a name="idebugfunctionobject2createstringobjectwithlength"></a>IDebugFunctionObject2::CreateStringObjectWithLength
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tworzy obiekt ciągu, który ma określony czas.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT CreateStringObjectWithLength (  
   LPCOLESTR      pcstrString,  
   UINT           uiLength,  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int CreateStringObjectWithLength (  
   string           pcstrString,  
   uint             uiLength,  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcstrString`  
 [in] Wartość ciągu z obiektem ciągu.  
  
 `uiLength`  
 [in] Długość ciągu w bajtach.  
  
 `ppObject`  
 [out] Zwraca [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) obiekt, który reprezentuje obiekt ciągu nowo utworzony.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
