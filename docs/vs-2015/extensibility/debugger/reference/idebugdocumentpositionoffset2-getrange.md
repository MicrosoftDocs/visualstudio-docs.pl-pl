---
title: 'IDebugDocumentPositionOffset2:: GetRange | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2::GetRange
ms.assetid: 27da7130-0932-4f97-abde-05e6fb018606
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a028a2c88fe44aa6a117ddb81cff5788eec1732e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200230"
---
# <a name="idebugdocumentpositionoffset2getrange"></a>IDebugDocumentPositionOffset2::GetRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera zakres dla bieżącego położenia dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetRange(  
   DWORD* pdwBegOffset,  
   DWORD* pdwEndOffset  
);  
```  
  
```csharp  
public int GetRange(  
   ref uint pdwBegOffset,  
   ref uint pdwEndOffset  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pdwBegOffset`  
 [in. out] Przesunięcie dla pozycji początkowej zakresu. Jeśli te informacje nie są konieczne, należy ustawić wartość null dla tego parametru.  
  
 `pdwEndOffset`  
 [in. out] Przesunięcie dla pozycji końcowej zakresu. Jeśli te informacje nie są konieczne, należy ustawić wartość null dla tego parametru.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli powiedzie się, zwraca `S_OK` ; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Zakres określony w położeniu dokumentu dla punktu przerwania lokalizacji jest używany przez aparat debugowania (DE) do wyszukania instrukcji, która faktycznie współużytkuje kod. Rozważmy na przykład następujący kod:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 Wiersz nr 5 przyczynia się do debugowania kodu programu. Jeśli debuger ustawiający punkt przerwania w wierszu 5 chce, aby wyszukiwać do przodu określoną ilość dla pierwszego wiersza, który współużytkuje kod, debuger określi zakres, który zawiera dodatkowe wiersze kandydatów, w których punkt przerwania może być prawidłowo umieszczony. A następnie wyszukuje przechodzenie do przodu w tych wierszach do momentu znalezienia wiersza, który może akceptować punkt przerwania.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)   
 [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)
