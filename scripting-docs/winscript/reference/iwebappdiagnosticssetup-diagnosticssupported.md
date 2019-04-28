---
title: IWebAppDiagnosticsSetup::DiagnosticsSupported | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 1d4214dea16c1e8a96ece7428f9ea73640025a9c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63443673"
---
# <a name="iwebappdiagnosticssetupdiagnosticssupported"></a>IWebAppDiagnosticsSetup::DiagnosticsSupported
Określa, czy diagnostyki są obsługiwane w tej aplikacji. Jeśli [setsite —](http://go.microsoft.com/fwlink/?LinkId=232439) została wywołana na obiekt implementujący ten interfejs o wartości innej niż NULL, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) zwraca `true`. Jeśli nie, zwraca `false` i wywołania [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) się nie powieść.  
  
> [!IMPORTANT]
> [Interfejs IWebAppDiagnosticsSetup](../../winscript/reference/iwebappdiagnosticssetup-interface.md) jest implementowany przez program PDM w wersji 11.0 i nowszych. Znaleziono w activdbg100.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT DiagnosticsSupported(        [out, retval] VARIANT_BOOL* pRetVal        );  
```  
  
#### <a name="parameters"></a>Parametry  
 `pRetVal`  
 Jeśli [setsite —](http://go.microsoft.com/fwlink/?LinkId=232439) została wywołana na obiekt implementujący ten interfejs o wartości innej niż NULL, [DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) zwraca `true`. Jeśli nie, zwraca `false`i zwraca [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) się nie powieść.