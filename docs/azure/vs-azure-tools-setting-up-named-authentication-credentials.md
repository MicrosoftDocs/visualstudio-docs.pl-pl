---
title: Skonfiguruj poświadczenia uwierzytelniania o nazwie | Dokumentacja firmy Microsoft
description: Dowiedz się, jak Podaj poświadczenia, które Visual Studio może użyć do uwierzytelniania żądań do platformy Azure, dzięki czemu można opublikować aplikację na platformie Azure z programu Visual Studio lub monitorowanie istniejącej usługi w chmurze.
author: ghogen
manager: douge
assetId: 61570907-42a1-40e8-bcd6-952b21a55786
ms.prod: visual-studio-dev15
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/11/2017
ms.author: ghogen
ms.openlocfilehash: 62f95253b894e27cce7131bf387aacb5dd0f6903
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2018
ms.locfileid: "51000269"
---
# <a name="set-up-named-authentication-credentials"></a>Konfigurowanie nazwanych poświadczeń uwierzytelniania

Aby opublikować aplikację na platformie Azure lub do monitorowania istniejącej usługi w chmurze, program Visual Studio wymaga poświadczeń do uwierzytelniania żądań do systemu Azure, a mianowicie swój identyfikator subskrypcji platformy Azure i prawidłowy certyfikat X.509 v3 kluczem do co najmniej 2048 bitów. Te poświadczenia przy użyciu jednej z następujących metod:

- W programie Visual Studio wybierz **Widok > Eksploratora serwera**, kliknij prawym przyciskiem myszy **Azure** węzeł **nawiązywanie połączenia z subskrypcją platformy Microsoft Azure**i zaloguj się.
- Utwórz plik subskrypcji (`.publishsettings`), który zawiera klucz publiczny dla certyfikatu. Plik subskrypcji może zawierać poświadczenia dla więcej niż jedną subskrypcję, zgodnie z opisem w tym artykule.

Uwaga: te poświadczenia są inne niż poświadczenia używane do uwierzytelniania żądań do usługi Azure storage.

## <a name="create-a-subscription-file"></a>Utwórz plik subskrypcji

W Eksploratorze serwera, kliknij prawym przyciskiem myszy **Azure** a następnie wybierz węzeł **subskrypcji filtru i Zarządzaj**. Następnie wybierz pozycję **certyfikaty** kartę, a następnie wykonaj jedną z następujących czynności:

- Wybierz **importu** otworzyć **subskrypcji platformy Microsoft Azure Import** okno dialogowe. Wybierz **pobierania pliku subskrypcji** połączyć, a w przeglądarce Zapisz pobrany plik do lokalizacji tymczasowej. W oknie dialogowym Przejdź do lokalizacji pobierania, a następnie zaimportuj go do użycia w przypadku uwierzytelniania.
- Wybierz aktywną subskrypcję i wybierz pozycję **Edytuj**, która otwiera okno dialogowe, w którym można edytować istniejącą subskrypcję do użycia w przypadku uwierzytelniania.
- Wybierz **New** otworzyć **nową subskrypcję** okna dialogowego pole, a następnie podaj wymagane szczegóły. Aby przekazać certyfikat z Twoją chmurą usługi są podane w oknie dialogowym Zaloguj się do witryny Azure portal, przejdź do usługi w chmurze, wybierz opcję **Ustawienia > certyfikaty zarządzania**, wybierz opcję **przekazywanie**, następnie Określ ścieżkę do `.cer` pliku.

Jeśli chcesz samodzielnie utworzyć certyfikat, mogą odwoływać się do instrukcji w [tworzenie i przekazywanie certyfikatów zarządzania dla platformy Azure](https://msdn.microsoft.com/library/windowsazure/gg551722.aspx) a następnie ręcznie przekazać certyfikat do [witryny Azure portal](https://portal.azure.com/).

## <a name="next-steps"></a>Następne kroki

- [Ogólne omówienie aplikacji sieci Web](https://docs.microsoft.com/azure/app-service/)
- [Wdrażanie aplikacji w usłudze Azure App Service](https://docs.microsoft.com/azure/app-service/app-service-deploy-local-git) 
- [Wdrażanie zadań Webjob za pomocą programu Visual Studio](https://docs.microsoft.com/azure/app-service/websites-dotnet-deploy-webjobs)
- [Tworzenie i wdrażanie usługi w chmurze](https://docs.microsoft.com/azure/cloud-services/cloud-services-how-to-create-deploy-portal)