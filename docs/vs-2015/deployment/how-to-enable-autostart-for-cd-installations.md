---
title: 'Instrukcje: Włączenie funkcji AutoStart dla instalacji z dysku CD | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061103"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Instrukcje: Włączanie funkcji AutoStart dla instalacji z dysku CD
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W przypadku wdrażania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji za pomocą nośników wymiennych, takich jak dysk CD-ROM lub DVD-ROM, aby umożliwić `AutoStart` tak, aby [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacja jest uruchamiana automatycznie, gdy nośnik zostanie wstawiona.  
  
 `AutoStart` można włączyć dla **Publikuj** strony **projektanta projektu**.  
  
### <a name="to-enable-autostart"></a>Aby włączyć automatyczne uruchamianie  
  
1. Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** kliknij menu **właściwości**.  
  
2. Kliknij przycisk **Publikuj** kartę.  
  
3. Kliknij przycisk **opcje** przycisku.  
  
     **Opcji publikowania** pojawi się okno dialogowe.  
  
4. Kliknij przycisk **wdrożenia**.  
  
5. Wybierz **dla instalacji z dysku CD, automatycznie Rozpocznij instalację po włożeniu dysku CD** pole wyboru.  
  
     Plik Autorun.inf zostaną skopiowane do lokalizacji publikowania, gdy aplikacja została opublikowana.  
  
## <a name="see-also"></a>Zobacz też  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Instrukcje: Publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
