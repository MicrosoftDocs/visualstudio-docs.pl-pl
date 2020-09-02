---
title: 'Instrukcje: wyłączanie aktywacji adresu URL aplikacji ClickOnce za pomocą projektanta | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 27690ab275d0c7ef2a090fa8ef2e42887ae9daeb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153813"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Porady: wyłączanie aktywacji adresu URL aplikacji ClickOnce za pomocą Projektanta
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zazwyczaj [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacja zostanie uruchomiona automatycznie po zainstalowaniu z serwera sieci Web. Ze względów bezpieczeństwa może być konieczne wyłączenie tego zachowania i poinformowanie użytkowników, aby uruchomili aplikację z menu **Start** . Poniższa procedura opisuje sposób wyłączania aktywacji adresu URL.  
  
 Tej techniki można używać tylko w przypadku [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji zainstalowanych na komputerze użytkownika z serwera sieci Web. Nie może być używany tylko w przypadku aplikacji online, które można uruchomić tylko przy użyciu adresu URL. Aby uzyskać więcej informacji o różnicach między aplikacjami tylko online i zainstalowanymi, zobacz [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Ta procedura powoduje użycie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . To zadanie można także wykonać przy użyciu [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] . Aby uzyskać więcej informacji, zobacz [jak: wyłączanie aktywacji adresu URL aplikacji ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Aby wyłączyć aktywację adresów URL dla aplikacji  
  
1. Kliknij prawym przyciskiem myszy nazwę projektu w **Eksplorator rozwiązań**, a następnie kliknij pozycję **Właściwości**.  
  
2. Na stronie **Właściwości** kliknij kartę **Publikowanie** .  
  
3. Kliknij pozycję **Opcje**.  
  
4. Kliknij pozycję **manifesty**.  
  
5. Zaznacz pole wyboru **z etykietą Blokuj aplikacje przed aktywowaniem za pośrednictwem adresu URL**.  
  
6. Wdróż aplikację.  
  
## <a name="see-also"></a>Zobacz też  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
