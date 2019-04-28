---
title: 'Instrukcje: Automatyczne ClickOnce zwiększenie wersji publikacji | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cce9dfe48e34d642b115c8391de73c0350ce515b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62928496"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Instrukcje: Automatyczne ClickOnce zwiększenie wersji publikacji

Podczas publikowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikację, zmieniając `Publish Version` właściwości powoduje, że aplikacja opublikowana jako aktualizację. Domyślnie, Visual Studio automatycznie zwiększa `Revision` liczby `Publish Version` każdorazowo, możesz opublikować aplikację.

To zachowanie można wyłączyć na **Publikuj** strony **projektanta projektu**.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [zresetować ustawienia](../ide/environment-settings.md#reset-settings).

## <a name="to-disable-automatically-incrementing-the-publish-version"></a>Aby wyłączyć automatyczne zwiększenie wersji publikacji

1. Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.

2. Kliknij przycisk **Publikuj** kartę.

3. W **opublikować wersję** sekcji wyczyść **automatycznie zwiększ numer poprawki przy każdym wydaniu** pole wyboru.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: ClickOnce ustawienie wersji publikacji](../deployment/how-to-set-the-clickonce-publish-version.md)
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Instrukcje: Publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)