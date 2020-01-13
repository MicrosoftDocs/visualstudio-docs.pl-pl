---
title: Konfigurowanie poświadczeń uwierzytelniania nazwanego | Microsoft Docs
description: Dowiedz się, jak podać poświadczenia, których program Visual Studio może używać do uwierzytelniania żądań na platformie Azure, dzięki czemu możesz opublikować aplikację na platformie Azure z poziomu programu Visual Studio lub monitorować istniejącą usługę w chmurze.
author: ghogen
manager: jillfra
assetId: 61570907-42a1-40e8-bcd6-952b21a55786
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 27837390306ad29da55c7c5262ecd8fa6bcf75b3
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2020
ms.locfileid: "75917367"
---
# <a name="set-up-named-authentication-credentials"></a>Konfigurowanie nazwanych poświadczeń uwierzytelniania

Aby opublikować aplikację na platformie Azure lub monitorować istniejącą usługę w chmurze, program Visual Studio wymaga poświadczeń do uwierzytelniania żądań na platformie Azure, a mianowicie identyfikatora subskrypcji platformy Azure i prawidłowego certyfikatu X. 509 v3 z kluczem co najmniej 2048 bitów. Te poświadczenia są podane za pomocą jednej z następujących metod:

- W programie Visual Studio wybierz pozycję **wyświetl > Eksplorator serwera**, kliknij prawym przyciskiem myszy węzeł **platformy Azure** , wybierz pozycję **Połącz z subskrypcją Microsoft Azure**i zaloguj się.
- Utwórz plik subskrypcji (`.publishsettings`), który zawiera klucz publiczny certyfikatu. Plik subskrypcji może zawierać poświadczenia dla więcej niż jednej subskrypcji, zgodnie z opisem w tym artykule.

Uwaga: te poświadczenia różnią się od poświadczeń używanych do uwierzytelniania żądań w usługach Azure Storage.

## <a name="create-a-subscription-file"></a>Utwórz plik subskrypcji

W Eksplorator serwera kliknij prawym przyciskiem myszy węzeł **platformy Azure** i wybierz pozycję **Zarządzaj i Filtruj subskrypcje**. Następnie wybierz kartę **Certyfikaty** , a następnie wykonaj jedną z następujących czynności:

- Wybierz pozycję **Importuj** , aby otworzyć okno dialogowe **Importuj subskrypcje Microsoft Azure** . Wybierz łącze **Pobierz plik subskrypcji** , a w przeglądarce Zapisz pobrany plik w lokalizacji tymczasowej. W oknie dialogowym przejdź do lokalizacji pobierania, a następnie zaimportuj ją do użycia podczas uwierzytelniania.
- Wybierz aktywną subskrypcję i wybierz pozycję **Edytuj**, aby otworzyć okno dialogowe, w którym można edytować istniejącą subskrypcję do użycia w ramach uwierzytelniania.
- Wybierz pozycję **Nowy** , aby otworzyć okno dialogowe **Nowa subskrypcja** i podać wymagane szczegóły. Aby przekazać certyfikat do usługi w chmurze w oknie dialogowym, zaloguj się do Azure Portal, przejdź do usługi w chmurze, wybierz pozycję **ustawienia > certyfikaty zarządzania**, wybierz pozycję **Przekaż**, a następnie określ ścieżkę do pliku `.cer`.

Jeśli chcesz samodzielnie utworzyć certyfikat, możesz zapoznać się z instrukcjami w temacie [Tworzenie i przekazywanie certyfikatu zarządzania dla platformy Azure](https://msdn.microsoft.com/library/windowsazure/gg551722.aspx) , a następnie ręczne przekazywanie certyfikatu do [Azure Portal](https://portal.azure.com/).

## <a name="next-steps"></a>Następne kroki

- [Ogólne omówienie Web Apps](/azure/app-service/)
- [Wdróż aplikację w usłudze Azure App Service](/azure/app-service/app-service-deploy-local-git) 
- [Wdrażanie zadań WebJobs za pomocą programu Visual Studio](/azure/app-service/websites-dotnet-deploy-webjobs)
- [Tworzenie i wdrażanie usługi w chmurze](/azure/cloud-services/cloud-services-how-to-create-deploy-portal)