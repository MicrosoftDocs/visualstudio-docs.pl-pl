---
title: IWebAppDiagnosticsObjectInitialization::Initialize | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IWebAppDiagnosticsObjectInitialization::Initialize
ms.assetid: 7ccfac28-9f65-4e1c-a0fb-a8a6c7f75b63
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d887872c1735aabd0bc19d8de362f10044685bac
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58147361"
---
# <a name="iwebappdiagnosticsobjectinitializationinitialize"></a>IWebAppDiagnosticsObjectInitialization::Initialize
Inicjuje obiektów utworzonych za pomocą [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md).  
  
> [!IMPORTANT]
>  [Interfejs IWebAppDiagnosticsObjectInitialization](../../winscript/reference/iwebappdiagnosticsobjectinitialization-interface.md) znajduje się w zestawie activdbg100.h.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT Initialize(        [in, annotation("__in")] HANDLE_PTR hPassedHandle,        [in, annotation("__in")] IUnknown* pDebugApplication        );  
```  
  
#### <a name="parameters"></a>Parametry  
 `hPassedHandle`  
 Uchwyt, który został przekazany do [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) method in Class metoda `hPassToObject` parametru.  
  
 `pDebugApplication`  
 Program PDM w aplikacji za pomocą którego został utworzony obiekt.