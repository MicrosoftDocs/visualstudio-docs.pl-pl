---
title: Strona publikowania, Projektant projektu
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.PropertyPage
helpviewer_keywords:
- Project Designer, Publish page
- Publish page in Project Designer
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aa33f3adc4fe05bd0df5c24bcb1fa769f93682cc
ms.sourcegitcommit: 85d66dc9fea3fa49018263064876b15aeb6f9584
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68461640"
---
# <a name="publish-page-project-designer"></a>Strona publikowania, Projektant projektu

Strona **Publikowanie** **projektanta projektu** służy do konfigurowania właściwości wdrażania ClickOnce.

 Aby uzyskać dostęp do strony **Publikowanie** , wybierz węzeł projektu w **Eksplorator rozwiązań**, a następnie w menu **projekt** kliknij polecenie **Właściwości**. Gdy pojawi się **Projektant projektu** , kliknij kartę **Publikowanie** .

> [!NOTE]
> Niektóre z opisanych tutaj właściwości ClickOnce można także ustawić w **PublishWizard**, dostępne w menu **kompilacja** lub klikając przycisk **PublishWizard** na tej stronie.

## <a name="uielement-list"></a>Lista elementów UI

 **Lokalizacja folderu publikowania**

 Określa lokalizację, w której aplikacja jest publikowana. Może to być ścieżka dysku (`C:\deploy\myapplication`), udział plików (`\\server\myapplication`) lub serwer FTP (`ftp://ftp.microsoft.com/myapplication`). Zwróć uwagę, że tekst musi być obecny w polu **Lokalizacja publikowania** , aby można było wykonać przycisk Przeglądaj ( **...** ).

 **Adres URL folderu instalacji**

 Opcjonalny. Określa witrynę sieci Web, do której użytkownicy przejdą w celu zainstalowania aplikacji. Jest to konieczne tylko wtedy, gdy różni się od **lokalizacji publikowania**, na przykład po opublikowaniu aplikacji na serwerze przejściowym.

 **Tryb instalacji i ustawienia**

 Określa, czy aplikacja jest uruchamiana bezpośrednio z **lokalizacji publikowania** (gdy **aplikacja jest dostępna w trybie online** jest zaznaczona) lub jest zainstalowana i dodawana do menu **Start** oraz do apletu **Dodaj lub usuń programy** w **Panel sterowania** (gdy **aplikacja jest dostępna w trybie offline, a także** jest zaznaczona).

 W przypadku aplikacji przeglądarki sieci Web WPF **aplikacja jest dostępna w trybie offline** , a opcja jest wyłączona, ponieważ takie aplikacje są dostępne tylko w trybie online.

 **Pliki aplikacji**

 Otwiera okno dialogowe pliki aplikacji, w którym można określić, w jaki sposób i gdzie są instalowane poszczególne pliki.

 **Wymagania wstępne**

 Otwiera okno dialogowe wymagania wstępne, które służy do określania składników wymaganych wstępnie, takich jak .NET Framework, które mają być instalowane razem z aplikacją.

 **Aktualizacje**

 Otwiera okno dialogowe aktualizacje aplikacji, w którym można określić zachowanie aktualizacji dla aplikacji. Niedostępne, gdy **aplikacja jest dostępna tylko w trybie online** jest zaznaczona.

 **Opcje**

 Otwiera okno dialogowe Opcje publikowania, które służy do określania dodatkowych opcji publikowania zaawansowanego.

 **Wersja publikacji**

 Ustawia numer wersji publikacji dla aplikacji; po zmianie numeru wersji aplikacja zostanie opublikowana jako aktualizacja. Każda część wersji publikacji (**główna**, pomocnicza , **kompilacja**, **poprawka**) może mieć maksymalną wartość 65355 (<xref:System.UInt16.MaxValue>), maksymalną dozwoloną przez. <xref:System.Version>

 Po zainstalowaniu więcej niż jedna wersja aplikacji przy użyciu technologii ClickOnce, instalacja przemieszcza inne wersje aplikacji do folderu o nazwie archiwum, w lokalizacji publikowania, który określisz. Archiwizowanie starszych w ten sposób utrzymuje katalogu instalacyjnyego folderów z wcześniejszych wersji.

 **Automatycznie Zwiększ numer poprawki przy każdej publikacji**

 Opcjonalny. Gdy ta opcja jest zaznaczona (wartość domyślna), część **poprawki** numeru wersji publikacji jest zwiększana o jeden po opublikowaniu aplikacji. Powoduje to opublikowanie aplikacji jako aktualizacji.

 **Kreator publikacji**

 Otwiera Kreatora publikacji. Ukończenie działania Kreatora publikacji ma taki sam skutek jak uruchomienie polecenia **Publikuj** w menu **kompilacja** .

 **Publikuj teraz**

 Publikuje aplikację przy użyciu bieżących ustawień. Odpowiednik przycisku **Zakończ** w **PublishWizard**.

## <a name="see-also"></a>Zobacz także

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
