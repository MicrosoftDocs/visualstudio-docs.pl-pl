---
title: IDebugArrayField::GetRank | Dokumentacja firmy Microsoft
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
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2ff33ddc6ba41eb43f63ecfb92ad440f205f253a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51797738"
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

