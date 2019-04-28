---
title: Strona publikowania, Projektant projektu (Office development w programie Visual Studio)
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
ms.openlocfilehash: 84a62fc796243172c9130c8113c4e6d289ed3092
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447014"
---
# <a name="publish-page-project-designer-office-development-in-visual-studio"></a>Strona publikowania, Projektant projektu (Office development w programie Visual Studio)
  **Publikuj** strony **projektanta projektu** służy do konfigurowania właściwości dla wdrożenia.

 Dostępu do tej strony, wybierz projekt w **Eksploratora rozwiązań**, a następnie na **projektu** menu, wybierz *Projectname* **właściwości** . Jeśli **Publikuj** nie zostanie wyświetlona strona, wybierz polecenie **Publikuj** kartę.

> [!NOTE]
> Można również ustawić lokalizację publikowania w **Kreatora publikacji**. Aby uzyskać więcej informacji, zobacz [jak: Publikowanie rozwiązań pakietu Office przy użyciu technologii ClickOnce](https://msdn.microsoft.com/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8).

## <a name="uielement-list"></a>Lista elementów interfejsu użytkownika
 **Publikowanie lokalizacji folderu (witryny sieci web, serwer ftp lub ścieżka do pliku)** wymagane.

 Lokalizacja folderu publikowania jest to katalog, do którego program Visual Studio kopiuje pliki rozwiązania, takie jak manifestów, zespoły i innych plików z kompilacji. Musi mieć dostęp do zapisu do tego katalogu.

 Opcje obejmują komputera lokalnego, UNC udziału plików lub witryny sieci web HTTP/HTTPS. Ścieżka może być lokalny (*c:\foldername\publishfolder*) względnych (*publikowania\\*), lub w pełni kwalifikowanej lokalizacji (*\\\servername\foldername* lub http://<em>servername/foldername</em>).

 Domyślnie jest lokalizacja publikowania *http://localhost/projectname/* Jeśli usługi IIS są zainstalowane, lub *publikowania\\*  katalogu, jeśli nie masz zainstalowane usługi IIS.

 **Adres URL folderu instalacyjnego** opcjonalne.

 Adres URL folderu instalacyjnego jest to katalog, z którego użytkownik zainstaluje dostosowania. Należy również ścieżki, który rozwiązanie będzie używany do sprawdzenia aktualizacji. Ścieżka może być taka sama jak lokalizacja folderu publikowania, ale nie jest wymagane.

 Opcje obejmują komputera lokalnego, UNC udziału plików lub witryny sieci web HTTP/HTTPS. Ścieżka może być lokalny (*c:\foldername\publishfolder*) względnych (*publikowania\\*), lub w pełni kwalifikowanej lokalizacji (*\\\servername\foldername* lub http://<em>servername/foldername</em>). Wszystkie lokalizacje HTTP/HTTPS musi zostać utworzona z znaki US-ASCII. Znaki Unicode nie są obsługiwane.

 Jeśli ścieżka instalacji jest ustawiona, pliki dostosowania musi być w tej lokalizacji, użytkownicy mogą zainstalować dostosowania. Lokalizacja powinna być ustawiona tylko wtedy, gdy znasz lokalizacji końcowej wdrożenia.

 Jeśli pliki instalacyjne znajdują się w lokalizacji względnej wobec dokumentu lub program instalacyjny, takich jak z opcją dysku CD, pozostaw to pole puste.

 Tę wartość można przypisać później przez administratora. Aby uzyskać więcej informacji, zobacz [jak: Zmień ścieżkę instalacji rozwiązania do pakietu Office](https://msdn.microsoft.com/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).

 **Wymagania wstępne** wymagań wstępnych, które mogą być dołączone do programu instalacyjnego lub pobrane na żądanie, podczas instalacji.

- **Pobierz wstępnie wymagane składniki z witryny dostawcy składników**: Użyj tej opcji, aby pobrać te wymagania wstępne od firmy Microsoft.

- **Pobierz wstępnie wymagane składniki z tej samej lokalizacji co aplikację**: Użyj tej opcji, aby utworzyć pakiet wstępnie wymagane składniki Instalatora w. W tym pliki wymagań wstępnych programu instalacyjnego zwiększa rozmiar rozwiązania.

- **Pobierz wstępnie wymagane składniki z następującej lokalizacji**: Użyj tej opcji, aby udostępnić wymagania wstępne dla użytkowników końcowych oddzielnie jako inny program instalacyjny na stronie sieci web lub udziału sieciowego.

  **Aktualizacje** Określa interwał aktualizacji, jak często rozwiązanie sprawdza dostępność aktualizacji. Wartość domyślna to, aby sprawdzić, co siedem dni.

  Sprawdzanie dostępności aktualizacji za każdym razem, gdy jest ładowany dostosowywania poziomie dokumentu lub dodatku narzędzi VSTO zachowa ona zaktualizowana, ale będzie mieć wpływ na wydajność uruchamiania.

  Jeśli są wdrażane przy użyciu dysku CD lub dysku wymiennego, ustaw tę opcję na **nigdy nie sprawdzaj aktualizacji**.

  **Opcje (opis)** można ustawić opcje publikowania dla następujących właściwości:

- Język publikacji: ustawienia regionalne rozwiązania dla pakietu Office.

- Nazwa wydawcy: Nazwa firmy lub developer postaci, w jakiej jest wyświetlana w **Dodaj/Usuń programy** lub **programy i funkcje**.

- Nazwa produktu: Nazwa rozwiązania dla pakietu Office postaci, w jakiej pojawi się w **Dodaj/Usuń programy** lub **programy i funkcje**.

- Adres URL pomocy technicznej: lokalizacja do się z pomocą techniczną dla rozwiązań Office dla użytkowników końcowych.

  **Opcje (ustawienia pakietu Office)** można ustawić opcje publikowania dla następujących właściwości:

- Nazwa rozwiązania: Nazwa rozwiązania dla pakietu Office postaci, w jakiej pojawi się w aplikacji pakietu Office.

- Opis: opis rozwiązania dla pakietu Office postaci, w jakiej jest wyświetlany w aplikacji pakietu Office.

- Zachowanie ładowania dodatku narzędzi VSTO dla programów.

  - Ładowania przy uruchamianiu: Określa, czy dodatku narzędzi VSTO ładuje podczas uruchamiania aplikacji Office.

  - Załaduj na żądanie: Określa, że dodatku narzędzi VSTO ładuje, kiedy aplikacja wymaga, np. kiedy użytkownik kliknie element interfejsu użytkownika, który korzysta z funkcji w dodatku VSTO.

  **Język publikacji** ta opcja określa język postanowienia licencyjne dotyczące oprogramowania firmy Microsoft i zawiera pakietów językowych w listę wymagań wstępnych. Nie ma ona wpływu na język dostosowania. Język w programie instalacyjnym jest określany przez zainstalowane języki programu Visual Studio.

  Aby uzyskać więcej informacji dotyczących sposobu zmieniania **języka publikacji**, zobacz [jak: Zmienianie języka publikacji dla aplikacji ClickOnce](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md).

  **Opublikuj wersję** Ustawia numer wersji dla dostosowania. Po zmianie numeru wersji, aplikacja została opublikowana jako aktualizację. Tworzony jest nowy folder dla każdej wersji podczas procesu kompilacji, aby zapobiec zastąpieniu poprzednio opublikowanej wersji. Każda część wersję publikacji (**głównych**, **pomocnicza**, **kompilacji**, **poprawki**) może zawierać maksymalnie pięciu cyfr.

  **Automatycznie zwiększ numer poprawki przy każdym wydaniu** atrybut opcjonalny. Po wybraniu (ustawienie domyślne), **poprawki** część numeru wersji jest zwiększany o jeden, za każdym razem, gdy opublikowania dostosowania. Powoduje to dostosowania, które mają zostać opublikowane jako aktualizację.

  **Publikuj teraz** publikuje aplikacji przy użyciu bieżących ustawień. Odpowiednikiem **Zakończ** znajdujący się w **Kreatora publikacji**.

## <a name="see-also"></a>Zobacz także

- [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)
- [Wdrażanie rozwiązania do pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)
- [Wymagania wstępne rozwiązania pakietu Office wdrożenia](https://msdn.microsoft.com/9f672809-43a3-40a1-9057-397ce3b5126e)
