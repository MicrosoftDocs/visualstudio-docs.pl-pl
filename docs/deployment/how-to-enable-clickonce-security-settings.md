---
title: Włącz ustawienia zabezpieczeń ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5f407ac42dc9997215bfe6682bb8b974b78c7847
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "90850933"
---
# <a name="how-to-enable-clickonce-security-settings"></a>Instrukcje: Włączanie ustawień zabezpieczeń technologii ClickOnce
Aby można było opublikować aplikację, należy włączyć zabezpieczenia dostępu kodu dla aplikacji ClickOnce. Jest to wykonywane automatycznie podczas publikowania aplikacji przy użyciu Kreatora publikacji.

 W niektórych przypadkach włączenie zabezpieczeń dostępu kodu może mieć wpływ na wydajność podczas kompilowania lub debugowania aplikacji. w takich przypadkach można tymczasowo wyłączyć ustawienia zabezpieczeń.

 Ustawienia zabezpieczeń ClickOnce można włączać lub wyłączać na stronie **zabezpieczenia** **projektanta projektu**.

### <a name="to-enable-clickonce-security-settings"></a>Aby włączyć ustawienia zabezpieczeń ClickOnce

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **Zabezpieczenia**.

3. Zaznacz pole wyboru **Włącz ustawienia zabezpieczeń ClickOnce** .

     Teraz możesz dostosować ustawienia zabezpieczeń aplikacji na stronie Zabezpieczenia.

    > [!NOTE]
    > To pole wyboru jest wybierane automatycznie za każdym razem, gdy aplikacja jest publikowana przy użyciu kreatora **publikacji** .

### <a name="to-disable-clickonce-security-settings"></a>Aby wyłączyć ustawienia zabezpieczeń ClickOnce

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **Zabezpieczenia**.

3. Wyczyść pole wyboru **Włącz ustawienia zabezpieczeń ClickOnce** .

     Aplikacja zostanie uruchomiona z pełnymi ustawieniami zabezpieczeń zaufania; wszystkie ustawienia na stronie **zabezpieczenia** zostaną zignorowane.

    > [!NOTE]
    > Za każdym razem, gdy aplikacja jest publikowana przy użyciu Kreatora publikacji, to pole wyboru zostanie zaznaczone. należy wyczyścić ją ponownie po każdym pomyślnym opublikowaniu.

## <a name="see-also"></a>Zobacz także
- [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
- [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
