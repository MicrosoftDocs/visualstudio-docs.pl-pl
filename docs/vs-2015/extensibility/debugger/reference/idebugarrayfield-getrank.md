---
title: IDebugArrayField::GetRank | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5d0396718482c9ce90527155a3612160612f66d3
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790783"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera ranga lub liczba wymiarów tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```csharp  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwRank`  
 [out] Zwraca rangę.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Ranga tablicy odpowiada liczbę wymiarów. W języku C++ i C# są naprawdę tablice tablic wielowymiarowych tablic, a w związku z tym można uznać za Jednowymiarowa tablica (i `GetRank` metoda zawsze zwraca 1). W [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], z drugiej strony, wielowymiarowe tablice są obsługiwane inaczej i rangę tablicy takich odzwierciedla liczbę wymiarów (i `GetRank` metoda zawsze zwraca liczbę wymiarów).  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
