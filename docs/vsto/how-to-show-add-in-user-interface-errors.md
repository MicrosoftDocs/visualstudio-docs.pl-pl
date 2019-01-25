---
title: 'Instrukcje: Pokaż błędy interfejsu użytkownika dodatku'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- add-ins [Office development in Visual Studio], user interface errors
- errors [Office development in Visual Studio], user interface errors
- user interfaces [Office development in Visual Studio], errors
- application-level add-ins [Office development in Visual Studio], user interface errors
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 466b316340f922d13ed559791d1340912c4cecfd
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54862918"
---
# <a name="how-to-show-add-in-user-interface-errors"></a>Instrukcje: Pokaż błędy interfejsu użytkownika dodatku
  Domyślnie jeśli dodatku narzędzi VSTO prób do manipulowania Microsoft Office interfejsu użytkownika (UI) i kończy się niepowodzeniem, żaden komunikat o błędzie jest wyświetlany. Można jednak skonfigurować aplikacje Microsoft Office, aby wyświetlić komunikaty błędów, które odnoszą się do interfejsu użytkownika. Te komunikaty można użyć w celu określenia, dlaczego niestandardowa Wstążka jest niewidoczny, lub dlaczego Wstążka pojawia się, ale nie formanty są wyświetlane.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## <a name="to-show-vsto-add-in-user-interface-errors"></a>Aby wyświetlić błędy interfejsu użytkownika dodatku narzędzi VSTO  
  
1.  Uruchom aplikację.  
  
2.  Kliknij przycisk **pliku** kartę.  
  
3.  Kliknij przycisk **opcje**.  
  
4.  W okienku kategorii kliknij **zaawansowane**.  
  
5.  W okienku szczegółów wybierz **błędów interfejsu użytkownika dodatku narzędzi VSTO dla programów Pokaż**, a następnie kliknij przycisk **OK**.  
  
    > [!NOTE]  
    >  Dla programu Outlook **błędów interfejsu użytkownika dodatku narzędzi VSTO dla programów Pokaż** pole wyboru znajduje się w **Developer** części okienka szczegółów. Dla innych aplikacji, pole wyboru znajduje się w **ogólne** części okienka szczegółów.  
  
## <a name="see-also"></a>Zobacz także  
 [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md)   
 [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)   
 [Wstążka — omówienie](../vsto/ribbon-overview.md)   
 [Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)  
