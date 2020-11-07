---
title: Publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji
description: Dowiedz się więcej o używaniu Kreatora publikacji w celu udostępnienia aplikacji ClickOnce użytkownikom, w tym do których właściwości publikacji mają być używane.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 252d029e7e2e5b9b5dfe27b2fb1cd72e1c09b473
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94349883"
---
# <a name="how-to-publish-a-clickonce-application-using-the-publish-wizard"></a>Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji
Aby aplikacja ClickOnce była dostępna dla użytkowników, należy ją opublikować w udziale plików lub na ścieżce, serwerze FTP lub nośniku wymiennym. Aplikację można opublikować za pomocą Kreatora publikacji. dodatkowe właściwości związane z publikowaniem są dostępne na stronie **Publikuj** **projektanta projektu**. Aby uzyskać więcej informacji, zobacz [publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md).

Przed uruchomieniem Kreatora publikacji należy odpowiednio ustawić właściwości publikacji. Na przykład jeśli chcesz wyznaczyć klucz do podpisania aplikacji ClickOnce, możesz to zrobić na stronie **podpisywanie** w **projektancie projektu**. Aby uzyskać więcej informacji, zobacz [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md).

> [!NOTE]
> W przypadku instalowania więcej niż jednej wersji aplikacji przy użyciu technologii ClickOnce instalacja przenosi wcześniejsze wersje aplikacji do folderu o nazwie *archiwalne* w określonej lokalizacji publikowania. Archiwizowanie wcześniejszych wersji w ten sposób powoduje, że katalog instalacyjny jest niezrozumiały dla folderów ze starszej wersji.

> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, kliknij przycisk **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [Resetowanie ustawień](../ide/environment-settings.md#reset-settings).

## <a name="to-publish-to-a-file-share-or-path"></a>Aby opublikować do udziału plików lub ścieżki

1. W **Eksplorator rozwiązań** wybierz projekt aplikacji.

2. W menu **kompilacja** kliknij pozycję **Publikuj** *ProjectName*.

    Zostanie wyświetlony Kreator publikacji.

3. Na stronie **gdzie chcesz opublikować aplikację?** Wprowadź prawidłowy adres serwera FTP lub prawidłową ścieżkę pliku, używając jednego z wyświetlanych formatów, a następnie kliknij przycisk **dalej**.

4. Na stronie **jak użytkownicy będą instalować aplikację?** wybierz lokalizację, w której użytkownicy będą przechodzili, aby zainstalować aplikację:

   - Jeśli użytkownicy będą instalować z witryny sieci Web, kliknij opcję **z witryny sieci Web** i wprowadź adres URL odpowiadający ścieżce pliku wprowadzonej w poprzednim kroku. Kliknij przycisk **Dalej**. (Ta opcja jest zwykle używana w przypadku określenia adresu FTP jako lokalizacji publikowania. Bezpośrednie pobieranie z usługi FTP nie jest obsługiwane. W związku z tym musisz wprowadzić adres URL tutaj.)

   - Jeśli użytkownicy będą instalować aplikację bezpośrednio z udziału plików, kliknij **ścieżkę UNC lub udział plików** , a następnie kliknij przycisk **dalej**. (Dotyczy to publikowania lokalizacji w postaci *c:\deploy\myapp* lub *\\ \server\myapp* ).

   - Jeśli użytkownicy będą instalować z nośników wymiennych, kliknij **z dysku CD-ROM lub DVD-ROM** , a następnie kliknij przycisk **dalej**.

5. Na stronie **czy aplikacja będzie dostępna w trybie offline?** kliknij odpowiednią opcję:

   - Jeśli chcesz włączyć uruchamianie aplikacji, gdy użytkownik zostanie odłączony od sieci, kliknij przycisk **tak. Ta aplikacja będzie dostępna w trybie online lub offline**. Skrót do menu **Start** zostanie utworzony dla aplikacji.

   - Jeśli chcesz uruchomić aplikację bezpośrednio z lokalizacji publikowania, kliknij przycisk **nie, ta aplikacja jest dostępna tylko w trybie online**. Skrót w menu **Start** nie zostanie utworzony.

     Kliknij przycisk **Dalej** , aby kontynuować.

6. Kliknij przycisk **Zakończ** , aby opublikować aplikację.

    Stan publikowania jest wyświetlany w obszarze powiadomień o stanie.

## <a name="to-publish-to-a-cd-rom-or-dvd-rom"></a>Aby opublikować dysk CD-ROM lub DVD-ROM

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt aplikacji, a następnie kliknij polecenie **Właściwości**.

    Zostanie wyświetlony **Projektant projektu** .

2. Kliknij kartę **Publikuj** , aby otworzyć stronę **Opublikuj** w **projektancie projektu** , a następnie kliknij przycisk **Kreator publikacji** .

    Zostanie wyświetlony Kreator publikacji.

3. Na stronie **gdzie chcesz opublikować aplikację?** wprowadź ścieżkę pliku lub lokalizację FTP, w której aplikacja zostanie opublikowana, na przykład *d:\deploy*. Następnie kliknij przycisk **dalej** , aby kontynuować.

4. Na stronie **jak użytkownicy będą instalować aplikację?** kliknij pozycję z **dysku CD-ROM lub DVD-ROM** , a następnie kliknij przycisk **dalej**.

   > [!NOTE]
   > Jeśli chcesz, aby instalacja była uruchamiana automatycznie po włożeniu dysku CD-ROM do stacji, Otwórz stronę **Opublikuj** w **projektancie projektu** i kliknij przycisk **Opcje** , a następnie w kreatorze **opcji publikacji** wybierz opcję **instalacje CD, automatycznie Rozpocznij instalację po włożeniu dysku CD**.

5. Jeśli aplikacja jest dystrybuowana na dysku CD-ROM, warto udostępnić aktualizacje witryny sieci Web. Na stronie **gdzie aplikacja będzie sprawdzać dostępność aktualizacji?** wybierz opcję aktualizacji:

   - Jeśli aplikacja będzie sprawdzać dostępność aktualizacji, kliknij **aplikację, aby sprawdzić dostępność aktualizacji w następującej lokalizacji** i wprowadzić lokalizację, w której zostaną opublikowane aktualizacje. Może to być lokalizacja pliku, witryna sieci Web lub serwer FTP.

   - Jeśli aplikacja nie będzie sprawdzać dostępności aktualizacji, kliknij **aplikację nie będzie sprawdzać dostępności aktualizacji**.

     Kliknij przycisk **Dalej** , aby kontynuować.

6. Kliknij przycisk **Zakończ** , aby opublikować aplikację.

    Stan publikowania jest wyświetlany w obszarze powiadomień o stanie.

   > [!NOTE]
   > Po zakończeniu publikowania konieczne będzie użycie CD-Rewriter lub DVD-Rewriter do skopiowania plików z lokalizacji określonej w kroku 3 do nośnika CD-ROM lub DVD-ROM.

## <a name="see-also"></a>Zobacz też

- [Zabezpieczenia i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
- [Wdrażanie rozwiązania pakietu Office przy użyciu technologii ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)