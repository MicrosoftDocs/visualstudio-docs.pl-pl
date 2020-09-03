---
title: 'Instrukcje: debugowanie aplikacji sieci Web | Microsoft Docs'
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
- Web services, debugging
- ASP.NET Web Forms, debugging
- ASP.NET, debugging Web applications
- debugging ASP.NET Web applications, during development
ms.assetid: 6440d12e-6b29-42c5-a958-99aeaaff480f
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cd3cbbcd740c0f124b8ab4379204a9d425cd541c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205403"
---
# <a name="how-to-debug-web-applications"></a>Porady: debugowanie aplikacji internetowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] jest podstawową technologią tworzenia aplikacji sieci Web w programie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Debuger udostępnia zaawansowane narzędzia do debugowania [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web lokalnie lub na serwerze zdalnym. W tym temacie opisano sposób debugowania [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] projektu podczas opracowywania. Aby uzyskać informacje o sposobie debugowania [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web, która została już wdrożona na serwerze produkcyjnym, zobacz [debugowanie wdrożonych aplikacji sieci Web](../debugger/debugging-deployed-web-applications.md).  
  
 Aby debugować [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikację:  
  
- Musisz mieć wymagane uprawnienia. Aby uzyskać więcej informacji, zobacz [Wymagania systemowe](../debugger/aspnet-debugging-system-requirements.md).  
  
- [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Debugowanie musi być włączone we **właściwościach projektu**.  
  
- Plik konfiguracyjny aplikacji (Web.config) musi być ustawiony w tryb debugowania. Tryb debugowania powoduje [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] wygenerowanie symboli dla dynamicznie generowanych plików i umożliwia debugerowi dołączenie do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Ustawia to automatycznie po rozpoczęciu debugowania, jeśli projekt został utworzony z szablonu projektów sieci Web.  
  
- Aby uzyskać więcej informacji, zobacz [How to: Enable Debug for ASP.NET Applications](../debugger/how-to-enable-debugging-for-aspnet-applications.md).  
  
### <a name="to-debug-a-web-application-during-development"></a>Aby debugować aplikację sieci Web podczas tworzenia  
  
1. W menu **debugowanie** kliknij przycisk **Rozpocznij** , aby rozpocząć debugowanie aplikacji sieci Web.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] kompiluje projekt aplikacji sieci Web, w razie potrzeby wdraża aplikację, uruchamia serwer programistyczny ASP.NET w przypadku debugowania lokalnego i dołącza do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu roboczego.  
  
2. Użyj debugera, aby ustawić i wyczyścić punkty przerwania, wykonać krok i wykonywać inne operacje debugowania, jak w przypadku dowolnej aplikacji.  
  
     Aby uzyskać więcej informacji, zobacz [podstawy debugera](../debugger/debugger-basics.md).  
  
3. W menu **debugowanie** kliknij przycisk **Zatrzymaj debugowanie** , aby zakończyć sesję debugowania, lub w menu **plik** w programie Internet Explorer kliknij przycisk **Zamknij**.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie aplikacji sieci Web i skryptu](../debugger/debugging-web-applications-and-script.md)   
 [Debugowanie aplikacji ASP.NET i AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Porady: włączanie debugowania dla aplikacji ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
