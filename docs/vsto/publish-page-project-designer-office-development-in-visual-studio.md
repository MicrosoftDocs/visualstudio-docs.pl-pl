---
title: Strona publikowania, Projektant projektu (Programowanie Office)
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectProperties.Publish.2007System
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- deploying applications [Office development in Visual Studio]
- publishing, Office solutions
- Property Pages dialog box, Publish [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 86d575b254209b547504ea6d746d03853990bfb4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "67329003"
---
# <a name="publish-page-project-designer-office-development-in-visual-studio"></a>Strona publikowania, Projektant projektu (Office Development w Visual Studio)
  Strona **Publikowanie** **projektanta projektu** służy do konfigurowania właściwości wdrożenia.

 Aby uzyskać dostęp do tej strony, zaznacz projekt w **Eksplorator rozwiązań**, a następnie w menu **projekt** wybierz polecenie właściwości *ProjectName* **Properties**. Jeśli strona **Publikowanie** nie jest wyświetlana, wybierz kartę **Publikowanie** .

> [!NOTE]
> Możesz również ustawić lokalizację publikacji w **Kreatorze publikacji**. Aby uzyskać więcej informacji, zobacz [jak: publikowanie rozwiązania pakietu Office przy użyciu technologii ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8).

## <a name="uielement-list"></a>Lista elementów UIElement
 **Lokalizacja folderu publikowania (witryna sieci Web, serwer FTP lub ścieżka pliku)** Wymagane.

 Lokalizacja folderu publikowania to katalog, do którego program Visual Studio kopiuje pliki rozwiązania, takie jak manifesty, zestawy i inne pliki z kompilacji. Musisz mieć dostęp do zapisu w tym katalogu.

 Dostępne opcje to: komputer lokalny, udział plików UNC lub witryna sieci Web HTTP/HTTPS. Ścieżka może być ścieżką lokalną (*c:\FolderName\PublishFolder*), względną (* \\ Publish*) lub w pełni kwalifikowaną lokalizacją (* \\ \servername\foldername* lub http://<em>servername/nazwa_folderu</em>).

 Domyślnie lokalizacja publikowania jest *http://localhost/projectname/* zainstalowana, jeśli są zainstalowane usługi IIS lub katalog *publikacji \\ * , jeśli nie zainstalowano usług IIS.

 **Adres URL folderu instalacji** Obowiązkowe.

 Adres URL folderu instalacji to katalog, z którego użytkownik końcowy zainstaluje dostosowanie. Jest to również ścieżka, która będzie używana przez rozwiązanie do sprawdzania dostępności aktualizacji. Ścieżka może być taka sama jak lokalizacja folderu publikowania, ale nie jest to wymagane.

 Dostępne opcje to: komputer lokalny, udział plików UNC lub witryna sieci Web HTTP/HTTPS. Ścieżka może być ścieżką lokalną (*c:\FolderName\PublishFolder*), względną (* \\ Publish*) lub w pełni kwalifikowaną lokalizacją (* \\ \servername\foldername* lub http://<em>servername/nazwa_folderu</em>). Wszystkie lokalizacje HTTP/HTTPS muszą być tworzone przy użyciu znaków US-ASCII. Znaki Unicode nie są obsługiwane.

 Jeśli ścieżka instalacji jest ustawiona, pliki dostosowania muszą znajdować się w tej lokalizacji, aby użytkownicy mogli instalować dostosowanie. Lokalizacja powinna być ustawiona tylko wtedy, gdy znasz końcową lokalizację wdrożenia.

 Jeśli pliki instalacyjne znajdują się w lokalizacji względem dokumentu lub Instalatora programu, na przykład z opcją CD, pozostaw to pole puste.

 Tę wartość można przypisać później przez administratora. Aby uzyskać więcej informacji, zobacz [How to: zmiana ścieżki instalacji rozwiązania pakietu Office](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).

 **Wymagania wstępne** Wymagania wstępne można dołączać do programu instalacyjnego lub pobrać na żądanie podczas instalacji.

- **Pobierz wstępnie wymagane składniki z witryny sieci Web dostawcy składników**: Użyj tej opcji, aby pobrać te wymagania wstępne od firmy Microsoft.

- **Pobierz wstępnie wymagane składniki z tej samej lokalizacji co moja aplikacja**: Użyj tej opcji, aby spakować wymagania wstępne w instalatorze. Dołączenie plików wymagań wstępnych z programem instalacyjnym zwiększa rozmiar rozwiązania.

- **Pobierz wstępnie wymagane składniki z następującej lokalizacji**: Użyj tej opcji, aby udostępnić wymagania wstępne użytkownikom końcowym niezależnie od innego programu instalacyjnego na stronie sieci Web lub w udziale sieciowym.

  **Aktualizacje** Interwał aktualizacji określa, jak często rozwiązanie sprawdza dostępność aktualizacji. Wartość domyślna to sprawdzanie co siedem dni.

  Sprawdzanie dostępności aktualizacji za każdym razem, gdy zostanie załadowane dostosowanie na poziomie dokumentu lub dodatek VSTO, będzie on aktualizowany, ale wpłynie to na wydajność uruchamiania.

  Jeśli wdrażasz program przy użyciu dysku CD lub dysku wymiennego, ustaw tę opcję na wartość **nigdy nie sprawdzaj, czy**są używane aktualizacje.

  **Opcje (opis)** Można ustawić opcje publikowania dla następujących właściwości:

- Język publikacji: ustawienia regionalne rozwiązania pakietu Office.

- Nazwa wydawcy: Nazwa firmy lub dewelopera wyświetlana w **aplecie Dodaj/Usuń programy** lub **programy i funkcje**.

- Nazwa produktu: Nazwa rozwiązania pakietu Office wyświetlana w **aplecie Dodaj/Usuń programy** lub **programy i funkcje**.

- Adres URL pomocy technicznej: lokalizacja dla użytkowników końcowych kontaktu z pomocą techniczną dla rozwiązania pakietu Office.

  **Opcje (Ustawienia pakietu Office)** Można ustawić opcje publikowania dla następujących właściwości:

- Nazwa rozwiązania: Nazwa rozwiązania pakietu Office, która pojawia się w aplikacji pakietu Office.

- Opis: Opis rozwiązania pakietu Office wyświetlanego w aplikacji pakietu Office.

- Zachowanie ładowania dodatku VSTO.

  - Załaduj przy uruchomieniu: określa, że dodatek VSTO ładuje się podczas uruchamiania aplikacji pakietu Office.

  - Załaduj na żądanie: określa, że dodatek VSTO ładuje się, gdy aplikacja wymaga tego, na przykład gdy użytkownik kliknie element interfejsu użytkownika, który używa funkcji w dodatku VSTO.

  **Język publikacji** Ta opcja ustawia język postanowień licencyjnych dotyczących oprogramowania firmy Microsoft i zawiera pakiety językowe z listy wymagań wstępnych. Nie ma to wpływu na język dostosowywania. Język w programie instalacyjnym jest określany na podstawie zainstalowanych języków programu Visual Studio.

  Aby uzyskać więcej informacji na temat zmiany **języka publikacji**, zobacz [How to: Change the Publish language for a ClickOnce](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md).

  **Wersja publikacji** Ustawia numer wersji do dostosowania. Po zmianie numeru wersji aplikacja zostanie opublikowana jako aktualizacja. Nowy folder jest tworzony dla każdej wersji podczas procesu kompilacji, aby zapobiec zastąpieniu wcześniej opublikowanej wersji. Każda część wersji publikacji (**główna**, **pomocnicza**, **kompilacja**, **poprawka**) może zawierać maksymalnie pięć cyfr.

  **Automatycznie Zwiększ numer poprawki przy każdej wersji** Obowiązkowe. Po wybraniu (wartość domyślna) część **poprawki** numeru wersji jest zwiększana o jeden przy każdym publikowaniu. Powoduje to, że dostosowanie zostanie opublikowane jako aktualizacja.

  **Publikuj teraz** Publikuje aplikację przy użyciu bieżących ustawień. Odpowiednik przycisku **Zakończ** w **Kreatorze publikacji**.

## <a name="see-also"></a>Zobacz też

- [Wdróż rozwiązanie pakietu Office](../vsto/deploying-an-office-solution.md)
- [Wdrażanie rozwiązania pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Wymagania wstępne dotyczące wdrażania pakietu Office](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e)
