---
title: IDebugApplicationNode100::QueryIsChildNode | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::QueryIsChildNode
ms.assetid: 4f36f435-0f34-4f9e-bba3-e75285fd7bbb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 959de620e1e556d92a51dcab0062fa6ff055ec46
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446662"
---
# <a name="idebugapplicationnode100queryischildnode"></a>IDebugApplicationNode100::QueryIsChildNode
Określa, czy określony dokument należy do jednego z węzłów podrzędnych tego węzła.  
  
> [!IMPORTANT]
> [Interfejs IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md) jest implementowany przez program PDM 10.0 lub nowszym. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT QueryIsChildNode(        [in] IDebugDocument* pSearchKey        );  
```  
  
#### <a name="parameters"></a>Parametry  
 `pSearchKey`  
 Klucz wyszukiwania.  
  
## <a name="see-also"></a>Zobacz też  
 [IDebugApplicationNode100, interfejs](../../winscript/reference/idebugapplicationnode100-interface.md)