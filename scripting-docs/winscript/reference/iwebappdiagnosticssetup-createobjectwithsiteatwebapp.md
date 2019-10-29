---
title: 'IWebAppDiagnosticsSetup:: CreateObjectWithSiteAtWebApp | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
ms.assetid: 30975973-acb1-48f4-8266-5e097a57db22
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 253b995c200566868ac9ccc06b259e0a152e1676
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984605"
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
Ta metoda współtworzy klasę, której identyfikator został przekazany, `rclsid` przy użyciu `dwClsContext`. Jest to podobne do sposobu, w jaki [IRemoteDebugApplication:: CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) działa, z tą różnicą, że w przypadku `CreateObjectWithSiteAtWebApp` obiekt jest tworzony asynchronicznie w wątku interfejsu użytkownika aplikacji sieci Web. Obiekt określony przez identyfikator klasy powinien implementować [interfejs IWebAppDiagnosticsObjectInitialization](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md). Po utworzeniu obiektu [IWebAppDiagnosticsObjectInitialization:: Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) jest wywoływana z odwołaniem do aplikacji debugowania PDM i parametrem `hPassToObject` `CreateObjectWithSiteAtWebApp`. Tej metody można użyć do przekazania do aplikacji dojścia do anonimowego potoku, który został skopiowany przy użyciu [DuplicateHandle](/windows/win32/api/handleapi/nf-handleapi-duplicatehandle).  
  
> [!IMPORTANT]
> [Interfejs IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md) jest implementowany przez PDM v 11.0 i nowsze. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(        [in] REFCLSID rclsid,         [in] DWORD dwClsContext,         [in] REFIID riid,         [in] DWORD_PTR hPassToObject        );  
```  
  
#### <a name="parameters"></a>Parametry  
 `rclsid`  
 Identyfikator klasy do utworzenia.  
  
 `dwClsContext`  
 Kontekst, w którym zostanie uruchomiony kod. W większości przypadków jest to CLSCTX_INPROC_SERVER.  
  
 `riid`  
 Nie używany.  
  
 `hPassToObject`  
 Wartość, która zostanie przeniesiona do obiektu po jego utworzeniu w wątku interfejsu użytkownika, jeśli obiekt implementuje [interfejs IWebAppDiagnosticsObjectInitialization](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md).