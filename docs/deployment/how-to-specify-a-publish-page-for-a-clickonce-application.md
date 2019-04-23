---
title: 'Instrukcje: Określanie strony publikowania dla aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29d83dd1a232ae1cf0437c1ab6d4662acef2900d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60048637"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Instrukcje: Określanie strony publikowania dla aplikacji ClickOnce
Podczas publikowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji domyślnej strony sieci Web (publish.htm) jest wygenerowany i opublikowanych wraz z aplikacji. Ta strona zawiera nazwę aplikacji, link do instalacji aplikacji i/lub wszystkie wstępnie wymagane składniki oraz łącza do tematów Pomocy zawierająca opis [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. **Opublikuj stronę** właściwość dla projektu pozwala określić nazwę dla strony sieci Web dla usługi [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.

 Po stronie publikowania została określona, podczas następnego publikowania, zostanie on skopiowany do lokalizacji publikowania; nie zostaną zastąpione, jeśli w przypadku ponownego publikowania. Jeśli chcesz dostosować wygląd strony, możesz to zrobić bez konieczności martwienia się o utratę danych. Aby uzyskać więcej informacji, zobacz [jak: Dostosowywanie domyślnej strony sieci Web technologii ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).

 **Opublikuj stronę** właściwość można ustawić **opcji publikowania** okno dialogowe, dostępna z **Publikuj** okienku **projektanta projektu**.

### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>Aby określić niestandardowe strony sieci Web dla aplikacji ClickOnce

1. Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** kliknij menu **właściwości**.

2. Wybierz **Publikuj** okienka.

3. Kliknij przycisk **opcje** przycisk, aby otworzyć **opcji publikowania** okno dialogowe.

4. Kliknij przycisk **wdrożenia**.

5. W **opcji publikowania** okna dialogowego pole, upewnij się, że **opublikować stronę sieci web Otwórz wdrożenia po** pole wyboru jest zaznaczone (powinna ona zostać wybrana domyślnie).

6. W **stronę sieci web wdrożenia** , wprowadź nazwę dla strony sieci Web, a następnie kliknij **OK**.

### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Aby uniemożliwić uruchamianie każdorazowo, gdy opublikujesz strony publikowania

1. Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** kliknij menu **właściwości**.

2. Wybierz **Publikuj** okienka.

3. Kliknij przycisk **opcje** przycisk, aby otworzyć **opcji publikowania** okno dialogowe.

4. Kliknij przycisk **wdrożenia**.

5. W **opcji publikowania** okno dialogowe wyczyść **opublikować stronę sieci web Otwórz wdrożenia po** pole wyboru.

## <a name="see-also"></a>Zobacz także
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Instrukcje: Publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Instrukcje: Dostosowywanie domyślnej strony sieci Web technologii ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)