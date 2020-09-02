---
title: 'Instrukcje: Włączanie ustawień zabezpieczeń ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1b104a7a0451da7f772077d2f566b36b9f601c17
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64797257"
---
# <a name="how-to-enable-clickonce-security-settings"></a>Porady: włączenie ustawień zabezpieczeń technologii ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby można było opublikować aplikację, należy włączyć zabezpieczenia dostępu kodu dla aplikacji ClickOnce. Jest to wykonywane automatycznie podczas publikowania aplikacji przy użyciu Kreatora publikacji.  
  
 W niektórych przypadkach włączenie zabezpieczeń dostępu kodu może mieć wpływ na wydajność podczas kompilowania lub debugowania aplikacji. w takich przypadkach można tymczasowo wyłączyć ustawienia zabezpieczeń.  
  
 Ustawienia zabezpieczeń ClickOnce można włączać lub wyłączać na stronie **zabezpieczenia** **projektanta projektu**.  
  
### <a name="to-enable-clickonce-security-settings"></a>Aby włączyć ustawienia zabezpieczeń ClickOnce  
  
1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.  
  
2. Kliknij kartę **Zabezpieczenia**.  
  
3. Zaznacz pole wyboru **Włącz ustawienia zabezpieczeń ClickOnce** .  
  
     Teraz możesz dostosować ustawienia zabezpieczeń aplikacji na stronie Zabezpieczenia.  
  
    > [!NOTE]
    > To pole wyboru jest wybierane automatycznie za każdym razem, gdy aplikacja jest publikowana przy użyciu kreatora **publikacji** .  
  
### <a name="to-disable-clickonce-security-settings"></a>Aby wyłączyć ustawienia zabezpieczeń ClickOnce  
  
1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.  
  
2. Kliknij kartę **Zabezpieczenia**.  
  
3. Wyczyść pole wyboru **Włącz ustawienia zabezpieczeń ClickOnce** .  
  
     Aplikacja zostanie uruchomiona z pełnymi ustawieniami zabezpieczeń zaufania; wszystkie ustawienia na stronie **zabezpieczenia** zostaną zignorowane.  
  
    > [!NOTE]
    > Za każdym razem, gdy aplikacja jest publikowana przy użyciu Kreatora publikacji, to pole wyboru zostanie zaznaczone. należy wyczyścić ją ponownie po każdym pomyślnym opublikowaniu.  
  
## <a name="see-also"></a>Zobacz też  
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
