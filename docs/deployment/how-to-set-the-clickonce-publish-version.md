---
title: Ustaw wersję publikacji ClickOnce | Microsoft Docs
description: Informacje dotyczące ustawiania właściwości wersji publikacji ClickOnce, która określa, czy aplikacja jest aktualizacją.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, setting publish version
- publishing, ClickOnce
- Publish Version property
ms.assetid: 06f15504-6385-40a6-b01d-cd90ca36dc73
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 71d74d8b16e058b150187a231a1f3a7323c0c612
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885030"
---
# <a name="how-to-set-the-clickonce-publish-version"></a>Instrukcje: Ustawianie wersji publikacji ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] `Publish Version` Właściwość określa, czy publikowana aplikacja będzie traktowana jako aktualizacja. Za każdym razem, gdy wersja jest zwiększana, aplikacja zostanie opublikowana jako aktualizacja.

 `Publish Version`Właściwość można ustawić na stronie **Publikuj** **projektanta projektu**.

> [!NOTE]
> Istnieje opcja projektu, która automatycznie zwiększa `Publish Version` Właściwość za każdym razem, gdy aplikacja zostanie opublikowana. Ta opcja jest domyślnie włączona. Aby uzyskać więcej informacji, zobacz [jak: automatyczne zwiększanie wersji publikacji ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md).

### <a name="to-change-the-publish-version"></a>Aby zmienić wersję publikacji

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **Publikowanie** .

3. W polu **Publikowanie wersji** Zwiększ liczbę wersji **głównej**, **pomocniczej**, **kompilacji** lub **poprawki** .

    > [!NOTE]
    > Nie należy nigdy zmniejszać numeru wersji; wykonanie tej operacji może spowodować nieprzewidywalne zachowanie aktualizacji.

## <a name="see-also"></a>Zobacz też
- [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Instrukcje: automatyczne zwiększanie wersji publikacji ClickOnce](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)