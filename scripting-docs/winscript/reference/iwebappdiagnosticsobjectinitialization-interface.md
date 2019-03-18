---
title: Interfejs IWebAppDiagnosticsObjectInitialization | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsObjectInitialization Interface
ms.assetid: 32847838-01d9-4205-a811-3043d8c7a917
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 67cf59965d47b2a0e29bbe6280d69acf0000a20d
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58149578"
---
# <a name="iwebappdiagnosticsobjectinitialization-interface"></a>Interfejs IWebAppDiagnosticsObjectInitialization
Można zaimplementować ten interfejs dla klasy, które implementują [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md). [Interfejs IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md) jest implementowany przez obiekt, który implementuje [interfejs IDebugApplication](../../winscript/reference/idebugapplication-interface.md). W większości przypadków ten obiekt jest menedżerów PDM.  
  
 Po utworzeniu obiektu [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) jest wywoływana z odwołaniem do menedżerów PDM debugowania aplikacji i `hPassToObject` parametru `CreateObjectWithSiteAtWebApp`.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsObjectInitialization` znajduje się w zestawie activdbg100.h.  
  
## <a name="methods"></a>Metody  
 Ten interfejs udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md)|Inicjuje obiekt.|