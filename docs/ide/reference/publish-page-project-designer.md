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
ms.openlocfilehash: 6bbb43408dc12c55b72eb0ca0909d8b261198a5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68926170"
---
# <a name="publish-page-project-designer"></a>Strona publikowania, Projektant projektu

Strona **Publikowanie** **projektanta projektu** służy do konfigurowania właściwości wdrażania ClickOnce.

Aby uzyskać dostęp do strony **Publikowanie** , wybierz węzeł projektu w **Eksplorator rozwiązań**, a następnie w menu **projekt** kliknij polecenie **Właściwości**. Gdy pojawi się **Projektant projektu** , kliknij kartę **Publikowanie** .

> [!NOTE]
> Niektóre z opisanych tutaj właściwości ClickOnce można także ustawić w **PublishWizard**, dostępne w menu **kompilacja** lub klikając przycisk **PublishWizard** na tej stronie.

## <a name="uielement-list"></a>Lista elementów UI

 **Lokalizacja folderu publikowania**

Określa lokalizację, w której aplikacja jest publikowana. Może to być ścieżka dysku ( `C:\deploy\myapplication` ), udział plików ( `\\server\myapplication` ) lub serwer FTP ( `ftp://ftp.microsoft.com/myapplication` ). Zwróć uwagę, że tekst musi być obecny w polu **Lokalizacja publikowania** , aby można było wykonać przycisk Przeglądaj (**...**).

 **Adres URL folderu instalacji**

Opcjonalny. Określa witrynę sieci Web, do której użytkownicy przejdą w celu zainstalowania aplikacji. Jest to konieczne tylko wtedy, gdy różni się od **lokalizacji publikowania**, na przykład po opublikowaniu aplikacji na serwerze przejściowym.

 **Tryb instalacji i ustawienia**

Określa, czy aplikacja jest uruchamiana bezpośrednio z **lokalizacji publikowania** (gdy **aplikacja jest dostępna w trybie online** jest zaznaczona) lub jest zainstalowana i dodawana do menu **Start** oraz w aplecie **Dodaj lub usuń programy** w **Panelu sterowania** (gdy **aplikacja jest dostępna w trybie offline, jak również** jest zaznaczona).

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

Ustawia numer wersji publikacji dla aplikacji; po zmianie numeru wersji aplikacja zostanie opublikowana jako aktualizacja. Każda część wersji publikacji (**główna**, **pomocnicza**, **kompilacja**, **poprawka**) może mieć maksymalną wartość 65355 ( <xref:System.UInt16.MaxValue> ), maksymalną dozwoloną przez <xref:System.Version> .

W przypadku instalowania więcej niż jednej wersji aplikacji przy użyciu technologii ClickOnce instalacja przenosi wcześniejsze wersje aplikacji do folderu o nazwie archiwalne w określonej lokalizacji publikowania. Archiwizowanie wcześniejszych wersji w ten sposób powoduje, że katalog instalacyjny jest niezrozumiały dla folderów ze starszej wersji.

 **Automatycznie Zwiększ numer poprawki przy każdej publikacji**

Opcjonalny. Gdy ta opcja jest zaznaczona (wartość domyślna), część **poprawki** numeru wersji publikacji jest zwiększana o jeden po opublikowaniu aplikacji. Powoduje to opublikowanie aplikacji jako aktualizacji.

 **Kreator publikacji**

Otwiera Kreatora publikacji. Ukończenie działania Kreatora publikacji ma taki sam skutek jak uruchomienie polecenia **Publikuj** w menu **kompilacja** .

 **Publikuj teraz**

Publikuje aplikację przy użyciu bieżących ustawień. Odpowiednik przycisku **Zakończ** w **PublishWizard**.

## <a name="see-also"></a>Zobacz też

- [Publikowanie aplikacji ClickOnce](../../deployment/publishing-clickonce-applications.md)
- [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Porady: określanie lokalizacji kopiowania plików przez program Visual Studio](../../deployment/how-to-specify-where-visual-studio-copies-the-files.md)
- [Instrukcje: określanie lokalizacji, z której użytkownicy końcowi będą przeprowadzać instalacje](../../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)
- [Instrukcje: określanie linku do pomocy technicznej](../../deployment/how-to-specify-a-link-for-technical-support.md)
- [Instrukcje: określanie trybu offline lub online instalowania za pomocą technologii ClickOnce](../../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)
- [Porady: włączenie funkcji AutoStart dla instalacji z dysku CD](../../deployment/how-to-enable-autostart-for-cd-installations.md)
- [Instrukcje: ustawienie wersji publikacji technologii ClickOnce](../../deployment/how-to-set-the-clickonce-publish-version.md)
- [Instrukcje: automatyczne zwiększenie wersji publikacji ClickOnce](../../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)
- [Instrukcje: określanie plików publikowanych za pomocą technologii ClickOnce](../../deployment/how-to-specify-which-files-are-published-by-clickonce.md)
- [Porady: instalowanie wstępnie wymaganych składników za pomocą aplikacji ClickOnce](../../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
- [Porady: zarządzanie aktualizacji dla aplikacji ClickOnce](../../deployment/how-to-manage-updates-for-a-clickonce-application.md)
- [Porady: zmienianie języka publikacji dla aplikacji ClickOnce](../../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)
- [Instrukcje: określanie nazwy menu Start dla aplikacji ClickOnce](../../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)
- [Instrukcje: określanie strony publikowania dla aplikacji ClickOnce](../../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)
- [Bezpieczeństwo i wdrażanie technologii ClickOnce](../../deployment/clickonce-security-and-deployment.md)
