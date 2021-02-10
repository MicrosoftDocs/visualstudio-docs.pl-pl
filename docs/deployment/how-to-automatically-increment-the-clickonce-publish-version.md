---
title: Autozwiększ wersję publikacji ClickOnce
description: Dowiedz się, jak wyłączyć automatyczne zwiększanie numeru poprawki dla aplikacji ClickOnce przy użyciu programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b84b0a8932bb9d8fd4738c2cd4924b61bb6faeb7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99947778"
---
# <a name="how-to-automatically-increment-the-clickonce-publish-version"></a>Instrukcje: automatyczne zwiększanie wersji publikacji ClickOnce

W przypadku publikowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji zmiana `Publish Version` właściwości powoduje opublikowanie aplikacji jako aktualizacji. Domyślnie program Visual Studio automatycznie zwiększa `Revision` liczbę przy `Publish Version` każdej publikacji aplikacji.

To zachowanie można wyłączyć na stronie **Publikowanie** **projektanta projektu**.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Resetowanie ustawień](../ide/environment-settings.md#reset-settings).

## <a name="to-disable-automatically-incrementing-the-publish-version"></a>Aby wyłączyć automatyczne zwiększanie wersji publikacji

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **Publikowanie** .

3. W sekcji **Publikowanie wersji** wyczyść pole wyboru **automatycznie Zwiększ numer poprawki przy każdej wersji** .

## <a name="see-also"></a>Zobacz też

- [Instrukcje: Ustawianie wersji publikacji ClickOnce](../deployment/how-to-set-the-clickonce-publish-version.md)
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)