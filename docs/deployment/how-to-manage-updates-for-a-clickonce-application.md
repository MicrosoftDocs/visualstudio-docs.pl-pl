---
title: Jak zarządzać aktualizacjami aplikacji ClickOnce | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Update
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, managing applications
- ClickOnce deployment, updates
- updating data, ClickOnce
- application updates
ms.assetid: a3f23f05-e7f1-4620-b23c-2d68f9643684
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 534171d9145d0a21fee7f8831e9a6355e6079cbd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382357"
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>Instrukcje: Zarządzanie aktualizacjami aplikacji ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje mogą automatycznie sprawdzać dostępność aktualizacji lub programowo. Jako deweloper możesz określić, kiedy i w jaki sposób testy aktualizacji są wykonywane, czy aktualizacje są obowiązkowe i gdzie aplikacja ma sprawdzać dostępność aktualizacji.

 Można skonfigurować aplikację, aby automatycznie sprawdzać dostępność aktualizacji przed uruchomieniem aplikacji, lub w ustalonych odstępach czasu po uruchomieniu aplikacji. Dodatkowo można określić minimalną wymaganą wersję; oznacza to, że aktualizacja jest zainstalowana, jeśli wersja użytkownika jest niższa niż wymagana wersja.

 Można skonfigurować aplikację, aby program mógł sprawdzać dostępność aktualizacji na podstawie zdarzenia, takiego jak żądanie użytkownika. Procedura "aby wyszukiwać aktualizacje programowo" w tym temacie pokazuje, w jaki sposób napisać kod, który używa <xref:System.Deployment.Application.ApplicationDeployment> klasy do sprawdzania dostępności aktualizacji na podstawie zdarzenia.

 Możesz również wdrożyć aplikację z jednej lokalizacji i zaktualizować ją z innej. Zobacz procedurę "aby określić inną lokalizację aktualizacji".

 Aby uzyskać więcej informacji, zobacz [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

 Zachowaniem aktualizacji zarządza się w oknie dialogowym **aktualizacje aplikacji** dostępnym na stronie **Publikuj** w **projektancie projektu.**

### <a name="to-check-for-updates-before-the-application-starts"></a>Aby sprawdzić dostępność aktualizacji przed uruchomieniem aplikacji

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **Publikowanie** .

3. Kliknij przycisk **aktualizacje** , aby otworzyć okno dialogowe **aktualizacje aplikacji** .

4. W oknie dialogowym **aktualizacje aplikacji** upewnij się, że jest zaznaczone pole wyboru **aplikacja powinna sprawdzać dostępność aktualizacji** .

5. W sekcji **Wybierz, kiedy aplikacja ma sprawdzać dostępność aktualizacji** wybierz **przed uruchomieniem aplikacji**. Dzięki temu użytkownicy połączeni z siecią zawsze będą uruchamiać aplikacje z najnowszymi aktualizacjami.

### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>Aby sprawdzić dostępność aktualizacji w tle po uruchomieniu aplikacji

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **Publikowanie** .

3. Kliknij przycisk **aktualizacje** , aby otworzyć okno dialogowe **aktualizacje aplikacji** .

4. W oknie dialogowym **aktualizacje aplikacji** upewnij się, że zaznaczone jest pole wyboru **aplikacja powinna sprawdzać dostępność aktualizacji** .

5. W **sekcji Wybierz, kiedy aplikacja ma sprawdzać dostępność aktualizacji**wybierz pozycję **po uruchomieniu aplikacji**. Aplikacja zacznie szybciej w ten sposób, a następnie będzie sprawdzać dostępność aktualizacji w tle, a następnie powiadamia użytkownika tylko o dostępności aktualizacji. Po zainstalowaniu aktualizacje zaczną obowiązywać dopiero po ponownym uruchomieniu aplikacji.

6. W sekcji **Określ, jak często aplikacja ma sprawdzać dostępność aktualizacji** zaznacz opcję **sprawdzaj przy każdym uruchomieniu aplikacji** (wartość domyślna) lub **Sprawdzaj co** i wprowadź liczbę i przedział czasu.

### <a name="to-specify-a-minimum-required-version-for-the-application"></a>Aby określić minimalną wersję wymaganą dla aplikacji

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **Publikowanie** .

3. Kliknij przycisk **aktualizacje** , aby otworzyć okno dialogowe **aktualizacje aplikacji** .

4. W oknie dialogowym **aktualizacje aplikacji** upewnij się, że jest zaznaczone pole wyboru **aplikacja powinna sprawdzać dostępność aktualizacji** .

5. Zaznacz pole **wyboru Określ minimalną wersję wymaganą dla tej aplikacji** , a następnie wprowadź numery **Główne**, **pomocnicze**, **kompilacje**i **poprawki** dla aplikacji.

### <a name="to-specify-a-different-update-location"></a>Aby określić inną lokalizację aktualizacji

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **Publikowanie** .

3. Kliknij przycisk **aktualizacje** , aby otworzyć okno dialogowe **aktualizacje aplikacji** .

4. W oknie dialogowym **aktualizacje aplikacji** upewnij się, że jest zaznaczone pole wyboru **aplikacja powinna sprawdzać dostępność aktualizacji** .

5. W polu **Lokalizacja aktualizacji** wprowadź lokalizację aktualizacji z w pełni kwalifikowanym adresem URL, używając formatu *http://Hostname/ApplicationName* lub ścieżki UNC przy użyciu formatu * \\ \Server\ApplicationName*, lub kliknij przycisk **Przeglądaj** , aby przejść do lokalizacji aktualizacji.

### <a name="to-check-for-updates-programmatically"></a>Aby programowo sprawdzić dostępność aktualizacji

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Kliknij kartę **Publikowanie** .

3. Kliknij przycisk **aktualizacje** , aby otworzyć okno dialogowe **aktualizacje aplikacji** .

4. W oknie dialogowym **aktualizacje aplikacji** upewnij się, że pole wyboru **aplikacja powinna sprawdzać dostępność aktualizacji** , jest wyczyszczone. (Opcjonalnie możesz zaznaczyć to pole wyboru, aby wyszukać aktualizacje programowo, a także umożliwić automatyczne sprawdzanie aktualizacji w środowisku uruchomieniowym ClickOnce).

5. W polu **Lokalizacja aktualizacji** wprowadź lokalizację aktualizacji z w pełni kwalifikowanym adresem URL, używając formatu *http://Hostname/ApplicationName* lub ścieżki UNC przy użyciu formatu * \\ \Server\ApplicationName*, lub kliknij przycisk **Przeglądaj** , aby przejść do lokalizacji aktualizacji. Lokalizacja aktualizacji polega na tym, że aplikacja będzie szukać zaktualizowanej wersji.

6. Utwórz przycisk, element menu lub inny element interfejsu użytkownika w formularzu systemu Windows, który użytkownicy będą wybierać w celu sprawdzenia dostępności aktualizacji. Z procedury obsługi zdarzeń tego elementu Wywołaj metodę, aby sprawdzić i zainstalować aktualizacje. Przykładowy kod Visual Basic i Visual C# można znaleźć w tej metodzie [: sprawdzanie aktualizacji aplikacji programowo przy użyciu interfejsu API wdrażania ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md).

7. Kompiluj aplikację.

## <a name="see-also"></a>Zobacz też
- <xref:System.Deployment.Application.ApplicationDeployment>
- [Okno dialogowe aktualizacje aplikacji](/previous-versions/visualstudio/visual-studio-2010/axw1fa38(v=vs.100))
- [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)
- [Jak: sprawdzanie aktualizacji aplikacji programowo przy użyciu interfejsu API wdrażania ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)
