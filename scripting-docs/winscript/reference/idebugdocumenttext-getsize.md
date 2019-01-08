---
title: IDebugDocumentText::GetSize | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetSize
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetSize
ms.assetid: 9da53856-613a-44b2-a84c-99454a2a1548
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c171b894856141d8c42ae641f1d08b058cd3d9c3
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087038"
---
# <a name="idebugdocumenttextgetsize"></a>IDebugDocumentText::GetSize
Zwraca liczbę wierszy i liczbę znaków w dokumencie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetSize(  
   ULONG*  pcNumLines,  
   ULONG*  pcNumChars  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pcNumLines`  
 [out] Liczba wierszy w dokumencie. Jeśli ten parametr ma wartość NULL, metoda nie zwraca wartości.  
  
 `pcNumChars`  
 [out] Liczba znaków w dokumencie. Jeśli ten parametr ma wartość NULL, metoda nie zwraca wartości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca liczbę wierszy i liczbę znaków w dokumencie.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentText, interfejs](../../winscript/reference/idebugdocumenttext-interface.md)