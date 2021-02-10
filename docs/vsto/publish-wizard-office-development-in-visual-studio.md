---
title: Kreator publikacji (Office Development w Visual Studio)
description: Dowiedz się, jak można użyć Kreatora publikacji do kopiowania plików rozwiązania do określonej lokalizacji, tworzenia plików manifestu i tworzenia programów instalacyjnych w programie Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.PublishWizard
- VST.PublishWizard.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ClickOnce deployment [Office development in Visual Studio], Publish Wizard
- deploying applications [Office development in Visual Studio], Publish Wizard
- Office applications [Office development in Visual Studio], Publish Wizard
- Publish Wizard, Office solutions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 29400e82dcd7b0d5cd9062679610b50bfaab191d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971690"
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>Kreator publikacji (Office Development w Visual Studio)
  Użyj **Kreatora publikacji** do kopiowania plików rozwiązania do określonej lokalizacji, tworzenia plików manifestu i tworzenia programu instalacyjnego.

 Aby uzyskać dostęp do tego kreatora, w menu **kompilacja** wybierz polecenie **Publikuj** *rozwiązanie*. Możesz również uzyskać dostęp do **Kreatora publikacji** **Eksplorator rozwiązań**. Otwórz menu skrótów dla węzła projektu, a następnie wybierz polecenie **Publikuj**.

 W każdej sekcji poniżej opisano stronę kreatora.

## <a name="where-do-you-want-to-publish-the-application"></a>Gdzie chcesz opublikować aplikację?
 **Określ lokalizację, w której ma zostać opublikowana aplikacja** Wymagane. Lokalizacja publikowania to katalog, w którym **Kreator publikacji** kopiuje pliki rozwiązania, takie jak manifesty, zestawy, certyfikat tymczasowy i inne pliki z kompilacji. Musisz mieć dostęp do zapisu w tym katalogu.

 Wpisz lokalizację jako ścieżkę dysku, udział plików, witrynę FTP lub adres URL witryny sieci Web, lub kliknij przycisk **Przeglądaj** , aby wyszukać lokalizację. Ścieżka może być w następujących formatach:

- Ścieżka względna lub bezwzględna w standardowym formacie systemu Windows, na przykład *C:\Deploy\MyApplication* lub *\MyApplication*.

- Ścieżka Universal Naming Convention (UNC), taka jak *\\ \ServerName\MyApplication \\*.

- Adres URL witryny sieci Web, na przykład `http://www.contoso.com/MyApplication` .

  Domyślnie lokalizacja publikowania to *http://localhost/projectname/* , czy program IIS jest zainstalowany, lub polecenie Publikuj \ katalog, jeśli nie zainstalowano usług IIS.

> [!NOTE]
> Jeśli na komputerze docelowym jest uruchomiony system Windows Vista, należy wziąć pod uwagę więcej zagadnień. Aby użyć opcji publikowania lokalnego, musisz być administratorem na komputerze z systemem Windows Vista. Ponadto domyślną lokalizacją jest zawsze katalog *publikowania \\* , niezależnie od tego, czy są zainstalowane usługi IIS.

## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>Jaka jest domyślna ścieżka instalacji na komputerach użytkowników końcowych?
 Ścieżka instalacji jest opcjonalna. Możesz ustawić ścieżkę instalacji później, jeśli wolisz. Aby uzyskać szczegółowe informacje, zobacz [jak to zrobić: zmiana ścieżki instalacji rozwiązania pakietu Office](/previous-versions/bb608626(v=vs.110)).

 Ścieżka instalacji to katalog, z którego użytkownik końcowy zainstaluje dostosowanie. Jest to również ścieżka, która będzie używana przez rozwiązanie do sprawdzania dostępności aktualizacji. **Kreator publikacji** nie wdraża rozwiązania w tej lokalizacji, chyba że ścieżka jest taka sama jak wprowadzona w polu **Określ lokalizację do opublikowania aplikacji** na poprzedniej stronie.

 **Z witryny sieci Web** Określ adres URL, po którym użytkownicy końcowi będą mogli zainstalować rozwiązanie.

 **Ze ścieżki UNC lub udziału plików** Określ ścieżkę UNC, która będzie przestrzegana przez użytkowników końcowych w celu zainstalowania rozwiązania.

 **Z dysku CD-ROM lub DVD-ROM** Ta opcja nie wymaga ścieżki instalacji.

 Program Visual Studio nie nagrywa dysku CD lub DVD. Należy ręcznie skopiować dane wyjściowe na dysk CD lub DVD.

## <a name="see-also"></a>Zobacz też
- [Wdrażanie rozwiązania pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Strona publikowania, Projektant projektu &#40;Office Development w programie Visual Studio&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)
- [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md)