---
title: Strona publikowania, Projektant projektu
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.PropertyPage
helpviewer_keywords:
- Project Designer, Publish page
- Publish page in Project Designer
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 731ed637c8c728f51dd318e6c06b980e512b7d57
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59658308"
---
# <a name="publish-page-project-designer"></a>Strona publikowania, Projektant projektu
**Publikuj** strony **projektanta projektu** służy do konfigurowania właściwości dla wdrażania ClickOnce.

 Aby uzyskać dostęp do **Publikuj** wybierz węzeł projektu w **Eksploratora rozwiązań**, a następnie na **projektu** menu, kliknij przycisk **właściwości**. Podczas **projektanta projektu** zostanie wyświetlona, kliknij przycisk **publikowania** kartę.

> [!NOTE]
> Niektóre właściwości ClickOnce, opisane w tym miejscu można również ustawić **PublishWizard**, która jest dostępna z **kompilacji** menu lub przez kliknięcie przycisku **PublishWizard** przycisk na to Strona.

## <a name="uielement-list"></a>Lista elementów UI
 **Lokalizacja folderu publikowania**

 Określa lokalizację, w którym aplikacja została opublikowana. Może być ścieżką dysku (`C:\deploy\myapplication`), udział pliku (`\\server\myapplication`), lub na serwerze FTP (`ftp://ftp.microsoft.com/myapplication`). Należy pamiętać, że tekst musi znajdować się w **lokalizację publikowania** polu w kolejności do przeglądania (**...** ) przycisku do pracy.

 **Adres URL folderu instalacji**

 Opcjonalna. Określa witryny sieci Web, do której przejdzie do zainstalowania aplikacji. Jest to konieczne, tylko gdy różni się od **lokalizację publikowania**, na przykład, jeśli aplikacja została opublikowana serwer przejściowy.

 **Tryb i ustawienia instalacji**

 Określa, czy aplikacja jest uruchamiana bezpośrednio z **lokalizację publikowania** (gdy **aplikacja jest dostępna online tylko** wybrano) lub jest zainstalowana i dodać do **Start**  menu i **apletu Dodaj lub usuń programy** elementu w **Panelu sterowania** (gdy **aplikacja jest dostępna w trybie offline oraz** jest zaznaczona).

 W przypadku aplikacji przeglądarki WPF sieci web **aplikacja jest dostępna w trybie offline oraz** opcja jest wyłączona, ponieważ takie aplikacje są dostępne tylko w trybie online.

 **Pliki aplikacji**

 Zostanie otwarte okno dialogowe pliki aplikacji, które służy do określania, jak i gdzie poszczególne pliki są zainstalowane.

 **Wymagania wstępne**

 Zostanie otwarte okno dialogowe wymagań wstępnych, które służy do określania wstępnie wymagane składniki, takie jak .NET Framework, można zainstalować wraz z aplikacją.

 **Aktualizacje**

 Zostanie otwarte okno dialogowe aktualizacji aplikacji, które służy do określania zachowania aktualizacji dla aplikacji. Nie jest dostępna, gdy **aplikacja jest dostępna online tylko** jest zaznaczone.

 **Opcje**

 Otwiera okno dialogowe Opcje publikowania, który jest używany do określenia dodatkowych zaawansowane opcje publikowania.

 **Opublikuj wersję**

 Ustawia numer wersji publikowania dla aplikacji; Po zmianie numeru wersji, aplikacja została opublikowana jako aktualizację. Każda część wersję publikacji (**głównych**, **pomocnicza**, **kompilacji**, **poprawki**) może mieć maksymalną wartość 65355 (<xref:System.UInt16.MaxValue>), Maksymalna dozwolona przez <xref:System.Version>.

 Po zainstalowaniu więcej niż jedna wersja aplikacji przy użyciu technologii ClickOnce, instalacja przemieszcza inne wersje aplikacji do folderu o nazwie archiwum, w lokalizacji publikowania, który określisz. Archiwizowanie starszych w ten sposób utrzymuje katalogu instalacyjnyego folderów z wcześniejszych wersji.

 **Automatycznie zwiększ numer poprawki przy każdej publikacji**

 Opcjonalna. Po wybraniu tej opcji (ustawienie domyślne), **poprawki** część numeru wersji publikowania jest zwiększany o jeden każdym opublikowaniu aplikacji. To powoduje, że aplikacja opublikowana jako aktualizację.

 **Kreator publikacji**

 Zostanie otwarty Kreator publikacji. Kończenie pracy Kreatora publikacji ma taki sam skutek jak działa **Publikuj** polecenie **kompilacji** menu.

 **Publikuj teraz**

 Publikuje aplikacji przy użyciu bieżących ustawień. Odpowiednikiem **Zakończ** znajdujący się w **PublishWizard**.

## <a name="see-also"></a>Zobacz też

- [Publikowanie aplikacji ClickOnce](../../deployment/publishing-clickonce-applications.md)
- [Instrukcje: Publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Instrukcje: Określanie lokalizacji kopiowania plików przez program Visual Studio](../../deployment/how-to-specify-where-visual-studio-copies-the-files.md)
- [Instrukcje: Określanie lokalizacji, z której użytkownicy końcowi będą przeprowadzać instalacje](../../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)
- [Instrukcje: Określanie linku do pomocy technicznej](../../deployment/how-to-specify-a-link-for-technical-support.md)
- [Instrukcje: Określanie trybu instalacji offline lub online w ramach technologii ClickOnce](../../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)
- [Instrukcje: Włączanie funkcji AutoStart dla instalacji z dysku CD](../../deployment/how-to-enable-autostart-for-cd-installations.md)
- [Instrukcje: Ustawianie wersji publikacji technologii ClickOnce](../../deployment/how-to-set-the-clickonce-publish-version.md)
- [Instrukcje: Automatyczne zwiększanie wersji publikacji ClickOnce](../../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [Instrukcje: Określanie plików publikowanych za pomocą technologii ClickOnce](../../deployment/how-to-specify-which-files-are-published-by-clickonce.md)
- [Instrukcje: Instalowanie wstępnie wymaganych składników za pomocą aplikacji ClickOnce](../../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Instrukcje: Zarządzanie aktualizacjami dla aplikacji ClickOnce](../../deployment/how-to-manage-updates-for-a-clickonce-application.md)
- [Instrukcje: Zmienianie języka publikacji dla aplikacji ClickOnce](../../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)
- [Instrukcje: Określanie nazwy menu Start dla aplikacji ClickOnce](../../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)
- [Instrukcje: Określanie strony publikowania dla aplikacji ClickOnce](../../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)
- [Wskazówki dotyczące wdrażania i zabezpieczeń ClickOnce](../../deployment/clickonce-security-and-deployment.md)
