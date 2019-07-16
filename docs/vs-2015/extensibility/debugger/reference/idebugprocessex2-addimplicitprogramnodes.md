---
title: IDebugProcessEx2::AddImplicitProgramNodes | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes
helpviewer_keywords:
- IDebugProcessEx2::AddImplicitProgramNodes method
ms.assetid: 8b491b00-f9e7-45b3-9115-fe58c3464289
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: faca728144bde572d8a1d3424fbfcf908403d679
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68202821"
---
# <a name="idebugprocessex2addimplicitprogramnodes"></a>IDebugProcessEx2::AddImplicitProgramNodes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Metoda ta umożliwia dodanie węzła dla każdego silnika debugowania (DE) określony program.  
  
## <a name="syntax"></a>Składnia  
  
```cpp#  
HRESULT AddImplicitProgramNodes(  
   REFGUID guidLaunchingEngine,  
   GUID*   rgguidSpecificEngines,  
   DWORD   celtSpecificEngines  
);  
```  
  
```csharp  
int AddImplicitProgramNodes(  
   ref Guid guidLaunchingEngine,  
   Guid[]   rgguidSpecificEngines,  
   uint     celtSpecificEngines  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `guidLaunchingEngine`  
 [in] `GUID` Z DE, która ma być używany do uruchamiania programów (przyjęto, że można dodać węzły swój własny program).  
  
 `rgguidSpecificEngines`  
 [in] Tablica `GUID`s DEs dla programu, który zostanie dodany węzłów.  
  
 `celtSpecificEngines`  
 [in] Liczba `GUID`s w `rgguidSpecificEngines` tablicy.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeśli operacja się powiedzie, zwraca `S_OK`; w przeciwnym razie zwraca kod błędu.  
  
## <a name="remarks"></a>Uwagi  
 [Program węzłów](../../../extensibility/debugger/program-nodes.md) zostanie dodana dla każdego DE wymienionych w `rgguidSpecificEngines`— z wyjątkiem uruchamiania aparatu (podany w `guidLaunchingEngine`), który zakłada się, że dodanie węzła swój własny program jest uruchamiany program.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)   
 [Węzły programu](../../../extensibility/debugger/program-nodes.md)
