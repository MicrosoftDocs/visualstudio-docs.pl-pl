---
title: 'Porady: zmiana języka publikacji dla aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4567ab9b72ccf827f8fad0bd35654210a4457ad4
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388351"
---
# <a name="how-to-change-the-publish-language-for-a-clickonce-application"></a>Porady: Zmienianie języka publikacji dla aplikacji ClickOnce

Podczas publikowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji interfejsu użytkownika wyświetlany podczas domyślne ustawienia instalacji języka i kultury komputer deweloperski. W przypadku publikowania zlokalizowanych aplikacji, należy określić języka i kultury, aby dopasować zlokalizowanej wersji. Jest to określane przez `Publish language` właściwość dla projektu.

`Publish language` Właściwość można ustawić **opcji publikowania** okno dialogowe, dostępna z **Publikuj** strony **projektanta projektu**.

> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [zresetować ustawienia](../ide/environment-settings.md#reset-settings).

## <a name="to-change-the-publish-language"></a>Aby zmienić język publikacji

1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.

2.  Kliknij przycisk **Publikuj** kartę.

3.  Kliknij przycisk **opcje** przycisk, aby otworzyć **opcji publikowania** okno dialogowe.

4.  Kliknij przycisk **opis**.

5.  W **opcji publikowania** okna dialogowego pole, wybierz język i kultury z **języka publikacji** listy rozwijanej, a następnie kliknij **OK**.

## <a name="see-also"></a>Zobacz także

- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)