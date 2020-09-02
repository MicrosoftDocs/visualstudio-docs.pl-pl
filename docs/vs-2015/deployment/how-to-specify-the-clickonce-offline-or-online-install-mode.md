---
title: 'Instrukcje: Określanie trybu offline lub online instalacji usługi ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, specifying install mode
- install mode
- online applications
- offline applications
- ClickOnce install mode
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d4111ca5aee4a405a4a797dbfee14a3d4b50435f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149752"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Porady: określanie trybu offline lub online instalowania za pomocą technologii ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Install Mode`Dla [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji określa, czy aplikacja będzie dostępna w trybie offline, czy w trybie online. Po wybraniu **aplikacji jest dostępna tylko w trybie online**, użytkownik musi mieć dostęp do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] lokalizacji publikowania (strona sieci Web lub udział plików) w celu uruchomienia aplikacji. Po wybraniu **aplikacji jest również dostępna w trybie offline**aplikacja dodaje wpisy do menu **Start** i okno dialogowe **Dodawanie lub usuwanie programów** ; Użytkownik może uruchomić aplikację, gdy nie są połączeni.  
  
 `Install Mode`Można ją ustawić na stronie **Publikuj** **projektanta projektu**.  
  
 **Uwaga** `Install Mode` Można również ustawić za pomocą Kreatora publikacji. Aby uzyskać więcej informacji, zobacz [jak: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-make-a-clickonce-application-available-online-only"></a>Aby aplikacja ClickOnce była dostępna tylko w trybie online  
  
1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.  
  
2. Kliknij kartę **Publikowanie** .  
  
3. W obszarze **tryb instalacji i ustawienia** kliknij przycisk opcji **aplikacja jest dostępna tylko w trybie online** .  
  
### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Aby udostępnić aplikację ClickOnce w trybie online lub offline  
  
1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.  
  
2. Kliknij kartę **Publikowanie** .  
  
3. W obszarze **tryb instalacji i ustawienia** kliknij pozycję **aplikacja jest dostępna w trybie offline jako** przycisk opcji.  
  
     Po zainstalowaniu aplikacja dodaje wpisy do menu **Start** i **apletu Dodaj lub usuń programy** w panelu sterowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
