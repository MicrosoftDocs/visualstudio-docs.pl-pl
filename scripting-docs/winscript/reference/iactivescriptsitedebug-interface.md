---
title: IActiveScriptSiteDebug Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 339325686d2a98e34c6e9f96056612769a9e110e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348311"
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