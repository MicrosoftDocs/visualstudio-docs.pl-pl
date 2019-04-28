---
title: IDebugSourceServerModule::GetSourceServerData | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule::GetSourceServerData
ms.assetid: f15d86aa-1bd9-4b16-a64a-21b01c27db2e
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fc99d014c1e31616ebd2a6cc16608a1d1bc741ce
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62916116"
---
# <a name="idebugsourceservermodulegetsourceserverdata"></a>IDebugSourceServerModule::GetSourceServerData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera tablicę informacji o serwerze źródłowym.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetSourceServerData(  
   ULONG* pDataByteCount,   
   BYTE** ppData  
);  
```  
  
```csharp  
public int GetSourceServerData(  
   out uint  pDataByteCount,   
   out int[] ppData  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pDataByteCount`  
 [out] Liczba bajtów w tablicy danych.  
  
 `ppData`  
 [out] Odwołanie do tablicy danych.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak zaimplementować tę metodę, aby uzyskać **CModule** obiekt ujawniający [IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md) interfejsu.  
  
```cpp#  
HRESULT CModule::GetSourceServerData(ULONG* pDataByteCount, BYTE** ppData)  
{  
    HRESULT hr = S_OK;  
    CComPtr<ISymUnmanagedReader> pSymReader;  
    CComPtr<ISymUnmanagedSourceServerModule> pSourceServerModule;  
  
    IfFalseGo( pDataByteCount && ppData, E_INVALIDARG );  
    *pDataByteCount = 0;  
    *ppData = NULL;  
  
    IfFailGo( this->GetUnmanagedSymReader( &pSymReader ) );  
    IfFailGo( pSymReader->QueryInterface( &pSourceServerModule ) );  
  
    IfFailGo( pSourceServerModule->GetSourceServerData( pDataByteCount, ppData ) );  
  
Error:  
  
    return hr;  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)
