---
title: 'Instrukcje: Dostosowywanie domyślnej strony sieci Web dla aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 324066d1f6bd6ad1719b2dc960de2b2357ec8cbd
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976384"
---
# <a name="how-to-customize-the-default-web-page-for-a-clickonce-application"></a>Instrukcje: Dostosowywanie domyślnej strony sieci Web dla aplikacji ClickOnce
Podczas publikowania aplikacji ClickOnce w sieci Web, strony sieci Web jest automatycznie generowany i opublikowanych wraz z aplikacji. Domyślna strona zawiera nazwę aplikacji i linki do zainstalowania aplikacji, instalowanie wstępnie wymaganego oprogramowania lub dostępu do pomocy w witrynie MSDN.  
  
> [!NOTE]
>  Rzeczywiste łącza, widocznych na stronie zależy od komputera, na którym wyświetlania strony i wymagania wstępne są włącznie.  
  
 Nazwa domyślnej strony sieci Web jest *Publish.htm*; możesz zmienić nazwę w **projektanta projektu**. Aby uzyskać więcej informacji, zobacz [jak: Określanie strony publikowania dla aplikacji ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).  
  
 *Publish.htm* strony sieci Web jest publikowany, tylko wtedy, gdy Wykryto nowszą wersję.  
  
> [!NOTE]
>  Zmiany wprowadzone do usługi **publikowania** nie wpłynie na ustawienia *Publish.htm* strony z jednym wyjątkiem: Jeśli dodasz lub usuniesz wymagania wstępne po początkowym opublikowaniu, będzie listę wymagań wstępnych już nie być dokładna. Należy edytować tekst łącza wymagań wstępnych odzwierciedlić zmiany.  
  
### <a name="to-customize-the-publish-web-page"></a>Aby dostosować strony sieci Web publikowania  
  
1.  Publikowanie aplikacji ClickOnce do lokalizacji w sieci Web. Aby uzyskać więcej informacji, zobacz [jak: Publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
2.  Na serwerze sieci Web otwórz *Publish.htm* pliku w Visual Web Designer lub innego edytora HTML.  
  
3.  Dostosowywanie strony zgodnie z potrzebami i zapisz go.  
  
4.  Opcjonalna. Aby zapobiec zastąpieniu strony sieci Web publikowanie niestandardowych programu Visual Studio, usuń zaznaczenie pola wyboru **automatycznie Generuj stronę sieci Web wdrożenia po każdej publikowania** w **opcji publikowania** okno dialogowe.  
  
## <a name="see-also"></a>Zobacz także  
 [Wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Instrukcje: Instalowanie wymagań wstępnych przy użyciu aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Instrukcje: Określanie strony publikowania dla aplikacji ClickOnce](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)