---
title: Wymagania wstępne dotyczące zdalnego debugowania aplikacji sieci Web | Microsoft Docs
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
ms.openlocfilehash: c8cbf0ae920be00980d270aae16d5e7d1f7a5313
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72574626"
---
# <a name="prerequisites-for-remote-debugging-web-applications"></a>Wstępne wymagania debugowania zdalnego aplikacji internetowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debuger umożliwia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] debugowanie aplikacji sieci Web w sposób przezroczysty na komputerze lokalnym lub serwerze zdalnym. Oznacza to, że debuger działa tak samo, jak i umożliwia korzystanie z tych samych funkcji na dowolnym komputerze. Aby debugowanie zdalne działało prawidłowo, należy jednak spełnić pewne wymagania wstępne.  
  
- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] na serwerze, który ma być debugowany, muszą być zainstalowane składniki debugowania zdalnego. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zdalnego debugowania](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
- Domyślnie [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] proces roboczy jest uruchamiany jako proces użytkownika ASPNET. W związku z tym należy mieć uprawnienia administratora na komputerze, na którym [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] jest uruchamiana jego debugowanie. Nazwa [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu roboczego zależy od scenariusza debugowania i wersji usług IIS. Aby uzyskać więcej informacji, zobacz [How to: find a Name the ASP.NET Process](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji ASP.NET i AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Wymagania systemowe](../debugger/aspnet-debugging-system-requirements.md)
