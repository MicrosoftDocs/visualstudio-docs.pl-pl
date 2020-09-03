---
title: Wdróż aplikacje ClickOnce bez ponownego podpisywania
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395323"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Wdrażaj aplikacje ClickOnce do testowania i serwerów produkcyjnych bez ponownego podpisywania
W tym artykule opisano funkcję ClickOnce wprowadzoną w .NET Framework w wersji 3,5, która umożliwia wdrażanie aplikacji ClickOnce z wielu lokalizacji sieciowych bez ponownego podpisywania lub zmiany manifestów ClickOnce.

> [!NOTE]
> Rejestracja jest nadal preferowaną metodą wdrażania nowych wersji aplikacji. Za każdym razem, gdy to możliwe, użyj metody podpisywania. Aby uzyskać więcej informacji, zobacz [ *Mage.exe* (narzędzie tworzenia i edycji manifestów)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

 Deweloperzy innych firm i dostawcy oprogramowania mogą zrezygnować z tej funkcji, ułatwiając klientom aktualizowanie aplikacji. Ta funkcja może być używana w następujących sytuacjach:

- Podczas aktualizacji aplikacji, a nie dla pierwszej instalacji aplikacji.

- Jeśli na komputerze jest tylko jedna konfiguracja aplikacji. Jeśli na przykład aplikacja jest skonfigurowana tak, aby wskazywała dwie różne bazy danych, nie można użyć tej funkcji.

## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>Wyklucz deploymentProvider z manifestów wdrożenia
 W .NET Framework 2,0 i .NET Framework 3,0 wszystkie aplikacje ClickOnce instalowane w systemie w celu zapewnienia dostępności w trybie offline muszą wystawić listę a `deploymentProvider` w manifeście wdrożenia. `deploymentProvider`Jest często określana jako lokalizacja aktualizacji; jest to lokalizacja, w której Technologia ClickOnce sprawdza dostępność aktualizacji aplikacji. Ten wymóg, wraz z potrzebą wydawcy aplikacji do podpisywania wdrożeń, utrudnia firmie aktualizację aplikacji ClickOnce od dostawcy lub innej osoby trzeciej. Utrudnia to również wdrażanie tej samej aplikacji z wielu lokalizacji w tej samej sieci.

 Ze zmianami wprowadzonymi w ramach technologii ClickOnce w .NET Framework 3,5, istnieje możliwość, że firma trzecia udostępni aplikację ClickOnce innej organizacji, która następnie może wdrożyć aplikację w własnej sieci.

 Aby móc korzystać z tej funkcji, deweloperzy aplikacji ClickOnce muszą wykluczyć `deploymentProvider` z ich manifestów wdrożenia. To wymaganie oznacza, że należy wykluczyć `-providerUrl` argument podczas tworzenia manifestów wdrożenia za pomocą Mage.exe. Lub, jeśli są generowane manifesty wdrożenia z MageUI.exe, należy upewnić się, że pole tekstowe **Lokalizacja uruchamiania** na karcie **manifest aplikacji** jest puste.

## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider i aktualizacje aplikacji
 Począwszy od .NET Framework 3,5, nie trzeba już określać `deploymentProvider` w manifeście wdrożenia, aby można było wdrożyć aplikację ClickOnce zarówno w trybie online, jak i offline. Ta zmiana obsługuje scenariusz, w którym konieczne jest samodzielne pakowanie i podpisywanie wdrożenia, ale umożliwienie innym firmom wdrożenia aplikacji za pośrednictwem swoich sieci.

 Ważne jest, aby pamiętać, że aplikacje, które `deploymentProvider` nie mogą zmienić ich lokalizacji instalacji podczas aktualizacji, do momentu wysłania aktualizacji, która zawiera `deploymentProvider` znacznik ponownie.

 Poniżej przedstawiono dwa przykłady do wyjaśnienia tego punktu. W pierwszym przykładzie należy opublikować aplikację ClickOnce, która nie ma `deploymentProvider` tagu, i poprosił użytkowników o ich zainstalowanie `http://www.adatum.com/MyApplication/` . Jeśli zdecydujesz, że chcesz opublikować następną aktualizację aplikacji z programu `http://subdomain.adatum.com/MyApplication/` , nie ma możliwości jej określenia w manifeście wdrażania, który znajduje się w `http://www.adatum.com/MyApplication/` . Można wykonać jedną z dwóch czynności:

- Poinformuj użytkowników, aby odinstalował poprzednią wersję, i zainstaluj nową wersję z nowej lokalizacji.

- Uwzględnij aktualizację `http://www.adatum.com/MyApplication/` , która zawiera `deploymentProvider` wskazanie elementu `http://www.adatum.com/MyApplication/` . Następnie zwolnij kolejną aktualizację później, `deploymentProvider` wskazując polecenie `http://subdomain.adatum.com/MyApplication/` .

  W drugim przykładzie należy opublikować aplikację ClickOnce, która określa `deploymentProvider` , a następnie zdecydować o jej usunięciu. Gdy nowa wersja nie `deploymentProvider` zostanie pobrana do klientów, nie można przekierować ścieżki używanej do aktualizacji do momentu wydania wersji aplikacji, która została `deploymentProvider` przywrócona. Podobnie jak w przypadku pierwszego przykładu, `deploymentProvider` musi początkowo wskazywać bieżącą lokalizację aktualizacji, a nie nową lokalizację. W takim przypadku próba wstawienia elementu `deploymentProvider` , który odwołuje się do programu `http://subdomain.adatum.com/MyApplication/` , kończy się niepowodzeniem.

## <a name="create-a-deployment"></a>Tworzenie wdrożenia
 Aby uzyskać wskazówki krok po kroku dotyczące tworzenia wdrożeń, które można wdrożyć z różnych lokalizacji sieciowych, zobacz [Przewodnik: ręczne wdrażanie aplikacji ClickOnce, która nie wymaga ponownego podpisywania i zachowuje informacje o znakowaniu](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).

## <a name="see-also"></a>Zobacz też
- [*Mage.exe* (narzędzie tworzenia i edycji manifestów)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [*MageUI.exe* (narzędzie tworzenia i edycji manifestów, klient graficzny)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
