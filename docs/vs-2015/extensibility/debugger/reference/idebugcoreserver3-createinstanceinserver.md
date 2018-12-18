---
title: IDebugCoreServer3::CreateInstanceInServer | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: efdd8078439e288e600ef3a318e4038af51c7d1b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51749709"
---
# <a name="idebugcoreserver3createinstanceinserver"></a>IDebugCoreServer3::CreateInstanceInServer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Tworzy wystąpienie aparatu debugowania na serwerze.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT CreateInstanceInServer(  
   LPCWSTR  szDll,  
   WORD     wLangId,  
   REFCLSID clsidObject,  
   REFIID   riid,  
   void**   ppvObject  
);  
```  
  
```csharp  
int CreateInstanceInServer(  
   string     szDll,   
   ushort     wLangID,   
   ref Guid   clsidObject,   
   ref Guid   riid,   
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `szDll`  
 [in] Ścieżka do biblioteki dll, która implementuje CLSID określone w `clsidObject` parametru. Jeśli jest to `NULL`, następnie modelu COM `CoCreateInstance` funkcja jest wywoływana.  
  
 `wLangId`  
 [in] Ustawienia regionalne aparatu debugowania. Może to być 0, jeśli [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) nie powinna być wywoływana metoda.  
  
 `clsidObject`  
 [in] Identyfikator CLSID aparat debugowania do utworzenia.  
  
 `riid`  
 [in] Identyfikator interfejsu określonego interfejsu, aby pobrać z obiektu klasy.  
  
 `ppvObject`  
 [out] `IUnknown` interfejsu z wystąpieniami obiektu. Rzutowanie lub kierować się ten obiekt do żądanego interfejsu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)

