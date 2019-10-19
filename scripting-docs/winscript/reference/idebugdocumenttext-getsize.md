---
title: 'IDebugDocumentText:: GetSize | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: ef6f75b396dddec80fb2ae89c71f8579ce3c29b9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572095"
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
 określoną Liczba wierszy w dokumencie. Jeśli ten parametr ma wartość NULL, metoda nie zwraca wartości.  
  
 `pcNumChars`  
 określoną Liczba znaków w dokumencie. Jeśli ten parametr ma wartość NULL, metoda nie zwraca wartości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca liczbę wierszy i liczbę znaków w dokumencie.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugDocumentText, interfejs](../../winscript/reference/idebugdocumenttext-interface.md)