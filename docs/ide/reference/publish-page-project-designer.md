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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "68926170"
---
# <a name="publish-page-project-designer"></a>Strona publikowania, Projektant projektu

Strona **Publikowania** **projektanta projektu** służy do konfigurowania właściwości wdrożenia ClickOnce.

Aby uzyskać dostęp do strony **Publikowanie,** wybierz węzeł projektu w **Eksploratorze rozwiązań,** a następnie w menu **Projekt** kliknij polecenie **Właściwości**. Po wyświetleniu **projektanta projektu** kliknij kartę **Publikuj.**

> [!NOTE]
> Niektóre właściwości ClickOnce opisane w tym miejscu można również ustawić w **PublishWizard**, dostępne z menu **Kompilacja** lub klikając przycisk **PublishWizard** na tej stronie.

## <a name="uielement-list"></a>Lista elementów UI

 **Lokalizacja folderu publikowania**

Określa lokalizację, w której aplikacja jest publikowana. Może to być`C:\deploy\myapplication`ścieżka dysku (`\\server\myapplication`), udział plików`ftp://ftp.microsoft.com/myapplication`( ) lub serwer FTP ( ). Należy pamiętać, że tekst musi znajdować się w polu **Lokalizacja publikowania,** aby przycisk przeglądania (**...**) działał.

 **Adres URL folderu instalacji**

Element opcjonalny. Określa witrynę sieci Web, do której użytkownicy przechodzą do zainstalowania aplikacji. Jest to konieczne tylko wtedy, gdy różni się od **lokalizacji publikowania**, na przykład, gdy aplikacja jest publikowana na serwerze przejściowym.

 **Tryb instalacji i ustawienia**

Określa, czy aplikacja jest uruchamiana bezpośrednio z **lokalizacji publikowania** (gdy aplikacja jest dostępna tylko **w trybie online** jest zaznaczona) lub jest zainstalowana i dodana do menu **Start** i elementu Dodaj lub **usuń programy** w **Panelu sterowania** (gdy aplikacja jest również dostępna w **trybie offline).**

W przypadku aplikacji przeglądarki sieci Web WPF **aplikacja jest dostępna w trybie offline, ponieważ** takie aplikacje są dostępne tylko w trybie online.

 **Pliki aplikacji**

Otwiera okno dialogowe Pliki aplikacji, które służy do określania sposobu i miejsca instalowania poszczególnych plików.

 **Wymagania wstępne**

Otwiera okno dialogowe Wymagania wstępne, które służy do określania składników wymagań wstępnych, takich jak .NET Framework, które mają być zainstalowane razem z aplikacją.

 **Aktualizacje**

Otwiera okno dialogowe Aktualizacje aplikacji, które służy do określania zachowania aktualizacji dla aplikacji. Opcja **niedostępna, gdy aplikacja jest dostępna tylko w trybie online.**

 **Opcje**

Otwiera okno dialogowe Opcje publikowania, które służy do określania dodatkowych zaawansowanych opcji publikowania.

 **Opublikuj wersję**

Ustawia numer wersji publikowania dla aplikacji; po zmianie numeru wersji aplikacja jest publikowana jako aktualizacja. Każda część wersji publikowania **(Major**, **Minor**, **Build**, **Revision**) może mieć<xref:System.UInt16.MaxValue>maksymalną wartość <xref:System.Version>65355 ( ), maksymalną dozwoloną przez .

Po zainstalowaniu więcej niż jednej wersji aplikacji przy użyciu ClickOnce, instalacja przenosi wcześniejsze wersje aplikacji do folderu o nazwie Archiwum, w lokalizacji publikowania, które określisz. Archiwizacja wcześniejszych wersji w ten sposób utrzymuje katalog instalacyjny z dala od folderów z wcześniejszej wersji.

 **Automatyczne zwiększanie wersji przy każdym publikowaniu**

Element opcjonalny. Po wybraniu tej opcji (domyślnie) **część rewizji** numeru wersji publikowania jest zwiększana o jeden za każdym razem, gdy aplikacja jest publikowana. Powoduje to, że aplikacja ma zostać opublikowana jako aktualizacja.

 **Kreator publikacji**

Otwiera Kreatora publikowania. Ukończenie Kreatora publikowania ma taki sam efekt jak uruchomienie polecenia **Publikuj** w menu **Kompilacja.**

 **Opublikuj teraz**

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
- [Kliknijonce zabezpieczenia i wdrażanie](../../deployment/clickonce-security-and-deployment.md)
