---
title: Wdrażanie aplikacji ClickOnce bez ponownego podpisywania
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, deploying without resigning
- ClickOnce deployment, without resigning
- application updates, ClickOnce
- update location [ClickOnce]
- deploymentProvider tag
- manifests [ClickOnce]
ms.assetid: 1218a98d-1ad5-4eef-95dd-0e0b3c44168c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89e1d7970b26d5ba9bd49090362a6a4e8c09f78d
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395323"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Wdrażanie aplikacji ClickOnce do testowania i tworzenia serwerów bez rezygnacji
W tym artykule opisano funkcję ClickOnce wprowadzone w .NET Framework w wersji 3.5, który umożliwia wdrażanie aplikacji ClickOnce z wielu lokalizacji sieciowych bez ponownego podpisywania lub zmiany Manifesty ClickOnce.

> [!NOTE]
> Rezygnacja jest nadal preferowaną metodą wdrażania nowych wersji aplikacji. Jeśli to możliwe, użyj metody rezygnacji. Aby uzyskać więcej informacji, zobacz [ *Mage.exe* (Manifest Generation and Editing Tool)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

 Deweloperzy zewnętrzni i dostawcy oprogramowania mogą zdecydować się na tę funkcję, ułatwiając klientom aktualizowanie aplikacji. Ta funkcja może być używana w następujących sytuacjach:

- Podczas aktualizowania aplikacji, a nie dla pierwszej instalacji aplikacji.

- Gdy na komputerze jest tylko jedna konfiguracja aplikacji. Na przykład jeśli aplikacja jest skonfigurowana do wskazywała dwie różne bazy danych, nie można użyć tej funkcji.

## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>Wykluczanie wdrożeniaProvider z manifestów wdrażania
 W programie .NET Framework 2.0 i .NET Framework 3.0 każda aplikacja ClickOnce instaluje `deploymentProvider` się w systemie w celu zapewnienia dostępności w trybie offline musi zawierać listę w manifeście wdrożenia. Jest `deploymentProvider` często określane jako lokalizacja aktualizacji; jest to miejsce, w którym ClickOnce sprawdza aktualizacje aplikacji. To wymaganie, wraz z koniecznością wydawców aplikacji do podpisania ich wdrożeń, utrudnił firmie zaktualizować clickonce aplikacji od dostawcy lub innej firmy trzeciej. Utrudnia to również wdrożenie tej samej aplikacji z wielu lokalizacji w tej samej sieci.

 Ze zmianami, które zostały wprowadzone do ClickOnce w .NET Framework 3.5, jest możliwe dla strony trzeciej, aby zapewnić ClickOnce aplikacji do innej organizacji, która może następnie wdrożyć aplikację w swojej sieci.

 Aby skorzystać z tej funkcji, deweloperzy aplikacji ClickOnce należy wykluczyć `deploymentProvider` z ich manifestów wdrażania. To wymaganie oznacza, `-providerUrl` że należy wykluczyć argument podczas tworzenia manifestów wdrażania z Mage.exe. Lub, jeśli generujesz manifesty wdrażania za pomocą programu MageUI.exe, należy upewnić się, że pole tekstowe **Lokalizacja uruchamiania** na karcie **Manifest aplikacji** pozostaje puste.

## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider i aktualizacje aplikacji
 Począwszy od .NET Framework 3.5, nie `deploymentProvider` trzeba już określić w manifeście wdrożenia w celu wdrożenia clickonce aplikacji dla użycia w trybie online i offline. Ta zmiana obsługuje scenariusz, w którym należy spakować i podpisać wdrożenie samodzielnie, ale zezwolić innym firmom na wdrożenie aplikacji za pośrednictwem swoich sieci.

 Ważnym punktem do zapamiętania jest `deploymentProvider` to, że aplikacje, które wykluczają nie `deploymentProvider` można zmienić ich lokalizacji instalacji podczas aktualizacji, dopóki nie wysyła aktualizacji, która zawiera tag ponownie.

 Oto dwa przykłady, aby wyjaśnić tę kwestię. W pierwszym przykładzie publikujesz aplikację ClickOnce, która nie `deploymentProvider` ma tagu, i prosisz użytkowników o zainstalowanie go z `http://www.adatum.com/MyApplication/`programu . Jeśli zdecydujesz, że chcesz opublikować następną `http://subdomain.adatum.com/MyApplication/`aktualizację aplikacji z programu , nie ma możliwości `http://www.adatum.com/MyApplication/`oznaczenia tego w manifeście wdrażania, który znajduje się w pliku . Możesz wykonać jedną z dwóch rzeczy:

- Powiedz użytkownikom, aby odinstalowali poprzednią wersję i zainstaluj nową wersję z nowej lokalizacji.

- Dołącz aktualizację, `http://www.adatum.com/MyApplication/` która `deploymentProvider` zawiera `http://www.adatum.com/MyApplication/`punktowanie . Następnie zwolnij kolejną `deploymentProvider` aktualizację `http://subdomain.adatum.com/MyApplication/`później ze wskazaniem .

  W drugim przykładzie można opublikować ClickOnce `deploymentProvider`aplikacji, która określa , a następnie zdecydujesz się go usunąć. Po pobraniu `deploymentProvider` nowej wersji bez pobierania do klientów, nie można przekierować ścieżkę `deploymentProvider` używaną do aktualizacji, dopóki nie wydasz wersji aplikacji, która została przywrócona. Podobnie jak w `deploymentProvider` pierwszym przykładzie, musi początkowo wskazywać bieżącą lokalizację aktualizacji, a nie nową lokalizację. W takim przypadku, jeśli spróbujesz `deploymentProvider` wstawić, który odwołuje się do `http://subdomain.adatum.com/MyApplication/`, następna aktualizacja kończy się niepowodzeniem.

## <a name="create-a-deployment"></a>Tworzenie wdrożenia
 Aby uzyskać wskazówki krok po kroku dotyczące tworzenia wdrożeń, które można wdrożyć z różnych lokalizacji sieciowych, zobacz [Przewodnik: Ręczne wdrażanie aplikacji ClickOnce, która nie wymaga ponownego podpisywania i która zachowuje informacje o znakowaniu.](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)

## <a name="see-also"></a>Zobacz też
- [*Mage.exe* (narzędzie do generowania manifestów i edycji)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [*MageUI.exe* (narzędzie do generowania manifestu i edycji, klient graficzny)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
