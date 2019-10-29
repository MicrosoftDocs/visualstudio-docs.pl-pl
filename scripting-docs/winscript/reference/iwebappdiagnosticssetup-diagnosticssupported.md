---
title: IWebAppDiagnosticsSetup::D iagnosticsSupported | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsSetup::DiagnosticsSupported
ms.assetid: 5bbcd0d0-1460-4cf7-bbb1-f4f4a04f739a
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd27e7c8759054fa2d7d67858d8d006fa9c9a152
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984582"
---
# <a name="iwebappdiagnosticssetupdiagnosticssupported"></a>IWebAppDiagnosticsSetup::DiagnosticsSupported
Określa, czy Diagnostyka jest obsługiwana w tej aplikacji. Jeśli funkcja [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) została wywołana w obiekcie implementującym ten interfejs o wartości innej niż null, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) zwraca `true`. Jeśli nie, zwraca `false` i wywołuje wywołania [IWebAppDiagnosticsSetup:: CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) .  
  
> [!IMPORTANT]
> [Interfejs IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md) jest implementowany przez PDM v 11.0 i nowsze. Znaleziono w activdbg100.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DiagnosticsSupported(        [out, retval] VARIANT_BOOL* pRetVal        );  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 Jeśli funkcja [SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite) została wywołana w obiekcie implementującym ten interfejs o wartości innej niż null, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) zwraca `true`. Jeśli nie, zwraca `false`i wywołania do [IWebAppDiagnosticsSetup:: CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) kończą się niepowodzeniem.