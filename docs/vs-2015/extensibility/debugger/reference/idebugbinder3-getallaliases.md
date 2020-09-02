---
title: 'IDebugBinder3:: GetAllAliases | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dc2075ccc37d280640f7559b1454990ee6684f25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555751"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ta metoda pobiera listę aliasów z programu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetAllAliases(  
   UINT          uRequest,  
   IDebugAlias** ppAliases,  
   UINT*         puFetched  
);  
```  
  
```csharp  
int GetAllAliases(  
   uint          uRequest,   
   IDebugAlias[] ppAliases,   
   out uint      puFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `uRequest`  
 podczas Maksymalna liczba aliasów do zwrócenia (określa długość tablicy, do której została przeniesiona `ppAliases` ).  
  
 `ppAliases`  
 [in. out] Tablica do wypełnienia przy użyciu aliasów (jeśli jest to wartość zerowa i `uRequest` wynosi 0, liczba aliasów, które mogą zostać zwrócone, będzie zwracana przez `puFetched` ).  
  
 `puFetched`  
 określoną Zwraca liczbę uzyskanych aliasów.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
