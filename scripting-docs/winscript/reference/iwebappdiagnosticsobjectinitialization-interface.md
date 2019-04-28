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
ms.openlocfilehash: a992f8512d4927eeb58d6437ccb830abda688b28
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443681"
---
# <a name="iwebappdiagnosticsobjectinitialization-interface"></a>Interfejs IWebAppDiagnosticsObjectInitialization
Można zaimplementować ten interfejs dla klasy, które implementują [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md). [Interfejs IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md) jest implementowany przez obiekt, który implementuje [interfejs IDebugApplication](../../winscript/reference/idebugapplication-interface.md). W większości przypadków ten obiekt jest menedżerów PDM.  
  
 Po utworzeniu obiektu [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) jest wywoływana z odwołaniem do menedżerów PDM debugowania aplikacji i `hPassToObject` parametru `CreateObjectWithSiteAtWebApp`.  
  
> [!IMPORTANT]
> `IWebAppDiagnosticsObjectInitialization` znajduje się w zestawie activdbg100.h.  
  
## <a name="methods"></a>Metody  
 Ten interfejs udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md)|Inicjuje obiekt.|