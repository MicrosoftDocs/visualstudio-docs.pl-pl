---
title: IDebugDocumentPosition2::GetRange | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834969"
---
# <a name="idebugdocumentposition2getrange"></a>IDebugDocumentPosition2::GetRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Pobiera zakres dla tej pozycji dokumentu.  
  
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
 [out w] A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) strukturę, która jest wypełniane pozycja początkowa. Ustaw ten argument ma wartość null, jeśli te informacje nie są potrzebne.  
  
 `pEndPosition`  
 [out w] A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) strukturę, która jest wypełniane pozycji końcowej. Ustaw ten argument ma wartość null, jeśli te informacje nie są potrzebne.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 Zakres określony w pozycji dokument w lokalizacji punktu przerwania jest używany przez aparat debugowania (DE) do przodu wyszukiwania instrukcję, która faktycznie przyczynia się kod. Na przykład rozważmy następujący kod:  
  
```  
Line 5: // comment  
Line 6: x = 1;  
```  
  
 Wiersz 5 przyczynia się żadnego kodu do debugowanego programu. Jeśli debuger, która ustawia punkt przerwania w wierszu 5 chce DE wyszukiwania do przodu pewien dla pierwszego wiersza, która wspiera kodu, debuger określić zakres, który zawiera dodatkowe Release candidate wiersze, gdy punkt przerwania może prawidłowo umieszczone. DE będzie następnie wyszukuj do przodu, za pomocą tych wierszy aż do znalezienia go wiersza, który mógłby odebrać punktu przerwania.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
