---
title: 'Porady: Określanie, której pliki kopii programu Visual Studio 2015 | Dokumentacja firmy Microsoft'
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: wpickett
ms.openlocfilehash: 2fe9fba9ebfd5690bb54add6e2d4e09da3027796
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53051495"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Porady: określanie lokalizacji kopiowania plików przez program Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas publikowania aplikacji przy użyciu technologii ClickOnce, `Publish Location` właściwość określa lokalizację, gdzie umieścić pliki aplikacji i manifest. Może to być ścieżka pliku lub ścieżkę do serwera FTP.

 Można określić `Publish Location` właściwość **Publikuj** strony **projektanta projektu**, lub za pomocą Kreatora publikacji. Aby uzyskać więcej informacji, zobacz [porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!NOTE]
>  Po zainstalowaniu więcej niż jedna wersja aplikacji przy użyciu technologii ClickOnce, instalacja przemieszcza inne wersje aplikacji do folderu o nazwie archiwum, w lokalizacji publikowania, który określisz. Archiwizowanie starszych w ten sposób utrzymuje katalogu instalacyjnyego folderów z wcześniejszych wersji.

### <a name="to-specify-a-publishing-location"></a>Aby określić lokalizację publikowania

1. Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.

2. Kliknij przycisk **Publikuj** kartę.

3. W **lokalizacji publikowania** wprowadź lokalizację publikowania za pomocą jednego z następujących formatów:

   - Aby opublikować udziału lub dysku ścieżki pliku, wprowadź ścieżkę przy użyciu ścieżki UNC (\\\Server\ApplicationName) lub ścieżkę do pliku (C:\Deploy\ApplicationName).

   - Aby opublikować na serwerze FTP, należy wprowadzić ścieżkę przy użyciu ftp://ftp.microsoft.com/ApplicationName formatu.

     Należy pamiętać, że tekst musi znajdować się w **lokalizację publikowania** polu w kolejności do przeglądania (**...** ) przycisku do pracy.

## <a name="see-also"></a>Zobacz też
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md) [porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
