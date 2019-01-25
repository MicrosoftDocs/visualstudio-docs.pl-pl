---
title: 'Przygotowanie debugowania: Aplikacje sieci Web programu ASP.NET | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
helpviewer_keywords:
- debugging ASP.NET Web applications
- debugging [Visual Studio], Web applications
ms.assetid: bcfb1080-98d1-42f9-96af-186fb14f232a
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: baa5e454eec00c2530190834974cd946838a0947
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54781303"
---
# <a name="debugging-preparation-aspnet-web-applications"></a>Przygotowanie debugowania: Aplikacje internetowe ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Szablon witryny sieci Web tworzy aplikację formularza sieci Web. Po utworzeniu witryny sieci Web przy użyciu tego szablonu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tworzy ustawienia domyślne dla debugowania. W **właściwości projektu** okno dialogowe, można określić czy ma być stronie startowej strony sieci Web. Po rozpoczęciu debugowania [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]witryny sieci Web przy użyciu tych ustawień domyślnych [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] uruchamia program Internet Explorer i dołącza debuger [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] proces roboczy (aspnet_wp.exe lub w3wp.exe). Aby uzyskać więcej informacji, zobacz [wymagania systemowe](../debugger/aspnet-debugging-system-requirements.md).  
  
### <a name="to-create-a-web-forms-application"></a>Aby utworzyć aplikację formularzy sieci Web  
  
1.  Na **pliku** menu, wybierz **nową witrynę sieci Web**.  
  
2.  W **nową witrynę sieci Web** okno dialogowe, wybierz opcję [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] **witryny sieci Web**.  
  
3.  Kliknij przycisk **OK**.  
  
### <a name="to-debug-your-web-form"></a>Aby debugować formularz sieci Web  
  
1.  Ustaw co najmniej jednego punktu przerwania w funkcji i procedury obsługi zdarzeń.  
  
     Aby uzyskać więcej informacji, zobacz [punkty przerwania i śledzenia](http://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2.  Po osiągnięciu punktu przerwania przejść przez kod wewnątrz funkcji. Obserwuj wykonywanie kodu, dopóki nie można ustalić przyczynę problemu.  
  
     Aby uzyskać więcej informacji, zobacz [przechodzenie krok po kroku](http://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9) i [debugowanie aplikacji sieci Web i skryptu](../debugger/debugging-web-applications-and-script.md).  
  
## <a name="changing-default-configurations"></a>Zmiana konfiguracji domyślnych  
 Jeśli chcesz zmienić domyślne debugowania i zwalniania konfiguracji utworzone przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], możesz to zrobić. Aby uzyskać więcej informacji, zobacz [jak: Ustaw wartość Debug i Release konfiguracje](../debugger/how-to-set-debug-and-release-configurations.md).  
  
#### <a name="to-change-the-default-debug-configuration"></a>Aby zmienić domyślną konfigurację debugowania  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy witrynę sieci Web i wybierz **stron właściwości** otworzyć **stron właściwości** okno dialogowe.  
  
2.  Kliknij przycisk **opcje uruchamiania**.  
  
3.  Ustaw **Akcja uruchamiania** do strony sieci Web, które powinny być wyświetlane jako pierwsze.  
  
4.  W obszarze **debugery**, upewnij się, że **debugowanie ASP.NET** jest zaznaczone.  
  
     Aby uzyskać więcej informacji, zobacz [ustawienia stron właściwości dla projektów sieci Web](../debugger/property-pages-settings-for-web-projects.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie kodu zarządzanego](../debugger/debugging-managed-code.md)
