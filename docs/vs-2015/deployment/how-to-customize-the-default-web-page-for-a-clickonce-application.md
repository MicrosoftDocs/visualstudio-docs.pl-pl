---
title: 'Instrukcje: Dostosowywanie domyślnej strony sieci Web dla aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish.htm Web page
- ClickOnce deployment default Web page
- deploying applications [ClickOnce], publishing
- publishing, ClickOnce
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
caps.latest.revision: 16
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 275d3d0547d83e794801c45a7554d58e181d64e7
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60107063"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Instrukcje: Dostosowywanie domyślnej strony internetowej dla aplikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas publikowania aplikacji ClickOnce w sieci Web, strony sieci Web jest automatycznie generowany i opublikowanych wraz z aplikacji. Domyślna strona zawiera nazwę aplikacji i linki do zainstalowania aplikacji, instalowanie wstępnie wymaganego oprogramowania lub dostępu do pomocy w witrynie MSDN.  
  
> [!NOTE]
>  Rzeczywiste łącza, widocznych na stronie zależy od komputera, na którym wyświetlania strony i wymagania wstępne są włącznie.  
  
 Domyślna nazwa strony sieci Web to Publish.htm; Możesz zmienić nazwę w **projektanta projektu**. Aby uzyskać więcej informacji, zobacz [jak: Określanie strony publikowania dla aplikacji ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).  
  
 Strona sieci Publish.htm Web została opublikowana, tylko wtedy, gdy Wykryto nowszą wersję.  
  
> [!NOTE]
>  Zmiany wprowadzone do usługi **Publikuj** ustawienia nie wpłynie na stronie Publish.htm z jednym wyjątkiem: Jeśli dodasz lub usuniesz wymagania wstępne po początkowym opublikowaniu, listę wymagań wstępnych nie będzie już dokładne. Należy edytować tekst łącza wymagań wstępnych odzwierciedlić zmiany.  
  
### <a name="to-customize-the-publish-web-page"></a>Aby dostosować strony sieci Web publikowania  
  
1. Publikowanie aplikacji ClickOnce do lokalizacji w sieci Web. Aby uzyskać więcej informacji, zobacz [jak: Publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
2. Na serwerze sieci Web otwórz plik Publish.htm w Visual Web Designer lub innego edytora HTML.  
  
3. Dostosowywanie strony zgodnie z potrzebami i zapisz go.  
  
4. Opcjonalna. Aby zapobiec zastąpieniu strony sieci Web publikowanie niestandardowych programu Visual Studio, usuń zaznaczenie pola wyboru **automatycznie Generuj stronę sieci web wdrożenia po każdej publikowania** w oknie dialogowym Opcje publikowania.  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Instrukcje: Instalowanie wymagań wstępnych przy użyciu aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Instrukcje: Określanie strony publikowania dla aplikacji ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)
