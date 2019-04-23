---
title: Wstępne wymagania zdalne debugowanie aplikacji sieci Web | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging ASP.NET Web applications, remote servers
- remote debugging, prerequisites
- remote servers, debugging Web applications
ms.assetid: 1cd777b5-6d20-4ca6-a0df-51653b118469
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 46bf49567558cab556180c470bfd4b80d93f5dbb
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60105516"
---
# <a name="prerequistes-for-remote-debugging-web-applications"></a>Wstępne wymagania debugowania zdalnego aplikacji internetowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] debugera można debugować aplikacji sieci Web w sposób niewidoczny dla użytkownika na komputerze lokalnym lub zdalnym serwerem. To oznacza, że funkcje debugera taki sam sposób i umożliwia korzystanie z tej samej funkcji na komputerze. Zdalne debugowanie działało poprawnie, istnieją pewne wymagania wstępne.  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] składniki zdalnego debugowania musi być zainstalowany na serwerze, który chcesz debugować. Aby uzyskać więcej informacji, zobacz [ustawienie zapasowej zdalne debugowanie](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
- Domyślnie [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] proces roboczy, który jest uruchamiany jako proces użytkownika ASPNET. W rezultacie, musi mieć uprawnienia administratora na komputerze, gdzie [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] przebiegów, aby go debugować. Nazwa [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu roboczego zależy od scenariusz debugowania i wersję usług IIS. Aby uzyskać więcej informacji, zobacz [jak: Znajdowanie nazwy procesu ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji ASP.NET i AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Wymagania systemowe](../debugger/aspnet-debugging-system-requirements.md)
