---
title: 'Instrukcje: Określanie lokalizacji, z której użytkownicy końcowi będą instalować | Microsoft Docs'
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
ms.openlocfilehash: 82181d906adc3454dfe77ef4fb21d8bdf99df16f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77557985"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Porady: określanie lokalizacji, z której użytkownicy końcowi będą przeprowadzać instalacje
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas publikowania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji, lokalizacja, w której użytkownicy przechodzą do pobierania i instalowania aplikacji, nie musi być lokalizacją, w której początkowo aplikacja została opublikowana. Na przykład w niektórych organizacjach deweloper może opublikować aplikację na serwerze przejściowym, a następnie administrator przeniesie aplikację na serwer sieci Web.  
  
 W takim przypadku można użyć `Installation URL` właściwości, aby określić serwer sieci Web, na którym użytkownicy będą przechodzili w celu pobrania aplikacji. Jest to konieczne, aby manifest aplikacji wiedział, gdzie szukać aktualizacji.  
  
 `Installation URL`Właściwość można ustawić na stronie **Publikuj** **projektanta projektu**.  
  
 **Uwaga** `Installation URL` Właściwość można również ustawić za pomocą **PublishWizard**. Aby uzyskać więcej informacji, zobacz [jak: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
### <a name="to-specify-an-installation-url"></a>Aby określić adres URL instalacji  
  
1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.  
  
2. Kliknij kartę **Publikowanie** .  
  
3. W polu adres URL instalacji wprowadź lokalizację instalacji przy użyciu w pełni kwalifikowanego adresu URL przy użyciu formatu `https://www.contoso.com/ApplicationName` lub ścieżki UNC przy użyciu formatu `\\Server\ApplicationName` .  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: Określanie, gdzie program Visual Studio ma kopiować pliki](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
