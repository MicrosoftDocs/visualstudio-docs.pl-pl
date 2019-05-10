---
title: 'Instrukcje: Określ, gdzie plików kopii programu Visual Studio 2015 | Dokumentacja firmy Microsoft'
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
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226163"
---
# <a name="how-to-specify-where-visual-studio-copies-the-files"></a>Instrukcje: Określanie lokalizacji kopiowania plików przez program Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podczas publikowania aplikacji przy użyciu technologii ClickOnce, `Publish Location` właściwość określa lokalizację, gdzie umieścić pliki aplikacji i manifest. Może to być ścieżka pliku lub ścieżkę do serwera FTP.

 Można określić `Publish Location` właściwość **Publikuj** strony **projektanta projektu**, lub za pomocą Kreatora publikacji. Aby uzyskać więcej informacji, zobacz [jak: Publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).

> [!NOTE]
> Po zainstalowaniu więcej niż jedna wersja aplikacji przy użyciu technologii ClickOnce, instalacja przemieszcza inne wersje aplikacji do folderu o nazwie archiwum, w lokalizacji publikowania, który określisz. Archiwizowanie starszych w ten sposób utrzymuje katalogu instalacyjnyego folderów z wcześniejszych wersji.

### <a name="to-specify-a-publishing-location"></a>Aby określić lokalizację publikowania

1. Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.

2. Kliknij przycisk **Publikuj** kartę.

3. W **lokalizacji publikowania** wprowadź lokalizację publikowania za pomocą jednego z następujących formatów:

   - Aby opublikować udziału lub dysku ścieżki pliku, wprowadź ścieżkę przy użyciu ścieżki UNC (\\\Server\ApplicationName) lub ścieżkę do pliku (C:\Deploy\ApplicationName).

   - Aby opublikować na serwerze FTP, wprowadź ścieżkę przy użyciu protokołu ftp format:\//ftp.microsoft.com/ApplicationName.

     Należy pamiętać, że tekst musi znajdować się w **lokalizację publikowania** polu w kolejności do przeglądania (**...** ) przycisku do pracy.

## <a name="see-also"></a>Zobacz też
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md) [jak: Publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
