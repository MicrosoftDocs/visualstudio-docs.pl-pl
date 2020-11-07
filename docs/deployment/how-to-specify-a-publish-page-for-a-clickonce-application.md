---
title: Określanie strony publikowania (Aplikacja ClickOnce)
description: Dowiedz się, jak ustawić właściwość publikowanie strony dla projektu, co pozwala na określenie strony sieci Web dla aplikacji ClickOnce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying publish page
- Publish Page property
- publishing, ClickOnce
- ClickOnce deployment, specifying publish page
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ecf70f5ffdd81688943892c06fdf98aae73d6c57
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350962"
---
# <a name="how-to-specify-a-publish-page-for-a-clickonce-application"></a>Instrukcje: Określanie strony publikowania dla aplikacji ClickOnce
Podczas publikowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji domyślna strona sieci Web (publish.htm) jest generowana i publikowana razem z aplikacją. Ta strona zawiera nazwę aplikacji, link do zainstalowania aplikacji i/lub wymagania wstępne oraz link do tematu pomocy opisującego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Właściwość **Publikowanie strony** dla projektu pozwala określić nazwę strony sieci Web [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.

 Po określeniu strony publikowania przy następnym opublikowaniu zostanie ona skopiowana do lokalizacji publikowania. po ponownym opublikowaniu nie zostanie on nadpisany. Jeśli chcesz dostosować wygląd strony, możesz to zrobić bez obaw o utracie zmian. Aby uzyskać więcej informacji, zobacz [How to: dostosowywanie domyślnej strony sieci Web ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).

 Właściwość **Publikuj stronę** można ustawić w oknie dialogowym **Opcje publikowania** dostępnym w okienku **Publikowanie** **projektanta projektu**.

### <a name="to-specify-a-custom-web-page-for-a-clickonce-application"></a>Aby określić niestandardową stronę sieci Web dla aplikacji ClickOnce

1. Po wybraniu projektu w **Eksplorator rozwiązań** , w menu **projekt** kliknij polecenie **Właściwości**.

2. Wybierz okienko **Publikowanie** .

3. Kliknij przycisk **Opcje** , aby otworzyć okno dialogowe **Opcje publikowania** .

4. Kliknij pozycję **wdrażanie**.

5. W oknie dialogowym **Opcje publikowania** upewnij się, że pole wyboru **Otwórz stronę sieci Web wdrożenia po publikacji** jest zaznaczone (powinno być wybrane domyślnie).

6. W polu **Strona sieci Web wdrożenia** wprowadź nazwę strony sieci Web, a następnie kliknij przycisk **OK**.

### <a name="to-prevent-the-publish-page-from-launching-each-time-you-publish"></a>Aby zapobiec uruchamianiu strony publikowania przy każdym publikowaniu

1. Po wybraniu projektu w **Eksplorator rozwiązań** , w menu **projekt** kliknij polecenie **Właściwości**.

2. Wybierz okienko **Publikowanie** .

3. Kliknij przycisk **Opcje** , aby otworzyć okno dialogowe **Opcje publikowania** .

4. Kliknij pozycję **wdrażanie**.

5. W oknie dialogowym **Opcje publikowania** wyczyść pole wyboru **Otwórz stronę sieci Web wdrożenia po publikacji** .

## <a name="see-also"></a>Zobacz też
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Instrukcje: dostosowywanie domyślnej strony sieci Web ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)