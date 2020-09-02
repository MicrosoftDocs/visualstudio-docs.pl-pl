---
title: 'IDebugCustomAttributeQuery2:: GetCustomAttributeByName — | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e1af059cf4319c18b8f8bb63e7b50ec3d2822e93
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62568437"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Uzyskuje bajty atrybutów niestandardowych, używając nazwy atrybutu niestandardowego.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetCustomAttributeByName(   
   LPCOLESTR pszCustomAttributeName,  
   BYTE*     ppBlob,  
   DWORD*    pdwLen  
);  
```  
  
```csharp  
int GetCustomAttributeByName(  
   [In] string        pszCustomAttributeName,   
   [In, Out] byte[]   ppBlob,   
   [In, Out] ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pszCustomAttributeName`  
 podczas Ciąg zawierający nazwę atrybutu niestandardowego do wyszukania.  
  
 `ppBlob`  
 [in. out] Tablica, która jest uzupełniona o bajty atrybutów niestandardowych.  
  
 `pdwLen`  
 [in. out] Określa maksymalną liczbę bajtów zwracanych w `ppBlob` tablicy i zwraca liczbę bajtów rzeczywiście zapisaną do tablicy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca S_OK lub zwraca S_FALSE, jeśli atrybut niestandardowy nie istnieje. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ustaw `ppBlob` parametr na wartość null, aby zwrócić liczbę dostępnych bajtów atrybutów. Następnie przydziel tablicę i przekaż tę tablicę do `ppBlob` parametru.  
  
 Atrybut bajty reprezentuje pierwotne dane atrybutu niestandardowego.  
  
 Jeśli `ppBlob` Parametry i `pdwLen` są ustawione na wartość null, ta metoda może służyć do określenia, czy atrybut niestandardowy już istnieje. Jednak łatwiejszym rozwiązaniem jest wywołanie metody [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) .  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)
