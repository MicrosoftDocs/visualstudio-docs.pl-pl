---
title: 'Instrukcje: wyłączanie aktywacji adresu URL aplikacji ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 75a98706858323693ec01ec3c3420a6d2d25ffef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697213"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Porady: wyłączanie aktywacji adresu URL aplikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zazwyczaj [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacja zostanie uruchomiona automatycznie po zainstalowaniu z serwera sieci Web. Ze względów bezpieczeństwa może być konieczne wyłączenie tego zachowania i poinformowanie użytkowników, aby uruchomili aplikację z menu **Start** . Poniższa procedura opisuje sposób wyłączania aktywacji adresu URL.  
  
 Tej techniki można używać tylko w przypadku [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji zainstalowanych na komputerze użytkownika z serwera sieci Web. Nie może być używany tylko w przypadku aplikacji online, które można uruchomić tylko przy użyciu adresu URL. Aby uzyskać więcej informacji na temat różnic między aplikacjami tylko online i zainstalowanymi, zobacz [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Ta procedura używa [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] MageUI.exe narzędzia. Aby uzyskać więcej informacji na temat tego narzędzia, zobacz [MageUI.exe (narzędzie tworzenia i edycji manifestów, klient graficzny)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14). Tę procedurę można również wykonać za pomocą polecenia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="procedure"></a>Procedura  
  
#### <a name="to-disable-url-activation-for-your-application"></a>Aby wyłączyć aktywację adresów URL dla aplikacji  
  
1. Otwórz manifest wdrożenia w MageUI.exe. Jeśli jeszcze tego nie utworzono, wykonaj kroki opisane w [przewodniku: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2. Wybierz kartę **Opcje wdrażania** .  
  
3. Wyczyść pole wyboru **automatycznie uruchamiaj aplikację po zainstalowaniu** .  
  
4. Zapisz i podpisz manifest.  
  
## <a name="see-also"></a>Zobacz też  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
