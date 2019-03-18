---
title: Interfejs IDebugAsyncOperation | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugAsyncOperation interface
ms.assetid: ebb2ea75-1443-4d8a-812d-171a166f5f9d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 820ecc40924ace4153b76f46c8b8fd1603512ebb
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58150819"
---
# <a name="idebugasyncoperation-interface"></a>Interfejs IDebugAsyncOperation
Menedżer debugowania procesów implementuje `IDebugAsyncOperation` interfejsu. Aparat języka wywołuje `IDebugApplication::CreateAsyncDebugOperation` metodę, aby uzyskać odwołanie do tego interfejsu. Można użyć aparatu języka `IDebugAsyncOperation` interfejsu, aby zapewnić dostęp asynchronicznych operacji synchronicznych debugowania.  
  
 Oprócz metod odziedziczone `IUnknown`, `IDebugAsyncOperation` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugAsyncOperation::GetSyncDebugOperation](../../winscript/reference/idebugasyncoperation-getsyncdebugoperation.md)|Zwraca Operacja synchroniczna debugowania skojarzone z tym obiektem.|  
|[IDebugAsyncOperation::Start](../../winscript/reference/idebugasyncoperation-start.md)|Powoduje, że operacja asynchroniczna rozpocząć.|  
|[IDebugAsyncOperation::Abort](../../winscript/reference/idebugasyncoperation-abort.md)|Anuluje operację.|  
|[IDebugAsyncOperation::QueryIsComplete](../../winscript/reference/idebugasyncoperation-queryiscomplete.md)|Określa, jeśli operacja debugowania została zakończona.|  
|[IDebugAsyncOperation::GetResult](../../winscript/reference/idebugasyncoperation-getresult.md)|Zawiera wartości zwracanej i parametru zwracanego obiektu z operacji synchronicznych debugowania.|