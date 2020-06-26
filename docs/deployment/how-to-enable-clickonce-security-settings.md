---
title: Jak włączyć ustawienia zabezpieczeń ClickOnce | Microsoft Docs
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
ms.openlocfilehash: d673edac957e9625f7d948fbe766ee08b23b6b52
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382435"
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

## <a name="see-also"></a>Zobacz też
- [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
- [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
