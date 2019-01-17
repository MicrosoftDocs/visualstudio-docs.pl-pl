---
title: Interfejs IDebugHelper | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugHelper interface
ms.assetid: ef5691e0-1d82-42c2-997c-888e31c478dd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba760dc15cc0a3d3f2f0d80f3a16c5621582bc11
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347479"
---
# <a name="idebughelper-interface"></a>Interfejs IDebugHelper
Służy jako fabrykę do przeglądarki obiektów i punktów połączenia proste. Menedżer debugowania procesów (menedżerów PDM) implementuje ten interfejs, który jest używany przez aparatów skryptów.  
  
 Oprócz metod odziedziczone `IUnknown`, `IDebugHelper` interfejsu udostępnia następujące metody.  
  
## <a name="methods-in-vtable-order"></a>Metody w Vtable kolejności  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)|Zwraca przeglądarkę właściwości, która otacza wariant.|  
|[IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)|Zwraca przeglądarkę właściwości opakowuje Typ VARIANT, która umożliwia niestandardowych konwersję typu VARIANT wartości lub VARTYPE na ciągi.|  
|[IDebugHelper::CreateSimpleConnectionPoint](../../winscript/reference/idebughelper-createsimpleconnectionpoint.md)|Zwraca interfejs zdarzenia, który otacza danego `IDispatch` obiektu.|