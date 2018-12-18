---
title: IDebugProviderProgramNode2::UnmarshalDebuggeeInterface | Dokumentacja firmy Microsoft
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
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
helpviewer_keywords:
- IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 94b40ba62e079fbc70fa4f9c7f9560e79bcc0a29
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51771978"
---
# <a name="idebugproviderprogramnode2unmarshaldebuggeeinterface"></a>IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera określonego interfejsu, granice procesu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT UnmarshalDebuggeeInterface(  
   REFIID riid,  
   void** ppvObject  
);  
```  
  
```csharp  
int UnmarshalDebuggeeInterface(  
   ref Guid   riid,  
   out IntPtr ppvObject  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 [in] Identyfikator GUID interfejsu do uzyskania.  
  
 `ppvObject`  
 [out] Zwraca obiekt implementujący żądanego interfejsu. [C++] to może być rzutowany bezpośrednio typ żądanego interfejsu. [C#] Użyj <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> metodę umożliwiającą uzyskanie żądanego interfejsu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest używana, gdy aparat debugowania jest uruchomiony w [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] przestrzeni procesu, a program poddawany działa w jego własnej przestrzeni procesu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)

