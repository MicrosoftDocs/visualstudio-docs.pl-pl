---
title: 'IDebugDocumentPosition2:: GetRange | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2::GetRange
helpviewer_keywords:
- IDebugDocumentPosition2::GetRange
ms.assetid: 91a06ee7-253a-4215-be22-04bf57305aa8
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 189810280bd5db4573ba45c2335b8bb96a163abb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200262"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera zakres dla tego położenia dokumentu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT GetRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```csharp  
int GetRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pBegPosition`  
 [in. out] Struktura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , która jest wypełniana początkową pozycją. Jeśli te informacje nie są konieczne, należy ustawić wartość null dla tego argumentu.  
  
 `pEndPosition`  
 [in. out] Struktura [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) , która jest wypełniana pozycją końcową. Jeśli te informacje nie są konieczne, należy ustawić wartość null dla tego argumentu.  
  
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
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
