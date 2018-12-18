---
title: 'Porady: automatyczne zwiększenie ClickOnce wersji publikacji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], incrementing publish version automatically
- Publish Version property, incrementing
- ClickOnce deployment, incrementing publish version automatically
- publishing, ClickOnce
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b7dd1723d9d92d9bc1b667cc3fddbc3ea297d8b8
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389127"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Porady: automatyczne zwiększenie ClickOnce wersji publikacji

Podczas publikowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikację, zmieniając `Publish Version` właściwości powoduje, że aplikacja opublikowana jako aktualizację. Domyślnie, Visual Studio automatycznie zwiększa `Revision` liczby `Publish Version` każdorazowo, możesz opublikować aplikację.

To zachowanie można wyłączyć na **Publikuj** strony **projektanta projektu**.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [zresetować ustawienia](../ide/environment-settings.md#reset-settings).

## <a name="to-disable-automatically-incrementing-the-publish-version"></a>Aby wyłączyć automatyczne zwiększenie wersji publikacji

1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.

2.  Kliknij przycisk **Publikuj** kartę.

3.  W **opublikować wersję** sekcji wyczyść **automatycznie zwiększ numer poprawki przy każdym wydaniu** pole wyboru.

## <a name="see-also"></a>Zobacz także

- [Porady: ustawienie ClickOnce wersji publikacji](../deployment/how-to-set-the-clickonce-publish-version.md)
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)