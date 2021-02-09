---
title: Określ tryb instalacji w trybie offline lub online (ClickOnce)
description: Dowiedz się, jak określić tryb instalacji dla aplikacji ClickOnce, która określa, czy aplikacja jest dostępna w trybie offline, czy w trybie online.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, specifying install mode
- install mode
- online applications
- offline applications
- ClickOnce install mode
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 918cb7e60f4e3fed2beee024d51b94499b14b632
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900428"
---
# <a name="how-to-specify-the-clickonce-offline-or-online-install-mode"></a>Instrukcje: Określanie trybu instalacji ClickOnce w trybie offline lub online
`Install Mode`Dla [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji określa, czy aplikacja będzie dostępna w trybie offline, czy w trybie online. Po wybraniu **aplikacji jest dostępna tylko w trybie online**, użytkownik musi mieć dostęp do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] lokalizacji publikowania (strona sieci Web lub udział plików) w celu uruchomienia aplikacji. Po wybraniu **aplikacji jest również dostępna w trybie offline** aplikacja dodaje wpisy do menu **Start** i okno dialogowe **Dodawanie lub usuwanie programów** ; Użytkownik może uruchomić aplikację, gdy nie są połączeni.

`Install Mode`Można ją ustawić na stronie **Publikuj** **projektanta projektu**.

> [!NOTE]
> `Install Mode`Można również ustawić za pomocą Kreatora publikacji. Aby uzyskać więcej informacji, zobacz [jak: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-make-a-clickonce-application-available-online-only"></a>Aby aplikacja ClickOnce była dostępna tylko w trybie online

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **Publikowanie** .

3. W obszarze **tryb instalacji i ustawienia** kliknij przycisk opcji **aplikacja jest dostępna tylko w trybie online** .

### <a name="to-make-a-clickonce-application-available-online-or-offline"></a>Aby udostępnić aplikację ClickOnce w trybie online lub offline

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **Publikowanie** .

3. W obszarze **tryb instalacji i ustawienia** kliknij pozycję **aplikacja jest dostępna w trybie offline jako** przycisk opcji.

     Po zainstalowaniu aplikacja dodaje wpisy do menu **Start** i **apletu Dodaj lub usuń programy** w panelu sterowania.

## <a name="see-also"></a>Zobacz też
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Wybieranie strategii wdrażania technologii ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)