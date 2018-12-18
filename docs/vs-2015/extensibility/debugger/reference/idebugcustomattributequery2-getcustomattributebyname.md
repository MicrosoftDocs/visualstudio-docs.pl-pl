---
title: IDebugCustomAttributeQuery2::GetCustomAttributeByName | Dokumentacja firmy Microsoft
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
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 80e67c26924a906cada5dec022b8a385f0f4afad
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796119"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera atrybuty niestandardowe bajtów, biorąc pod uwagę nazwę atrybutu niestandardowego.  
  
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
 [in] Ciąg zawierający nazwę atrybutu niestandardowego do wyszukania.  
  
 `ppBlob`  
 [out w] Tablica, która jest wypełniane bajtów atrybutu niestandardowego.  
  
 `pdwLen`  
 [out w] Określa maksymalną liczbę bajtów do zwrócenia w `ppBlob` tablicy i zwraca liczbę bajtów rzeczywiście zapisanych na tablicy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli to się powiedzie, zwraca wartość S_OK lub zwraca wartość S_FALSE, jeśli nie ma atrybutu niestandardowego. W przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ustaw `ppBlob` parametr ma wartość null, aby zwrócić liczbę atrybutów dostępnych bajtów. Następnie przydzielić tablicy i przekażesz ten tablica w `ppBlob` parametru.  
  
 Bajty atrybut reprezentują dane pierwotne atrybutu niestandardowego.  
  
 Jeśli `ppBlob` i `pdwLen` parametry są ustawione na wartość null, Metoda ta może służyć do ustalenia, czy atrybut niestandardowy jedynie istnieje. Alternatywą łatwiej jest jednak wywołać [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) metody.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)

