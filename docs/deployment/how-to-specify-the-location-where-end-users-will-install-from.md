---
title: 'Instrukcje: Określanie lokalizacji, z której użytkownicy końcowi będą instalować | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], specifying an installation URL
- URLs, specifying an installation URL
- installation, specifying installation an URL
- Installation URL property
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 993c654ccd16f2d51d86a46a716edd611ae154dd
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557612"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Instrukcje: Określanie lokalizacji, z której użytkownicy końcowi będą instalować
Podczas publikowania aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], lokalizacja, w której użytkownicy przechodzą do pobierania i instalowania aplikacji, nie musi być lokalizacją, w której początkowo opublikowano aplikację. Na przykład w niektórych organizacjach deweloper może opublikować aplikację na serwerze przejściowym, a następnie administrator przeniesie aplikację na serwer sieci Web.

W takim przypadku można użyć właściwości `Installation URL`, aby określić serwer sieci Web, na którym użytkownicy będą przechodzili w celu pobrania aplikacji. Jest to konieczne, aby manifest aplikacji wiedział, gdzie szukać aktualizacji.

Właściwość `Installation URL` można ustawić na stronie **Publikuj** **projektanta projektu**.

> [!NOTE]
> Właściwość `Installation URL` można również ustawić za pomocą **PublishWizard**. Aby uzyskać więcej informacji, zobacz [jak: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-specify-an-installation-url"></a>Aby określić adres URL instalacji

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **Publikowanie** .

3. W polu adres URL instalacji wprowadź lokalizację instalacji przy użyciu w pełni kwalifikowanego adresu URL przy użyciu formatu `https://www.contoso.com/ApplicationName`lub ścieżki UNC przy użyciu formatu `\Server\ApplicationName`.

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Określanie, gdzie program Visual Studio ma kopiować pliki](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)