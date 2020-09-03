---
title: 'IDebugProgramProvider2:: GetProviderProgramNode | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
helpviewer_keywords:
- IDebugProgramProvider2::GetProviderProgramNode
ms.assetid: e62e8e83-acbb-4c52-aedf-ffbd4670db29
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5fa9f4db6aa71e9bba1f456b13ba52abd24ab966
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68198713"
---
# <a name="idebugprogramprovider2getproviderprogramnode"></a>IDebugProgramProvider2::GetProviderProgramNode
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera węzeł programu dla określonego programu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetProviderProgramNode(  
   PROVIDER_FLAGS       Flags,  
   IDebugDefaultPort2*  pPort,  
   AD_PROCESS_ID        processId,  
   REFGUID              guidEngine,  
   UINT64               programId,  
   IDebugProgramNode2** ppProgramNode  
);  
```  
  
```csharp  
int GetProviderProgramNode(  
   enum_PROVIDER_FLAGS    Flags,  
   IDebugDefaultPort2     pPort,  
   AD_PROCESS_ID          ProcessId,  
   ref Guid               guidEngine,  
   ulong                  programId,  
   out IDebugProgramNode2 ppProgramNode  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `Flags`  
 podczas Kombinacja flag z wyliczenia [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md) . Następujące flagi są typowe dla tego wywołania:  
  
|Flaga|Opis|  
|----------|-----------------|  
|`PFLAG_REMOTE_PORT`|Obiekt wywołujący jest uruchomiony na komputerze zdalnym.|  
|`PFLAG_DEBUGGEE`|Obiekt wywołujący jest obecnie debugowany (dodatkowe informacje o kierowaniu zostaną zwrócone dla każdego węzła).|  
|`PFLAG_ATTACHED_TO_DEBUGGEE`|Obiekt wywołujący został dołączony do, ale nie został uruchomiony przez debuger.|  
  
 `pPort`  
 podczas Port, na którym jest uruchomiony proces wywołujący.  
  
 `processId`  
 podczas Struktura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) przechowująca identyfikator procesu zawierającego dany program.  
  
 `guidEngine`  
 podczas Identyfikator GUID aparatu debugowania, do którego jest dołączony program (jeśli istnieje).  
  
 `programId`  
 podczas Identyfikator programu, dla którego ma zostać pobrany węzeł programu.  
  
 `ppProgramNode`  
 określoną Obiekt [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) reprezentujący żądany węzeł programu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)   
 [PROVIDER_FLAGS](../../../extensibility/debugger/reference/provider-flags.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)   
 [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
