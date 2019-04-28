---
title: 'Instrukcje: Włączenie funkcji AutoStart dla instalacji z dysku CD | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66f5510ae63507aebb97a7f8bdfd3e367f1afc85
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62928506"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Instrukcje: Włączenie funkcji AutoStart dla instalacji z dysku CD
W przypadku wdrażania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji za pomocą nośników wymiennych, takich jak dysk CD-ROM lub DVD-ROM, aby umożliwić `AutoStart` tak, aby [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja jest uruchamiana automatycznie, gdy nośnik zostanie wstawiona.

 `AutoStart` można włączyć dla **Publikuj** strony **projektanta projektu**.

### <a name="to-enable-autostart"></a>Aby włączyć automatyczne uruchamianie

1. Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** kliknij menu **właściwości**.

2. Kliknij przycisk **Publikuj** kartę.

3. Kliknij przycisk **opcje** przycisku.

     **Opcji publikowania** pojawi się okno dialogowe.

4. Kliknij przycisk **wdrożenia**.

5. Wybierz **dla instalacji z dysku CD, automatycznie Rozpocznij instalację po włożeniu dysku CD** pole wyboru.

     *Autorun.inf* po opublikowaniu aplikacji plik zostanie skopiowany do lokalizacji publikowania.

## <a name="see-also"></a>Zobacz także
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Instrukcje: Publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)