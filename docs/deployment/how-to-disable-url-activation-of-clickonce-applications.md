---
title: 'Instrukcje: Wyłączanie aktywacji adresu URL aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowUrlActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6841b8a91cec24f467f6e3f684cbb27e25c9fa63
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045619"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Instrukcje: Wyłączanie aktywacji adresu URL aplikacji ClickOnce

Zazwyczaj [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji zostanie automatycznie uruchomiony natychmiast, po zakończeniu instalacji z serwera sieci Web. Ze względów bezpieczeństwa może zdecydować wyłączyć to zachowanie i poinformuj użytkowników, aby uruchomić aplikację z **Start** menu zamiast tego. Poniższa procedura opisuje sposób wyłączanie aktywacji adresu URL.

Ta technika może zostać użyta tylko w przypadku [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji zainstalowanych na komputerze użytkownika z serwera sieci Web. Nie można używać dla aplikacji tylko w trybie online, które można uruchamiać tylko przy użyciu swojego adresu URL. Aby uzyskać więcej informacji na temat różnią się tylko w trybie online i zainstalowanych aplikacji, zobacz [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

Ta procedura korzysta z narzędzia Windows Software Development Kit (SDK) MageUI.exe. Aby uzyskać więcej informacji na temat tego narzędzia, zobacz [MageUI.exe (Manifest Generation i graficzny klient Editing Tool)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Można również wykonać tę procedurę przy użyciu programu Visual Studio.

## <a name="procedure"></a>Procedura

### <a name="to-disable-url-activation-for-your-application"></a>Aby wyłączanie aktywacji adresu URL aplikacji

1. Otwórz manifest wdrożenia w MageUI.exe. Jeśli użytkownik jeszcze nie utworzono jedną, wykonaj kroki opisane w [instruktażu: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

2. Wybierz **opcje wdrażania** kartę.

3. Wyczyść **automatycznie uruchomić aplikacji po zainstalowaniu** pole wyboru.

4. Zapisz i podpisać manifest.

## <a name="see-also"></a>Zobacz także

- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)