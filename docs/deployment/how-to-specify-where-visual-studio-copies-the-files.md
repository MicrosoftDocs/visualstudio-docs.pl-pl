---
title: Określ, gdzie mają zostać skopiowane pliki | Microsoft Docs
description: Dowiedz się, jak ustawić właściwość lokalizacja publikowania dla aplikacji ClickOnce, która określa lokalizację, w której są umieszczane pliki i manifest aplikacji.
ms.custom:
- SEO-VS-2020
- seodec18
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 50f3e5d8500e57dd336919a5da58af094db97169
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887422"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Instrukcje: Określanie, gdzie program Visual Studio ma kopiować pliki
W przypadku publikowania aplikacji przy użyciu technologii ClickOnce `Publish Location` Właściwość określa lokalizację, w której są umieszczane pliki i manifest aplikacji. Może to być ścieżka do pliku lub ścieżka do serwera FTP.

 Właściwość można określić `Publish Location` na stronie **Publikuj** **projektanta projektu** lub za pomocą Kreatora publikacji. Aby uzyskać więcej informacji, zobacz [jak: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!NOTE]
> W przypadku instalowania więcej niż jednej wersji aplikacji przy użyciu technologii ClickOnce instalacja przenosi wcześniejsze wersje aplikacji do folderu o nazwie archiwalne w określonej lokalizacji publikowania. Archiwizowanie wcześniejszych wersji w ten sposób powoduje, że katalog instalacyjny jest niezrozumiały dla folderów ze starszej wersji.

### <a name="to-specify-a-publishing-location"></a>Aby określić lokalizację publikowania

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **Publikowanie** .

3. W polu **Publikuj lokalizację** wprowadź lokalizację publikowania przy użyciu jednego z następujących formatów:

   - Aby opublikować w udziale plików lub w ścieżce dysku, wprowadź ścieżkę przy użyciu ścieżki UNC (*\\ \Server\ApplicationName*) lub ścieżki pliku (*C:\Deploy\ApplicationName*).

   - Aby opublikować na serwerze FTP, wprowadź ścieżkę przy użyciu formatu <em>FTP://FTP.Microsoft.com/ \<ApplicationName> </em>.

     Zwróć uwagę, że tekst musi być obecny w polu **Lokalizacja publikowania** , aby można było wykonać przycisk Przeglądaj (**...**).

## <a name="see-also"></a>Zobacz też
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)