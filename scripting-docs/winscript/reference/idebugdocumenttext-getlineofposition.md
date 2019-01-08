---
title: IDebugDocumentText::GetLineOfPosition | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 9c916f0a76021afea82b4021ed1ce7d411317807
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087714"
---
# <a name="idebugdocumenttextgetlineofposition"></a>IDebugDocumentText::GetLineOfPosition
Zwraca numer wiersza i, opcjonalnie, Przesunięcie znaku w wierszu, który odnosi się do danej pozycji znaku.  
  
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
 [in] Lokalizacja z zakresu znaków pozycja początkowa.  
  
 `pcLineNumber`  
 [out] Numer wiersza zakresu.  
  
 `pcCharacterOffsetInLine`  
 [out w] Przesunięcie znaku zakresu, w wierszu `pcLineNumber`. Jeśli ten parametr jest `NULL`, metoda nie zwraca wartości.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda ta zwraca `HRESULT`. Przykładowe dopuszczalne wartości wymieniono w tabeli poniżej.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wykonanie metody powiodło się.|  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zwraca numer wiersza i, opcjonalnie, Przesunięcie znaku w wierszu, który odnosi się do danej pozycji znaku.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentText, interfejs](../../winscript/reference/idebugdocumenttext-interface.md)