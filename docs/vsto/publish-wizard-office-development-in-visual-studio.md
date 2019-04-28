---
title: Kreator publikacji (Office development w programie Visual Studio)
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7879ad7cf18c3d09fddbab3923296e0896688af9
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447067"
---
# <a name="publish-wizard-office-development-in-visual-studio"></a>Kreator publikacji (Office development w programie Visual Studio)
  Użyj **Kreatora publikacji** Aby skopiować pliki rozwiązania do określonej lokalizacji, Utwórz pliki manifestu i Utwórz program instalacyjny.

 Dostęp do tego kreatora w **kompilacji** menu, wybierz **Publikuj** *SolutionName*. Można również przejść **Kreatora publikacji** z **Eksploratora rozwiązań**. Otwórz menu skrótów dla węzła projektu, a następnie wybierz **Publikuj**.

 Poniższej sekcji opisano strony kreatora.

## <a name="where-do-you-want-to-publish-the-application"></a>Gdzie chcesz opublikować aplikację?
 **Określ lokalizację do publikowania tej aplikacji** wymagane. Lokalizacji publikowania jest katalogiem gdzie **Kreatora publikacji** kopiuje pliki rozwiązania, takie jak manifestów, zestawy, tymczasowy certyfikat i innych plików z kompilacji. Musi mieć dostęp do zapisu do tego katalogu.

 Wpisz lokalizację jako ścieżka na dysku, udziału plików, witryny FTP lub adres URL witryny sieci web, lub kliknij przycisk **Przeglądaj** przycisk, aby wyszukać lokalizację. Ścieżka może być w tych formatach:

- Względna lub bezwzględna ścieżka w standardzie Windows formatowania, takich jak *C:\Deploy\MyApplication* lub *\MyApplication*.

- Ścieżka Universal Naming Convention (UNC), takie jak  *\\\ServerName\MyApplication\\*.

- Adres URL sieci Web site, takich jak http://www.microsoft.com/MyApplication.

  Domyślnie jest lokalizacja publikowania *http://localhost/projectname/* usługi IIS są zainstalowane, czy katalog publish\, jeśli to zrobisz nie IIS zainstalowany.

> [!NOTE]
> Jeśli na komputerze docelowym systemem Windows Vista jest więcej istotnych kwestii. Musisz być administratorem na komputerze Windows Vista do korzystania z opcji publikowania lokalnych. Ponadto domyślna lokalizacja to zawsze *publikowania\\*  katalogu, niezależnie od tego, czy zostały zainstalowane usługi IIS.

## <a name="what-is-the-default-installation-path-on-end-user-computers"></a>Co to jest domyślna ścieżka instalacji na komputerach użytkowników końcowych?
 Ścieżka instalacji jest opcjonalne. Można ustawić ścieżki instalacji później, jeśli użytkownik sobie tego życzy. Aby uzyskać więcej informacji, zobacz [jak: Zmień ścieżkę instalacji rozwiązania do pakietu Office](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).

 Ścieżka instalacji jest katalog, z którego użytkownik zainstaluje dostosowania. Należy również ścieżki, który rozwiązanie będzie używany do sprawdzenia aktualizacji. **Kreatora publikacji** nie wdrażają rozwiązania do tej lokalizacji, chyba, że ścieżka jest taka sama jak wprowadzona w **Określ lokalizację do publikowania tej aplikacji** pole na poprzedniej stronie.

 **Z witryny sieci Web** Podaj adres URL, do którego użytkownicy końcowi będą wykonać, aby zainstalować rozwiązanie.

 **Z udziału pliku lub ścieżki UNC** Określ ścieżkę UNC, które użytkownicy końcowi będą wykonać, aby zainstalować rozwiązanie.

 **Z dysku CD-ROM lub DVD-ROM** ta opcja nie wymaga ścieżkę instalacji.

 Program Visual Studio nie nagrywanie, dysku CD lub DVD. Należy ręcznie skopiuj dane wyjściowe na dysku CD lub DVD.

## <a name="see-also"></a>Zobacz także
- [Wdrażanie rozwiązania do pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Strona publikowania, Projektant projektu &#40;programowanie Office w Visual Studio&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)
- [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)
