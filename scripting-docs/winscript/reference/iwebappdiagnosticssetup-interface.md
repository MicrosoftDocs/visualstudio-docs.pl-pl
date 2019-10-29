---
title: Interfejs IWebAppDiagnosticsSetup | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup Interface
ms.assetid: ec7359f2-633e-4d59-b64b-9cab0134dfd0
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1e9bb3905da6227b978bc27b96493500f8d6d2ff
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984538"
---
# <a name="iwebappdiagnosticssetup-interface"></a>Interfejs IWebAppDiagnosticsSetup
Ten interfejs jest implementowany przez aplikację debugowania PDM do tworzenia obiektów COM w debugowanym procesie i w celu włączenia diagnostyki sieci Web. Jeśli obiekt aplikacji PDM Debug implementuje [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite), program Internet Explorer wywołuje [ją w programie](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) , po utworzeniu i przekazuje odwołanie do [IWebBrowser2](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa752127(v=vs.85)). Aplikacja WWA wywołuje metodę [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) i przekazuje w IWebApplicationHost interfejsie WWA. Jeśli funkcja [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) została wywołana o wartości innej niż null, [IWebAppDiagnosticsSetup::D iagnosticssupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) zwraca wartość true. Jeśli nie, zwraca wartość false, a wywołania [IWebAppDiagnosticsSetup:: CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) kończą się niepowodzeniem.  
  
> [!IMPORTANT]
> `IWebAppDiagnosticsSetup` jest implementowana przez PDM v 11.0 i nowsze. Znajduje się w zestawie activdbg100.h.  
  
## <a name="methods"></a>Metody  
 Ten interfejs uwidacznia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Pobiera dokumenty tekstowe, które są ukryte przez określony filtr.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Określa, czy określony dokument należy do jednego z węzłów podrzędnych tego węzła.|