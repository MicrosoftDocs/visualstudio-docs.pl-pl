---
title: Interfejs IWebAppDiagnosticsSetup | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: b84fd126ebd4d311264efa5d2156f9d83961fee9
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58148753"
---
# <a name="iwebappdiagnosticssetup-interface"></a>Interfejs IWebAppDiagnosticsSetup
Ten interfejs jest implementowany przez program PDM w debugowaniu aplikacji w języku do tworzenia obiektów COM w procesie, który jest debugowany i włączanie diagnostyki sieci web. Jeśli program PDM debugowania aplikacji obiekt implementuje [IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438), wymaga programu Internet Explorer [setsite —](http://go.microsoft.com/fwlink/?LinkId=232439) go po jego utworzeniu i przebiegów w odwołaniu do [IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449). Aplikacja WWA wywołuje [setsite —](http://go.microsoft.com/fwlink/?LinkId=232439) i przebiegów w WWA interfejsu IWebApplicationHost zamiast tego. Jeśli [setsite —](http://go.microsoft.com/fwlink/?LinkId=232439) została wywołana z wartością NIEZEROWĄ [IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) zwraca wartość true. Jeśli nie, zwraca wartość false i wywołania [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) się nie powieść.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsSetup` jest implementowany przez program PDM w wersji 11.0 i nowszych. Znajduje się w zestawie activdbg100.h.  
  
## <a name="methods"></a>Metody  
 Ten interfejs udostępnia następujące metody.  
  
|Metoda|Opis|  
|------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Pobiera dokumenty tekstowe, ukryte przez określony filtr.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Określa, czy określony dokument należy do jednego z węzłów podrzędnych tego węzła.|