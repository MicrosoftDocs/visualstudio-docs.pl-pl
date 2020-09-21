---
title: Określ lokalizację, z której użytkownicy końcowi instalują
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 1ba02b1cf8947fa2d1907d6316e36af8f8f54a77
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808727"
---
# <a name="how-to-specify-the-location-where-end-users-will-install-from"></a>Instrukcje: Określanie lokalizacji, z której użytkownicy końcowi będą instalować

Podczas publikowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, lokalizacja, w której użytkownicy przechodzą do pobierania i instalowania aplikacji, nie musi być lokalizacją, w której początkowo aplikacja została opublikowana. Na przykład w niektórych organizacjach deweloper może opublikować aplikację na serwerze przejściowym, a następnie administrator przeniesie aplikację na serwer sieci Web.

W takim przypadku można użyć `Installation URL` właściwości, aby określić serwer sieci Web, na którym użytkownicy będą przechodzili w celu pobrania aplikacji. Jest to konieczne, aby manifest aplikacji wiedział, gdzie szukać aktualizacji.

`Installation URL`Właściwość można ustawić na stronie **Publikuj** **projektanta projektu**.

> [!NOTE]
> `Installation URL`Właściwość można również ustawić za pomocą **PublishWizard**. Aby uzyskać więcej informacji, zobacz [jak: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

### <a name="to-specify-an-installation-url"></a>Aby określić adres URL instalacji

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **Publikowanie** .

3. W polu adres URL instalacji wprowadź lokalizację instalacji przy użyciu w pełni kwalifikowanego adresu URL przy użyciu formatu `https://www.contoso.com/ApplicationName` lub ścieżki UNC przy użyciu formatu `\Server\ApplicationName` .

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Określanie, gdzie program Visual Studio ma kopiować pliki](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)