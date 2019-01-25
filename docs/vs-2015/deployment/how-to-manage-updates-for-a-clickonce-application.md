---
title: 'Instrukcje: Zarządzanie aktualizacjami dla aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9781745af5d65d497652002c9afcd8132058ffb6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790685"
---
# <a name="how-to-manage-updates-for-a-clickonce-application"></a>Instrukcje: Zarządzanie aktualizacjami dla aplikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacje można sprawdzić dostępność aktualizacji automatycznie lub programowo. Jako deweloper masz dużą elastyczność określania moment i sposób aktualizacji są sprawdzane, czy aktualizacje są obowiązkowe i którym aplikacja ma sprawdzać dostępność aktualizacji.  
  
 Można skonfigurować aplikację, aby sprawdzał dostępność aktualizacji, automatycznie przed uruchomieniem aplikacji lub w ustalonych odstępach czasu, po uruchomieniu aplikacji. Ponadto można określić minimalnej wymaganej wersji; oznacza to jeśli jego wersja jest starsza niż wymagana wersja jest instalowana aktualizacja.  
  
 Można skonfigurować aplikację, aby wyszukać aktualizacje programowo oparte na zdarzenie, takie jak żądania użytkownika. W procedurze "Aby wyszukać aktualizacje programowo" w tym temacie pokazano, jak należy napisać kod, który używa <xref:System.Deployment.Application.ApplicationDeployment> klasy, aby sprawdzał dostępność aktualizacji na podstawie zdarzenia.  
  
 Możesz również wdrożyć aplikację z jednej lokalizacji i zaktualizować go z innego. Zapoznaj się z procedurą "Aby określić lokalizację inną aktualizację."  
  
 Aby uzyskać więcej informacji, zobacz [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).  
  
 Zachowanie aktualizacji są zarządzane w **aktualizacje aplikacji** okno dialogowe, dostępnym **Publikuj** strony **projektanta projektu.**  
  
### <a name="to-check-for-updates-before-the-application-starts"></a>Aby sprawdzić dostępność aktualizacji, przed uruchomieniem aplikacji  
  
1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **Publikuj** kartę.  
  
3.  Kliknij przycisk **aktualizacje** przycisk, aby otworzyć **aktualizacje aplikacji** okno dialogowe.  
  
4.  W **aktualizacje aplikacji** okna dialogowego pole, upewnij się, że **aplikacja ma sprawdzać dostępność aktualizacji** pole wyboru jest zaznaczone.  
  
5.  W **wybierz, kiedy aplikacja ma sprawdzać dostępność aktualizacji** zaznacz **przed uruchomieniem aplikacji**. Daje to gwarancję, że użytkownicy zawsze podłączone do sieci uruchomić aplikację z najnowszymi aktualizacjami.  
  
### <a name="to-check-for-updates-in-the-background-after-the-application-starts"></a>Aby sprawdzić dostępność aktualizacji w tle, po uruchomieniu aplikacji  
  
1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **Publikuj** kartę.  
  
3.  Kliknij przycisk **aktualizacje** przycisk, aby otworzyć **aktualizacje aplikacji** okno dialogowe.  
  
4.  W **aktualizacje aplikacji** okna dialogowego pole, upewnij się, że pole wyboru **aplikacja ma sprawdzać dostępność aktualizacji** jest zaznaczone.  
  
5.  W **wybierz, kiedy aplikacja powinna sprawdzać, czy aktualizacje sekcji**, wybierz opcję **po uruchomieniu aplikacji**. Aplikacja rozpocznie się szybciej dzięki temu, a następnie go będzie sprawdzać dostępność aktualizacji w tle, a tylko Powiadom użytkownika, gdy aktualizacja jest dostępna. Po zainstalowaniu aktualizacji nie zostały zastosowane do ponownego uruchomienia aplikacji.  
  
