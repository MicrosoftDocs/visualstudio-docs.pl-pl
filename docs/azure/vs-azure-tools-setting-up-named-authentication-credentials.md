---
title: Konfigurowanie poświadczeń uwierzytelniania nazwanego | Microsoft Docs
description: Dowiedz się, jak podać poświadczenia, których program Visual Studio może używać do uwierzytelniania żądań na platformie Azure, dzięki czemu możesz opublikować aplikację na platformie Azure z poziomu programu Visual Studio lub monitorować istniejącą usługę w chmurze.
author: ghogen
manager: jillfra
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 059ac654f13ed833e80464e74e18a6cb8b0f8132
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2020
ms.locfileid: "94902002"
---
# <a name="set-up-named-authentication-credentials"></a>Konfigurowanie nazwanych poświadczeń uwierzytelniania

Aby opublikować aplikację na platformie Azure lub monitorować istniejącą usługę w chmurze, program Visual Studio wymaga poświadczeń do uwierzytelniania żądań na platformie Azure, a mianowicie identyfikatora subskrypcji platformy Azure i prawidłowego certyfikatu X. 509 v3 z kluczem co najmniej 2048 bitów. Te poświadczenia są podane za pomocą jednej z następujących metod:

- W programie Visual Studio wybierz pozycję **wyświetl > Eksplorator serwera**, kliknij prawym przyciskiem myszy węzeł **platformy Azure** , wybierz pozycję **Połącz z subskrypcją Microsoft Azure** i zaloguj się.
- Utwórz plik subskrypcji ( `.publishsettings` ), który zawiera klucz publiczny certyfikatu. Plik subskrypcji może zawierać poświadczenia dla więcej niż jednej subskrypcji, zgodnie z opisem w tym artykule.

Uwaga: te poświadczenia różnią się od poświadczeń używanych do uwierzytelniania żądań w usługach Azure Storage.

## <a name="create-a-subscription-file"></a>Utwórz plik subskrypcji

W Eksplorator serwera kliknij prawym przyciskiem myszy węzeł **platformy Azure** i wybierz pozycję **Zarządzaj i Filtruj subskrypcje**. Następnie wybierz kartę **Certyfikaty** , a następnie wykonaj jedną z następujących czynności:

- Wybierz pozycję **Importuj** , aby otworzyć okno dialogowe **Importuj subskrypcje Microsoft Azure** . Wybierz łącze **Pobierz plik subskrypcji** , a w przeglądarce Zapisz pobrany plik w lokalizacji tymczasowej. W oknie dialogowym przejdź do lokalizacji pobierania, a następnie zaimportuj ją do użycia podczas uwierzytelniania.
- Wybierz aktywną subskrypcję i wybierz pozycję **Edytuj**, aby otworzyć okno dialogowe, w którym można edytować istniejącą subskrypcję do użycia w ramach uwierzytelniania.
- Wybierz pozycję **Nowy** , aby otworzyć okno dialogowe **Nowa subskrypcja** i podać wymagane szczegóły. Aby przekazać certyfikat do usługi w chmurze w oknie dialogowym, zaloguj się do Azure Portal, przejdź do usługi w chmurze, wybierz pozycję **ustawienia > certyfikaty zarządzania**, wybierz pozycję **Przekaż**, a następnie określ ścieżkę do `.cer` pliku.

Jeśli chcesz samodzielnie utworzyć certyfikat, możesz zapoznać się z instrukcjami w temacie [Tworzenie i przekazywanie certyfikatu zarządzania dla platformy Azure](/azure/cloud-services/cloud-services-certs-create) , a następnie ręczne przekazywanie certyfikatu do [Azure Portal](https://portal.azure.com/).

## <a name="next-steps"></a>Następne kroki

- [Ogólne omówienie Web Apps](/azure/app-service/)
- [Wdróż aplikację w usłudze Azure App Service](/azure/app-service/app-service-deploy-local-git)
- [Wdrażanie zadań WebJobs za pomocą programu Visual Studio](/azure/app-service/websites-dotnet-deploy-webjobs)
- [Tworzenie i wdrażanie usługi w chmurze](/azure/cloud-services/cloud-services-how-to-create-deploy-portal)
