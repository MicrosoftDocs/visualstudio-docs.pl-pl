---
title: 'Instrukcje: Zmiana języka publikacji dla aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Publish language property
- ClickOnce deployment, changing publish language
- publishing, ClickOnce
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7e5bf51fd416fd9ccbb2343c17412984858429da
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60115292"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Instrukcje: Zmienianie języka publikacji dla aplikacji ClickOnce

Podczas publikowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji interfejsu użytkownika wyświetlany podczas domyślne ustawienia instalacji języka i kultury komputer deweloperski. W przypadku publikowania zlokalizowanych aplikacji, należy określić języka i kultury, aby dopasować zlokalizowanej wersji. Jest to określane przez `Publish language` właściwość dla projektu.

`Publish language` Właściwość można ustawić **opcji publikowania** okno dialogowe, dostępna z **Publikuj** strony **projektanta projektu**.

> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [zresetować ustawienia](../ide/environment-settings.md#reset-settings).

## <a name="to-change-the-publish-language"></a>Aby zmienić język publikacji

1. Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.

2. Kliknij przycisk **Publikuj** kartę.

3. Kliknij przycisk **opcje** przycisk, aby otworzyć **opcji publikowania** okno dialogowe.

4. Kliknij przycisk **opis**.

5. W **opcji publikowania** okna dialogowego pole, wybierz język i kultury z **języka publikacji** listy rozwijanej, a następnie kliknij **OK**.

## <a name="see-also"></a>Zobacz także

- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Instrukcje: Publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)