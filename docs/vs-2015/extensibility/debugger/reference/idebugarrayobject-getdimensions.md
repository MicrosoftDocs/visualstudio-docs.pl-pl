---
title: IDebugArrayObject::GetDimensions | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugArrayObject::GetDimensions
helpviewer_keywords:
- IDebugArrayObject::GetDimensions method
ms.assetid: 113e0aff-9028-49d6-b104-9fe7be4772d7
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 09902c60f87cfb92d0f0778fcbd106ade4d8dac4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54777389"
---
# <a name="idebugarrayobjectgetdimensions"></a>IDebugArrayObject::GetDimensions
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera wymiary tablicy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetDimensions(   
   DWORD dwCount,  
   DWORD dwDimensions[]  
);  
```  
  
```csharp  
int GetDimensions(  
   [In] uint    dwCount,   
   [Out] uint[] dwDimensions  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwCount`  
 [in] Liczba wymiarów do pobrania.  
  
 `dwDimensions`  
 [out w] Tablica, która jest wypełniane rozmiarów każdego wymiaru. `dwCount` Określa maksymalny rozmiar `dwDimensions` tablicy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca wartość S_OK; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Wielowymiarowe tablice może mieć różne rozmiary dla każdego wymiaru. Na przykład, biorąc pod uwagę tablicy trójwymiarowej `myarray[3][2][6]`, ta metoda zwróci 3, 2 i 6 w `dwDimensions` parametru w tej kolejności.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)
