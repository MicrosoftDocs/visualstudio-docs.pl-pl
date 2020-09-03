---
title: 'Przygotowanie debugowania: ASP.NET aplikacje sieci Web | Microsoft Docs'
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
ms.openlocfilehash: 7a80587062442688551d07128a2cec49a712adf6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691461"
---
# <a name="debugging-preparation-aspnet-web-applications"></a>Przygotowanie debugowania: Aplikacje internetowe ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Szablon witryny sieci Web tworzy aplikację formularza sieci Web. Podczas tworzenia witryny sieci Web przy użyciu tego szablonu program [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tworzy domyślne ustawienia dla debugowania. W oknie dialogowym **właściwości projektu** można określić, czy strona sieci Web ma być stroną startową. Po rozpoczęciu debugowania [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] witryny sieci Web przy użyciu tych ustawień domyślnych program [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Internet Explorer i dołącza debuger do [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu roboczego (aspnet_wp.exe lub w3wp.exe). Aby uzyskać więcej informacji, zobacz [Wymagania systemowe](../debugger/aspnet-debugging-system-requirements.md).  
  
### <a name="to-create-a-web-forms-application"></a>Aby utworzyć aplikację formularzy sieci Web  
  
1. W menu **plik** wybierz polecenie **Nowa witryna sieci Web**.  
  
2. W oknie dialogowym **Nowa witryna sieci Web** wybierz pozycję [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] **Witryna sieci Web**.  
  
3. Kliknij przycisk **OK**.  
  
### <a name="to-debug-your-web-form"></a>Aby debugować formularz sieci Web  
  
1. Ustaw co najmniej jeden punkt przerwania w funkcjach i obsłudze zdarzeń.  
  
     Aby uzyskać więcej informacji, zobacz [punkty przerwania i punkty śledzenia](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2. Po trafieniu punktu przerwania przejdź do kodu wewnątrz funkcji. Obserwuj wykonywanie kodu do momentu odizolowania problemu.  
  
     Aby uzyskać więcej informacji, zobacz [krokowe](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9) i [debugowanie aplikacji sieci Web i skryptów](../debugger/debugging-web-applications-and-script.md).  
  
## <a name="changing-default-configurations"></a>Zmienianie konfiguracji domyślnych  
 Jeśli chcesz zmienić domyślne konfiguracje debugowania i wydania utworzone przez [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] program, możesz to zrobić. Aby uzyskać więcej informacji, zobacz [How to: Set Debug and Release Configurations](../debugger/how-to-set-debug-and-release-configurations.md).  
  
#### <a name="to-change-the-default-debug-configuration"></a>Aby zmienić domyślną konfigurację debugowania  
  
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy witrynę sieci Web i wybierz polecenie **strony właściwości** , aby otworzyć okno dialogowe **strony właściwości** .  
  
2. Kliknij przycisk **Start Opcje**.  
  
3. Ustaw **akcję uruchamiania** na stronę sieci Web, która powinna być wyświetlana jako pierwsza.  
  
4. W obszarze **debugery**upewnij się, że jest zaznaczone polecenie **Debuguj ASP.NET** .  
  
     Aby uzyskać więcej informacji, zobacz [Ustawienia stron właściwości dla projektów sieci Web](../debugger/property-pages-settings-for-web-projects.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Ustawienia debugera i przygotowanie](../debugger/debugger-settings-and-preparation.md)   
 [Podstawowe informacje o debugerze](../debugger/debugger-basics.md)   
 [Zabezpieczenia debugera](../debugger/debugger-security.md)   
 [Debugowanie zarządzanego kodu](../debugger/debugging-managed-code.md)
