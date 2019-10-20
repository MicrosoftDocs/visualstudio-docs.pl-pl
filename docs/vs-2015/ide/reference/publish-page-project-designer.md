---
title: Strona publikowania, Projektant projektu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.PropertyPage
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Project Designer, Publish page
- Publish page in Project Designer
ms.assetid: 153527c6-8b95-4003-8e8e-03a489d0a629
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 391e6c457dd09afa154c46cbc8644f028052cb32
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665703"
---
# <a name="publish-page-project-designer"></a>Strona publikowania, Projektant projektu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Strona **Publikowanie** **projektanta projektu** służy do konfigurowania właściwości wdrażania ClickOnce.

 Aby uzyskać dostęp do strony **Publikowanie** , wybierz węzeł projektu w **Eksplorator rozwiązań**, a następnie w menu **projekt** kliknij polecenie **Właściwości**. Gdy pojawi się **Projektant projektu** , kliknij kartę **Publikowanie** .

> [!NOTE]
> Niektóre z opisanych tutaj właściwości ClickOnce można także ustawić w **PublishWizard**, dostępne w menu **kompilacja** lub klikając przycisk **PublishWizard** na tej stronie.

## <a name="uielement-list"></a>Lista elementów UI
 **Lokalizacja folderu publikowania** Określa lokalizację, w której aplikacja jest publikowana. Może to być ścieżka dysku (`C:\deploy\myapplication`), udział plików (`\\server\myapplication`), serwer FTP (`ftp://ftp.microsoft.com/myapplication`) lub witryna sieci Web (`http://www.microsoft.com/myapplication`). Zwróć uwagę, że tekst musi być obecny w polu **Lokalizacja publikowania** , aby można było wykonać przycisk Przeglądaj ( **...** ).

 Domyślnie lokalizacja publikowania jest `http://localhost/<projectname>/`, jeśli są zainstalowane usługi IIS lub katalog `publish\`, jeśli nie zainstalowano usług IIS. Jeśli na komputerze jest uruchomiony system Windows Vista, domyślnie jest to katalog `publish\`, niezależnie od tego, czy są zainstalowane usługi IIS.

 **Adres URL folderu instalacji** Obowiązkowe. Określa witrynę sieci Web, do której użytkownicy przejdą w celu zainstalowania aplikacji. Jest to konieczne tylko wtedy, gdy różni się od **lokalizacji publikowania**, na przykład po opublikowaniu aplikacji na serwerze przejściowym.

 **Tryb instalacji i ustawienia** Określa, czy aplikacja jest uruchamiana bezpośrednio z **lokalizacji publikowania** (gdy **aplikacja jest dostępna w trybie online** jest zaznaczona) lub jest zainstalowana i dodawana do menu **Start** oraz do apletu **Dodaj lub usuń programy** w **Panel sterowania** (gdy **aplikacja jest dostępna w trybie offline, jak również** jest zaznaczona).

 W przypadku aplikacji przeglądarki sieci Web WPF **aplikacja jest dostępna w trybie offline** , a opcja jest wyłączona, ponieważ takie aplikacje są dostępne tylko w trybie online.

 **Pliki aplikacji** Otwiera [okno dialogowe pliki aplikacji](https://msdn.microsoft.com/b06dff3a-b87a-4caf-996b-7a4acf8137a8), w którym można określić, w jaki sposób i gdzie są instalowane poszczególne pliki.

 **Wymagania wstępne** Otwiera [okno dialogowe wymagania wstępne](../../ide/reference/prerequisites-dialog-box.md), które służy do określania składników wymaganych wstępnie, takich jak .NET Framework, które mają być instalowane razem z aplikacją.

 **Aktualizacje** Otwiera okno [dialogowe aktualizacje aplikacji](https://msdn.microsoft.com/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f), w którym można określić zachowanie aktualizacji dla aplikacji. Niedostępne, gdy **aplikacja jest dostępna tylko w trybie online** jest zaznaczona.

 **Opcje** Otwiera okno [dialogowe Opcje publikowania](https://msdn.microsoft.com/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), które służy do określania dodatkowych opcji publikowania zaawansowanego.

 **Wersja publikacji** Ustawia numer wersji publikacji dla aplikacji; po zmianie numeru wersji aplikacja zostanie opublikowana jako aktualizacja. Każda część wersji publikacji (**główna**, **pomocnicza**, **kompilacja**, **poprawka**) może mieć maksymalną wartość 65355 (<xref:System.UInt16.MaxValue>), maksymalną dozwoloną przez <xref:System.Version>.

 W przypadku instalowania więcej niż jednej wersji aplikacji przy użyciu technologii ClickOnce instalacja przenosi wcześniejsze wersje aplikacji do folderu o nazwie archiwalne w określonej lokalizacji publikowania. Archiwizowanie wcześniejszych wersji w ten sposób powoduje, że katalog instalacyjny jest niezrozumiały dla folderów ze starszej wersji.

 **Automatycznie Zwiększ numer poprawki przy każdej publikacji** Obowiązkowe. Gdy ta opcja jest zaznaczona (wartość domyślna), część **poprawki** numeru wersji publikacji jest zwiększana o jeden po opublikowaniu aplikacji. Powoduje to opublikowanie aplikacji jako aktualizacji.

 **Kreator publikacji** Otwiera [Kreatora publikacji](https://msdn.microsoft.com/fc6abebd-13d6-48e4-a567-fbc52dad0872). Ukończenie działania Kreatora publikacji ma taki sam skutek jak uruchomienie polecenia **Publikuj** w menu **kompilacja** .

 **Publikuj teraz** Publikuje aplikację przy użyciu bieżących ustawień. Odpowiednik przycisku **Zakończ** w **PublishWizard**.

## <a name="see-also"></a>Zobacz też
 [Publikowanie aplikacji ClickOnce](../../deployment/publishing-clickonce-applications.md) [instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) [instrukcje: Określanie, gdzie program Visual Studio kopiuje pliki](../../deployment/how-to-specify-where-visual-studio-copies-the-files.md) [: Określ lokalizację, z której użytkownicy końcowi będą instalować](../../deployment/how-to-specify-the-location-where-end-users-will-install-from.md) [ Aby: określić link do pomocy technicznej](../../deployment/how-to-specify-a-link-for-technical-support.md) [, jak: Określanie trybu offline lub w trybie online,](../../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md) jak to zrobić: [Włącz Autostart dla instalacji z dysku CD](../../deployment/how-to-enable-autostart-for-cd-installations.md) [instrukcje: Ustaw wersję publikacji ClickOnce,](../../deployment/how-to-set-the-clickonce-publish-version.md) [jak: automatycznie zwiększaj Wersja publikacji ClickOnce](../../deployment/how-to-automatically-increment-the-clickonce-publish-version.md) [: Określanie, które pliki są publikowane przez ClickOnce](../../deployment/how-to-specify-which-files-are-published-by-clickonce.md) [instrukcje: instalowanie wstępnie wymaganych składników za pomocą aplikacji ClickOnce](../../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) [: Zarządzanie aktualizacjami aplikacji ClickOnce](../../deployment/how-to-manage-updates-for-a-clickonce-application.md) [jak: zmiana Język publikacji aplikacji ClickOnce](../../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md) [instrukcje: Określanie nazwy menu Start dla aplikacji ClickOnce](../../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md) [instrukcje: Określanie strony publikowania dla](../../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md) [zabezpieczeń i wdrożenia](../../deployment/clickonce-security-and-deployment.md) aplikacji ClickOnce
