---
title: 'IDebugDocumentText:: GetLineOfPosition | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugDocumentText.GetLineOfPosition
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugDocumentText::GetLineOfPosition
ms.assetid: fe8d4802-ea16-49ca-8973-89dcaf6c915b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e8ce32e46c42ee864a88e169a79539efb8b05633
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572114"
---
# <a name="idebugdocumenttextgetlineofposition"></a>IDebugDocumentText::GetLineOfPosition
Zwraca numer wiersza i, opcjonalnie, Przesunięcie znaku w wierszu, który odnosi się do podanego położenia znaku.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetLineOfPosition(  
   ULONG   cCharacterPosition,  
   ULONG*  pcLineNumber,  
   ULONG*  pcCharacterOffsetInLine  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cCharacterPosition`  
 podczas Lokalizacja początkowa zakresu pozycji znaku.  
  
 `pcLineNumber`  
 określoną Numer wiersza zakresu.  
  
 `pcCharacterOffsetInLine`  
 [in. out] Przesunięcie znaku zakresu w wierszu `pcLineNumber`. Jeśli ten parametr jest `NULL`, metoda nie zwraca wartości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca numer wiersza i, opcjonalnie, Przesunięcie znaku w wierszu, który odnosi się do podanego położenia znaku.  
  
## <a name="see-also"></a>Zobacz także  
 [IDebugDocumentText, interfejs](../../winscript/reference/idebugdocumenttext-interface.md)