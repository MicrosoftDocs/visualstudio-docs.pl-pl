---
title: 'Instrukcje: Określ lokalizację, w której użytkownicy końcowi będą przeprowadzać instalacje | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying an installation URL
- URLs, specifying an installation URL
- installation, specifying installation an URL
- Installation URL property
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3139cb337428dfc0c14e5bae47e682ce169bc81d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60108506"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Instrukcje: Określanie lokalizacji, z której użytkownicy końcowi będą przeprowadzać instalacje
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas publikowania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji, lokalizację, do którego użytkownicy używają do pobrania i zainstalowania aplikacji nie jest koniecznie lokalizacji, w którym początkowo opublikować aplikację. Na przykład w niektórych organizacjach deweloper może publikować aplikacje na serwerze tymczasowym, a następnie administrator może przenieść aplikację na serwerze sieci Web.  
  
 W takim przypadku można użyć `Installation URL` właściwości w celu określenia serwera sieci Web, gdzie użytkownicy pobierać aplikację. Jest to konieczne, tak aby wie, gdzie szukać aktualizacji manifestu aplikacji.  
  
 `Installation URL` Właściwość można ustawić na **Publikuj** strony **projektanta projektu**.  
  
 **Uwaga** `Installation URL` właściwości można również ustawić za pomocą **PublishWizard**. Aby uzyskać więcej informacji, zobacz [jak: Publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-specify-an-installation-url"></a>Aby określić adres URL instalacji  
  
1. Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2. Kliknij przycisk **Publikuj** kartę.  
  
3. W polu adres URL instalacji wprowadź lokalizację instalacji przy użyciu w pełni kwalifikowany adres URL w formacie http://www.microsoft.com/ApplicationName, lub ścieżkę UNC w formacie \\\Server\ApplicationName.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Określanie lokalizacji kopiowania plików w programie Visual Studio](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Instrukcje: Publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
