---
title: 'IDebugCoreServer3:: CreateInstanceInServer | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::CreateInstanceInServer
helpviewer_keywords:
- IDebugCoreServer3::CreateInstanceInServer
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1d8964a79aaeb7b90dfbc809ec547d0282d79fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205265"
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
 podczas Ścieżka do biblioteki DLL implementującej identyfikator CLSID określony w `clsidObject` parametrze. Jeśli tak jest `NULL` , `CoCreateInstance` Funkcja com jest wywoływana.  
  
 `wLangId`  
 podczas Ustawienia regionalne aparatu debugowania. Może to być wartość 0, jeśli metoda [setlocal](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) nie powinna być wywoływana.  
  
 `clsidObject`  
 podczas Identyfikator CLSID aparatu debugowania do utworzenia.  
  
 `riid`  
 podczas Identyfikator interfejsu określonego interfejsu, który ma zostać pobrany z obiektu klasy.  
  
 `ppvObject`  
 [out] `IUnknown` Interfejs z obiektu skonkretyzowany. Rzutowanie lub kierowanie tego obiektu do żądanego interfejsu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)
