---
title: 'Instrukcje: Określanie strony publikowania dla aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying publish page
- Publish Page property
- publishing, ClickOnce
- ClickOnce deployment, specifying publish page
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 63356c6eb423ddead54290cc11c865a5102f55f2
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60098470"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Instrukcje: Określanie strony publikowania dla aplikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas publikowania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji domyślnej strony sieci Web (publish.htm) jest wygenerowany i opublikowanych wraz z aplikacji. Ta strona zawiera nazwę aplikacji, link do instalacji aplikacji i/lub wszystkie wstępnie wymagane składniki oraz łącza do tematów Pomocy zawierająca opis [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]. **Opublikuj stronę** właściwość dla projektu pozwala określić nazwę dla strony sieci Web dla usługi [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji.  
  
 Po stronie publikowania została określona, podczas następnego publikowania, zostanie on skopiowany do lokalizacji publikowania; nie zostaną zastąpione, jeśli w przypadku ponownego publikowania. Jeśli chcesz dostosować wygląd strony, możesz to zrobić bez konieczności martwienia się o utratę danych. Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie ClickOnce domyślnej strony sieci Web](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).  
  
 **Opublikuj stronę** właściwość można ustawić **opcji publikowania** okno dialogowe, dostępna z **Publikuj** okienku **projektanta projektu**.  
  
### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>Aby określić niestandardowe strony sieci Web dla aplikacji ClickOnce  
  
1. Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** kliknij menu **właściwości**.  
  
2. Wybierz **Publikuj** okienka.  
  
3. Kliknij przycisk **opcje** przycisk, aby otworzyć **opcji publikowania** okno dialogowe.  
  
4. Kliknij przycisk **wdrożenia**.  
  
5. W **opcji publikowania** okna dialogowego pole, upewnij się, że **opublikować stronę sieci web Otwórz wdrożenia po** pole wyboru jest zaznaczone (powinna ona zostać wybrana domyślnie).  
  
6. W **stronę sieci web wdrożenia:** , wprowadź nazwę dla strony sieci Web, a następnie kliknij **OK**.  
  
### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Aby uniemożliwić uruchamianie każdorazowo, gdy opublikujesz strony publikowania  
  
1. Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** kliknij menu **właściwości**.  
  
2. Wybierz **Publikuj** okienka.  
  
3. Kliknij przycisk **opcje** przycisk, aby otworzyć **opcji publikowania** okno dialogowe.  
  
4. Kliknij przycisk **wdrożenia**.  
  
5. W **opcji publikowania** okno dialogowe wyczyść **opublikować stronę sieci web Otwórz wdrożenia po** pole wyboru.  
  
## <a name="see-also"></a>Zobacz też  
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Instrukcje: Publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Instrukcje: Dostosowywanie domyślnej strony internetowej technologii ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)