6.  W **Określ, jak często aplikacja ma sprawdzać dostępność aktualizacji** sekcji, wybierz opcję **Sprawdź za każdym razem, gdy aplikacja zostanie uruchomiona** (ustawienie domyślne) lub **Sprawdź każdy** a następnie wprowadź interwał liczby i czasu.  
  
### <a name="to-specify-a-minimum-required-version-for-the-application"></a>Do określenia minimalnej wymaganej wersji aplikacji  
  
1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **Publikuj** kartę.  
  
3.  Kliknij przycisk **aktualizacje** przycisk, aby otworzyć **aktualizacje aplikacji** okno dialogowe.  
  
4.  W **aktualizacje aplikacji** okna dialogowego pole, upewnij się, że **aplikacja ma sprawdzać dostępność aktualizacji** pole wyboru jest zaznaczone.  
  
5.  Wybierz **określanie minimalnej wymaganej wersji tej aplikacji** pole wyboru, a następnie wprowadź **głównych**, **pomocnicza**, **kompilacji**i  **Poprawka** liczb dla aplikacji.  
  
### <a name="to-specify-a-different-update-location"></a>Aby określić lokalizację inną aktualizację  
  
1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **Publikuj** kartę.  
  
3.  Kliknij przycisk **aktualizacje** przycisk, aby otworzyć **aktualizacje aplikacji** okno dialogowe.  
  
4.  W **aktualizacje aplikacji** okna dialogowego pole, upewnij się, że **aplikacja ma sprawdzać dostępność aktualizacji** pole wyboru jest zaznaczone.  
  
5.  W **zaktualizować lokalizację** wprowadź lokalizacji aktualizacji za pomocą w pełni kwalifikowanym adresem URL, przy użyciu formatu http://Hostname/ApplicationName, lub ścieżkę UNC w formacie \\\Server\ApplicationName lub kliknij przycisk **Przeglądaj** przycisku Przeglądaj w poszukiwaniu lokalizacji aktualizacji.  
  
### <a name="to-check-for-updates-programmatically"></a>Aby wyszukać aktualizacje programowo  
  
1.  Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **Publikuj** kartę.  
  
3.  Kliknij przycisk **aktualizacje** przycisk, aby otworzyć **aktualizacje aplikacji** okno dialogowe.  
  
4.  W **aktualizacje aplikacji** okna dialogowego pole, upewnij się, że **aplikacja ma sprawdzać dostępność aktualizacji** pole wyboru jest wyczyszczone. (Opcjonalnie można wybrać to pole wyboru w celu wyszukania aktualizacji programowo, a także umożliwić środowiska uruchomieniowego ClickOnce, Sprawdź aktualizacje automatycznie.)  
  
5.  W **zaktualizować lokalizację** wprowadź lokalizacji aktualizacji za pomocą w pełni kwalifikowanym adresem URL, przy użyciu formatu http://Hostname/ApplicationName, lub ścieżkę UNC w formacie \\\Server\ApplicationName lub kliknij przycisk **Przeglądaj** przycisku Przeglądaj w poszukiwaniu lokalizacji aktualizacji. Lokalizacja aktualizacji jest, gdzie aplikacja będzie szukać zaktualizowaną wersję samego.  
  
6.  Utwórz przycisk, element menu lub innego elementu interfejsu użytkownika w formularzu Windows, która będzie wybierać użytkowników, aby sprawdzał dostępność aktualizacji. Z tego elementu procedura obsługi zdarzeń Wywołaj metodę, aby wyszukać i zainstalować aktualizacje. Można znaleźć przykład Visual Basic i Visual C# kod dla metody w [jak: Sprawdzanie aktualizacji aplikacji, programowo przy użyciu wdrażania interfejsu API ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md).  
  
7.  Tworzenie aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Deployment.Application.ApplicationDeployment>   
 [Okno dialogowe aktualizacji aplikacji](http://msdn.microsoft.com/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f)   
 [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)   
 [Instrukcje: Publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Instrukcje: Sprawdzanie aktualizacji aplikacji w sposób programowy za pomocą interfejsu API wdrażania ClickOnce](../deployment/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api.md)
