---
title: 'Instrukcje: Włączanie autostartu dla instalacji z dysku CD | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c4bd14060517793d28e24818a051df63efb8f0e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153787"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Porady: włączenie funkcji AutoStart dla instalacji z dysku CD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W przypadku wdrażania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji za pomocą nośników wymiennych, takich jak CD-ROM lub DVD-ROM, można włączyć `AutoStart` [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Automatyczne uruchamianie aplikacji po włożeniu nośnika.  
  
 `AutoStart` można ją włączyć na stronie **Publikuj** **projektanta projektu**.  
  
### <a name="to-enable-autostart"></a>Aby włączyć Autostart  
  
1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.  
  
2. Kliknij kartę **Publikowanie** .  
  
3. Kliknij przycisk **Opcje** .  
  
     Zostanie wyświetlone okno dialogowe **Opcje publikowania** .  
  
4. Kliknij pozycję **wdrażanie**.  
  
5. Wybierz **instalacje dla dysków CD, automatycznie Rozpocznij instalację po wstawieniu dysku CD** .  
  
     Plik autorun. inf zostanie skopiowany do lokalizacji publikowania po opublikowaniu aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
