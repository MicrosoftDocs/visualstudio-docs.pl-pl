---
title: Interfejs IDebugAsyncOperation | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: c0088fddd2661d6711c9a18495f4b8704f782b3c
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349996"
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