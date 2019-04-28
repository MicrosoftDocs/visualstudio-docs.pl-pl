---
title: IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 42f92cfe9245a5e3a6342c31fc996ae2db50ef70
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443699"
---
# <a name="iwebappdiagnosticssetupcreateobjectwithsiteatwebapp"></a>IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp
Ta metoda tworzy wspólnej klasy o identyfikatorze przekazywania przy użyciu `rclsid` przy użyciu `dwClsContext`. Jest to w sposób podobny do [IRemoteDebugApplication::CreateInstanceAtApplication](../../winscript/reference/iremotedebugapplication-createinstanceatapplication.md) działa, chyba że w przypadku właściwości `CreateObjectWithSiteAtWebApp` asynchronicznie tworzenia obiektu w wątku interfejsu użytkownika aplikacji sieci web. Obiekt określony przez identyfikator klasy należy zaimplementować [interfejs IWebAppDiagnosticsObjectInitialization](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md). Po utworzeniu obiektu [IWebAppDiagnosticsObjectInitialization::Initialize](../../winscript/reference/iwebappdiagnosticsobjectinitialization-initialize.md) jest wywoływana z odwołaniem do menedżerów PDM debugowania aplikacji i `hPassToObject` parametru `CreateObjectWithSiteAtWebApp`. Ta metoda służy do przekazania do niej dojścia do potoku anonimowego, które zostały skopiowane, za pomocą [DuplicateHandle](http://go.microsoft.com/fwlink/?LinkId=232450).  
  
> [!IMPORTANT]
> [Interfejs IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md) jest implementowany przez program PDM w wersji 11.0 i nowszych. Znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CreateObjectWithSiteAtWebApp(        [in] REFCLSID rclsid,         [in] DWORD dwClsContext,         [in] REFIID riid,         [in] DWORD_PTR hPassToObject        );  
```  
  
#### <a name="parameters"></a>Parametry  
 `rclsid`  
 Identyfikator klasy do utworzenia.  
  
 `dwClsContext`  
 Kontekst, w którym będzie uruchamiany kod. W większości przypadków jest CLSCTX_INPROC_SERVER.  
  
 `riid`  
 Nie używany.  
  
 `hPassToObject`  
 Wartość, które zostaną przekazane do obiektu po jego utworzeniu w wątku interfejsu użytkownika, jeśli obiekt implementuje [interfejs IWebAppDiagnosticsObjectInitialization](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md).