---
title: Jak włączyć funkcję Autostart dla instalacji z dysku CD | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, AutoStart
- ClickOnce deployment, installation on CD or DVD
- deploying applications [ClickOnce], installation on CD or DVD
ms.assetid: caaec619-900c-4790-90e3-8c91f5347635
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6ff96cdfe412e5016c04daa2b22922b0ec47a3a3
ms.sourcegitcommit: 3f491903e0c10db9a3f3fc0940f7b587fcbf9530
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85382448"
---
# <a name="how-to-enable-autostart-for-cd-installations"></a>Instrukcje: Włączanie autostartu dla instalacji z dysku CD
W przypadku wdrażania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji za pomocą nośników wymiennych, takich jak CD-ROM lub DVD-ROM, można włączyć `AutoStart` [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Automatyczne uruchamianie aplikacji po włożeniu nośnika.

 `AutoStart`można ją włączyć na stronie **Publikuj** **projektanta projektu**.

### <a name="to-enable-autostart"></a>Aby włączyć Autostart

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **Publikowanie** .

3. Kliknij przycisk **Opcje** .

     Zostanie wyświetlone okno dialogowe **Opcje publikowania** .

4. Kliknij pozycję **wdrażanie**.

5. Wybierz **instalacje dla dysków CD, automatycznie Rozpocznij instalację po wstawieniu dysku CD** .

     Plik *autorun. inf* zostanie skopiowany do lokalizacji publikowania po opublikowaniu aplikacji.

## <a name="see-also"></a>Zobacz też
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)