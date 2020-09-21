---
title: Wyłączanie aktywacji adresu URL aplikacji ClickOnce
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: f13921044e188d659ba8cd5b776a006f7af5b1a6
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90809764"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications"></a>Instrukcje: wyłączanie aktywacji adresu URL aplikacji ClickOnce

Zazwyczaj [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacja zostanie uruchomiona automatycznie po zainstalowaniu z serwera sieci Web. Ze względów bezpieczeństwa może być konieczne wyłączenie tego zachowania i poinformowanie użytkowników, aby uruchomili aplikację z menu **Start** . Poniższa procedura opisuje sposób wyłączania aktywacji adresu URL.

Tej techniki można używać tylko w przypadku [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji zainstalowanych na komputerze użytkownika z serwera sieci Web. Nie może być używany tylko w przypadku aplikacji online, które można uruchomić tylko przy użyciu adresu URL. Aby uzyskać więcej informacji na temat różnic między aplikacjami tylko online i zainstalowanymi, zobacz [Wybieranie strategii wdrażania ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

Ta procedura powoduje użycie narzędzia Windows Software Development Kit (SDK) MageUI.exe. Aby uzyskać więcej informacji na temat tego narzędzia, zobacz [MageUI.exe (narzędzie tworzenia i edycji manifestów, klient graficzny)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client). Tę procedurę można również wykonać przy użyciu programu Visual Studio.

## <a name="procedure"></a>Procedura

### <a name="to-disable-url-activation-for-your-application"></a>Aby wyłączyć aktywację adresów URL dla aplikacji

1. Otwórz manifest wdrożenia w MageUI.exe. Jeśli jeszcze nie utworzono, wykonaj kroki opisane w [przewodniku: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).

2. Wybierz kartę **Opcje wdrażania** .

3. Wyczyść pole wyboru **automatycznie uruchamiaj aplikację po zainstalowaniu** .

4. Zapisz i podpisz manifest.

## <a name="see-also"></a>Zobacz też

- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)