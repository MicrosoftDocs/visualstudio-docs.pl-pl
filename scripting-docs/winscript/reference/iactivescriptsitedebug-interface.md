---
title: IActiveScriptSiteDebug Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebug interface
ms.assetid: 2557ee09-688b-4c03-a821-180c24dfa0e6
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3cd8043648586ed3c614cbb137e51d992d7ae29b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992465"
---
# <a name="iactivescriptsitedebug-interface"></a>Interfejs IActiveScriptSiteDebug
Implementowanie hostów inteligentnych `IActiveScriptSiteDebug` interfejsu, aby wykonać Zarządzanie dokumentami i do wzięcia udziału w debugowaniu. `IActiveScriptSite` Obiekt zwykle zawiera implementację `IActiveScriptSiteDebug` interfejsu. Jeśli zostanie to zrobione, należy wywołać `IActiveScriptSite::QueryInterface` metodę, aby uzyskać `IActiveScriptSiteDebug` interfejsu.  
  
 Oprócz metod odziedziczone `IUnknown`, `IActiveScriptSiteDebug` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IActiveScriptSiteDebug::GetDocumentContextFromPosition](../../winscript/reference/iactivescriptsitedebug-getdocumentcontextfromposition.md)|Używane przez aparat języka, aby delegować `IDebugCodeContext::GetSourceContext`.|  
|[IActiveScriptSiteDebug::GetApplication](../../winscript/reference/iactivescriptsitedebug-getapplication.md)|Zwraca obiekt aplikacji debugowania, które są skojarzone z tą lokacją skryptu.|  
|[IActiveScriptSiteDebug::GetRootApplicationNode](../../winscript/reference/iactivescriptsitedebug-getrootapplicationnode.md)|Pobiera węzeł aplikacji, w ramach której skrypt dokumenty powinny zostać dodane.|  
|[IActiveScriptSiteDebug::OnScriptErrorDebug](../../winscript/reference/iactivescriptsitedebug-onscripterrordebug.md)|Umożliwia hosta inteligentnego określić sposób obsługi błędów czasu wykonywania.|