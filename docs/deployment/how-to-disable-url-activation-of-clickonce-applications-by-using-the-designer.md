---
title: 'Instrukcje: Wyłączanie aktywacji adresu URL aplikacji ClickOnce za pomocą projektanta | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4da1ba726253891ef7df2ccfde8a667ac11ad8d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62928585"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Instrukcje: Wyłączanie aktywacji adresu URL aplikacji ClickOnce przy użyciu narzędzia Projektant
Zazwyczaj [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji rozpocznie się automatycznie natychmiast, po zakończeniu instalacji z serwera sieci Web. Ze względów bezpieczeństwa może zdecydować wyłączyć to zachowanie i poinformuj użytkowników, aby uruchomić aplikację z **Start** menu zamiast tego. Poniższa procedura opisuje sposób wyłączanie aktywacji adresu URL.

 Ta technika może zostać użyta tylko w przypadku [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji zainstalowanych na komputerze użytkownika z serwera sieci Web. Nie można używać dla aplikacji tylko w trybie online, które można uruchomić tylko przy użyciu swojego adresu URL. Aby uzyskać więcej informacji na temat różnic między tylko w trybie online i zainstalowanych aplikacji, zobacz [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

 Ta procedura wykorzystuje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. To zadanie można również wykonać przy użyciu [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Aby uzyskać więcej informacji, zobacz [jak: Wyłączanie aktywacji adresu URL aplikacji ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).

## <a name="procedure"></a>Procedura

#### <a name="to-disable-url-activation-for-your-application"></a>Aby wyłączanie aktywacji adresu URL aplikacji

1. Kliknij prawym przyciskiem myszy nazwę projektu w **Eksploratora rozwiązań**i kliknij przycisk **właściwości**.

2. Na **właściwości** kliknij **Publikuj** kartę.

3. Kliknij przycisk **opcje**.

4. Kliknij przycisk **manifesty**.

5. Zaznacz pole wyboru przy opcji **Block aktywowania aplikacji za pomocą adresu URL**.

6. Wdrażanie aplikacji.

## <a name="see-also"></a>Zobacz także
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)