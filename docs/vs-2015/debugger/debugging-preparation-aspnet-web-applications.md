---
title: 'Przygotowanie debugowania: Aplikacje sieci Web ASP.NET | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 59f4f3e1db92c5f7b46a9bb9e1e164fc25b01010
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51730685"
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
  
     Aby uzyskać więcej informacji, zobacz [punkty przerwania i śledzenia](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2.  Po osiągnięciu punktu przerwania przejść przez kod wewnątrz funkcji. Obserwuj wykonywanie kodu, dopóki nie można ustalić przyczynę problemu.  
  
     Aby uzyskać więcej informacji, zobacz [przechodzenie krok po kroku](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9) i [debugowanie aplikacji sieci Web i skryptu](../debugger/debugging-web-applications-and-script.md).  
  
## <a name="changing-default-configurations"></a>Zmiana konfiguracji domyślnych  
 Jeśli chcesz zmienić domyślne debugowania i zwalniania konfiguracji utworzone przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], możesz to zrobić. Aby uzyskać więcej informacji, zobacz [porady: Ustawianie debugowania i konfiguracje wydania](../debugger/how-to-set-debug-and-release-configurations.md).  
  
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



