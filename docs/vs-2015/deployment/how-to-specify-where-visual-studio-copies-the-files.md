---
title: 'Instrukcje: Określanie, gdzie program Visual Studio 2015 kopiuje pliki | Microsoft Docs'
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- publishing, specifying location
- Publish Location property
ms.assetid: 6c552700-dda3-49fe-af98-4717344fda07
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8759145dd4a7647cad6e9964ae1f1c97d333b626
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65226163"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Porady: określanie lokalizacji kopiowania plików przez program Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W przypadku publikowania aplikacji przy użyciu technologii ClickOnce `Publish Location` Właściwość określa lokalizację, w której są umieszczane pliki i manifest aplikacji. Może to być ścieżka do pliku lub ścieżka do serwera FTP.

 Właściwość można określić `Publish Location` na stronie **Publikuj** **projektanta projektu**lub za pomocą Kreatora publikacji. Aby uzyskać więcej informacji, zobacz [jak: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!NOTE]
> W przypadku instalowania więcej niż jednej wersji aplikacji przy użyciu technologii ClickOnce instalacja przenosi wcześniejsze wersje aplikacji do folderu o nazwie archiwalne w określonej lokalizacji publikowania. Archiwizowanie wcześniejszych wersji w ten sposób powoduje, że katalog instalacyjny jest niezrozumiały dla folderów ze starszej wersji.

### <a name="to-specify-a-publishing-location"></a>Aby określić lokalizację publikowania

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **Publikowanie** .

3. W polu **Publikuj lokalizację** wprowadź lokalizację publikowania przy użyciu jednego z następujących formatów:

   - Aby opublikować w udziale plików lub w ścieżce dysku, wprowadź ścieżkę przy użyciu ścieżki UNC ( \\ \Server\ApplicationName) lub ścieżki pliku (C:\Deploy\ApplicationName).

   - Aby opublikować na serwerze FTP, wprowadź ścieżkę przy użyciu formatu FTP: \/ /FTP.Microsoft.com/ApplicationName.

     Zwróć uwagę, że tekst musi być obecny w polu **Lokalizacja publikowania** , aby można było wykonać przycisk Przeglądaj (**...**).

## <a name="see-also"></a>Zobacz też
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md) [instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
