---
title: 'Porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, publishing
- deploying applications [ClickOnce], Publish wizard
- Windows applications, ClickOnce deployments
- publishing, ClickOnce
ms.assetid: 2e4aa67c-4445-4f7b-9e03-9acb95829127
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 890a61290d7606fb2a03ea7aed2c4782e5b69b67
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388866"
---
# <a name="how-to-publish-a-clickonce-application-using-the-publish-wizard"></a>Porady: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji
Aby udostępnić aplikację ClickOnce użytkownikom, możesz opublikować go do udziału plików lub ścieżki, serwer FTP lub nośnik wymienny. Aplikację można opublikować za pomocą Kreatora publikacji; dodatkowe właściwości związanych z publikowaniem są dostępne na **Publikuj** strony **projektanta projektu**. Aby uzyskać więcej informacji, zobacz [publikowania ClickOnce applications](../deployment/publishing-clickonce-applications.md).

Przed uruchomieniem Kreatora publikowania należy odpowiednio ustawić właściwości publikacji. Na przykład, jeśli chcesz wyznaczyć klucz w celu podpisania aplikacji ClickOnce, możecie więc na **podpisywanie** strony **projektanta projektu**. Aby uzyskać więcej informacji, zobacz [aplikacji Secure ClickOnce](../deployment/securing-clickonce-applications.md).

> [!NOTE]
> Po zainstalowaniu więcej niż jedna wersja aplikacji przy użyciu technologii ClickOnce, instalacja przemieszcza inne wersje aplikacji do folderu o nazwie *archiwum*, w lokalizacji publikowania, który określisz. Archiwizowanie starszych w ten sposób utrzymuje katalogu instalacyjnyego folderów z wcześniejszych wersji.

> [!NOTE]
> Polecenia menu i okien dialogowych mogą różnić się od tych opisanych w pomocy, w zależności od ustawień aktywnych lub wersji. Aby zmienić swoje ustawienia, kliknij przycisk **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [zresetować ustawienia](../ide/environment-settings.md#reset-settings).

## <a name="to-publish-to-a-file-share-or-path"></a>Aby opublikować do udziału plików lub ścieżki

1. W **Eksploratora rozwiązań**, wybierz projekt aplikacji.

2. Na **kompilacji** menu, kliknij przycisk **Publikuj** *Projectname*.

    Pojawi się Kreator publikacji.

3. W **gdzie chcesz opublikować aplikację?** strony, wprowadź prawidłowy adres serwera FTP lub prawidłową ścieżkę do pliku przy użyciu jednego z formatów wyświetlane, a następnie kliknij **dalej**.

4. W **sposób będą użytkownicy instalować aplikację?** stronie, wybierz lokalizację, gdzie użytkownicy mają zainstalować aplikację:

   -   Jeśli użytkownicy będą instalować z witryny sieci Web, kliknij przycisk **z witryny sieci Web** i wprowadź adres URL, który odnosi się do ścieżki pliku wprowadzonej w poprzednim kroku. Kliknij przycisk **Dalej**. (Ta opcja jest zazwyczaj używana podczas określania adresu FTP jako lokalizacji publikowania. Bezpośrednie pobieranie z FTP nie jest obsługiwane. W związku z tym musisz wpisać URL tutaj.)

   -   Jeśli użytkownicy będą instalować aplikację bezpośrednio z udziału plików, kliknij przycisk **z UNC udziału pliku lub ścieżki**, a następnie kliknij przycisk **dalej**. (To jest do publikowania lokalizacji formularza *c:\deploy\myapp* lub  *\\\server\myapp*.)

   -   Jeśli użytkownicy będą instalować z nośników wymiennych, kliknij przycisk **z dysku CD-ROM lub DVD-ROM**, a następnie kliknij przycisk **dalej**.

5. Na **aplikacja będzie dostępna w trybie offline?** kliknij odpowiednią opcję:

   - Jeśli chcesz umożliwić uruchomienie aplikacji kiedy użytkownik jest odłączony od sieci, kliknij przycisk **tak, ta aplikacja będzie dostępna online lub offline**. Skrót na **Start** menu zostanie utworzony dla aplikacji.

   - Jeśli chcesz uruchomić aplikację bezpośrednio z lokalizacji publikacji, kliknij przycisk **nie, ta aplikacja jest dostępna tylko online**. Skrót na **Start** menu nie zostanie utworzony.

     Kliknij przycisk **Dalej** , aby kontynuować.

6. Kliknij przycisk **Zakończ** Aby opublikować aplikację.

    Stan publikowania jest wyświetlany w obszarze powiadomień stanu.

## <a name="to-publish-to-a-cd-rom-or-dvd-rom"></a>Aby opublikować na CD-ROM lub DVD-ROM

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt aplikacji i kliknij przycisk **właściwości**.

    **Projektanta projektu** pojawia się.

2. Kliknij przycisk **Publikuj** kartę, aby otworzyć **Publikuj** strony w **projektanta projektu**i kliknij przycisk **Kreatora publikacji** przycisku.

    Pojawi się Kreator publikacji.

3. W **gdzie chcesz opublikować aplikację?** strony, wprowadź ścieżkę do pliku lub lokalizację FTP, w którym aplikacja zostanie opublikowana, na przykład *d:\deploy*. Następnie kliknij przycisk **dalej** aby kontynuować.

4. Na **sposób będą użytkownicy instalować aplikację?** stronie, kliknij polecenie **dysku CD-ROM lub DVD-ROM**, a następnie kliknij przycisk **dalej**.

   > [!NOTE]
   >  Jeśli chcesz, aby instalacja do automatycznego uruchamiania podczas dysku CD-ROM jest wstawiany do stacji, otwórz **Publikuj** strony w **projektanta projektu** i kliknij przycisk **opcje** przycisk, a następnie w **opcji publikowania** kreatora wybierz **dla instalacji z dysku CD, automatycznie Rozpocznij instalację po włożeniu dysku CD**.

5. Jeśli dystrybucji aplikacji na dysku CD-ROM, można dostarczać aktualizacje z witryny sieci Web. W **gdzie aplikacja będzie sprawdzać aktualizacje?** stronie, wybierz opcję aktualizacji:

   - Jeśli aplikacja będzie sprawdzać dostępność aktualizacji, kliknij przycisk **aplikacja będzie sprawdzać dostępność aktualizacji z następującej lokalizacji** i podaj lokalizację, w której będą się pojawiać aktualizacje. Może to być lokalizacja pliku, witryny sieci Web lub serwera FTP.

   - Jeśli aplikacja nie będzie sprawdzać dostępność aktualizacji, kliknij przycisk **aplikacji nie będzie sprawdzać dostępność aktualizacji**.

     Kliknij przycisk **Dalej** , aby kontynuować.

6. Kliknij przycisk **Zakończ** Aby opublikować aplikację.

    Stan publikowania jest wyświetlany w obszarze powiadomień stanu.

   > [!NOTE]
   >  Po ukończeniu publikacji, należy użyć nagrywarki dysków CD lub nagrywarka DVD, aby skopiować pliki z lokalizacji określonej w kroku 3 do stacji CD-ROM lub DVD-ROM multimediów.

## <a name="see-also"></a>Zobacz także

- [Wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
- [Wdrażanie rozwiązania do pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)