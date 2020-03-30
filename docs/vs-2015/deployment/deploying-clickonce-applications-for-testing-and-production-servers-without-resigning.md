---
title: Wdrażanie aplikacji ClickOnce do testowania i tworzenia serwerów bez rezygnacji | Dokumenty firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a8e41e67d5e2800acc41e1220fe632001420a274
ms.sourcegitcommit: d6828e7422c8d74ec1e99146fedf0a05f757245f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395372"
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Wdrażanie technologii ClickOnce do testowania i obsługi serwerów produkcyjnych bez ponownego podpisywania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie omówiono nową funkcję ClickOnce wprowadzone w .NET Framework w wersji 3.5, który umożliwia wdrażanie aplikacji ClickOnce z wielu lokalizacji sieciowych bez ponownego podpisywania lub zmiany Manifesty ClickOnce.  
  
> [!NOTE]
> Rezygnacja jest nadal preferowaną metodą wdrażania nowych wersji aplikacji. Jeśli to możliwe, użyj metody rezygnacji. Aby uzyskać więcej informacji, zobacz [Mage.exe (Manifest Generation and Editing Tool)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
 Deweloperzy zewnętrzni i dostawcy oprogramowania mogą wyrazić zgodę na tę funkcję, co ułatwia klientom aktualizowanie aplikacji. Ta funkcja może być używana w następujących sytuacjach:  
  
- Podczas aktualizowania aplikacji, nie pierwsza instalacja aplikacji.  
  
- Gdy na komputerze jest tylko jedna konfiguracja aplikacji. Na przykład jeśli aplikacja jest skonfigurowana do wskazywała dwie różne bazy danych, nie można użyć tej funkcji.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Wykluczanie wdrożeniaProvider z manifestów wdrażania  
 W .NET Framework 2.0 i .NET Framework 3.0 każda aplikacja ClickOnce instaluje się `deploymentProvider` w systemie w celu zapewnienia dostępności w trybie offline musi określać w manifeście wdrożenia. Jest `deploymentProvider` często określane jako lokalizacja aktualizacji; jest to lokalizacja, w której ClickOnce sprawdzi dostępność aktualizacji aplikacji. To wymaganie, w połączeniu z koniecznością wydawców aplikacji do podpisania ich wdrożeń, utrudniło firmie zaktualizować clickonce aplikacji od dostawcy lub innej firmy. Utrudnia to również wdrożenie tej samej aplikacji z wielu lokalizacji w tej samej sieci.  
  
 Ze zmianami, które zostały wprowadzone do ClickOnce w .NET Framework 3.5, jest możliwe dla innych firm, aby zapewnić ClickOnce aplikacji do innej organizacji, która może następnie wdrożyć aplikację w swojej sieci.  
  
 Aby skorzystać z tej funkcji, deweloperzy aplikacji ClickOnce należy wykluczyć `deploymentProvider` z ich manifestów wdrażania. Oznacza to wyłączenie `-providerUrl` argumentu podczas tworzenia manifestów wdrożenia za pomocą programu Mage.exe lub upewnienie się, że pole tekstowe **Lokalizacja uruchamiania** na karcie **Manifest aplikacji** pozostaje puste, jeśli generujesz manifesty wdrażania za pomocą programu MageUI.exe.  
  
## <a name="deploymentprovider-and-application-updates"></a>Aktualizacje oprogramowania i aplikacji deploymentProvider i Application  
 Począwszy od .NET Framework 3.5, nie `deploymentProvider` trzeba już określić w manifeście wdrożenia w celu wdrożenia clickonce aplikacji dla użycia w trybie online i offline. Obsługuje to scenariusz, w którym należy spakować i podpisać wdrożenie samodzielnie, ale zezwolić innym firmom na wdrożenie aplikacji za pośrednictwem swoich sieci.  
  
 Punktem kluczowym do zapamiętania jest `deploymentProvider` to, że aplikacje, które wykluczają nie `deploymentProvider` można zmienić ich lokalizacji instalacji podczas aktualizacji, dopóki nie wysyła aktualizacji, która zawiera tag ponownie.  
  
 Oto dwa przykłady, aby wyjaśnić tę kwestię. W pierwszym przykładzie publikujesz aplikację ClickOnce, która nie `deploymentProvider` ma tagu, i prosisz użytkowników o zainstalowanie go z `http://www.adatum.com/MyApplication/`programu . Jeśli zdecydujesz, że chcesz opublikować następną `http://subdomain.adatum.com/MyApplication/`aktualizację aplikacji z programu , nie będziesz miał możliwości `http://www.adatum.com/MyApplication/`oznaczenia tego w manifeście wdrażania, który znajduje się w . Możesz wykonać jedną z dwóch rzeczy:  
  
- Powiedz użytkownikom, aby odinstalowali poprzednią wersję i zainstaluj nową wersję z nowej lokalizacji.  
  
- Dołącz aktualizację, `http://www.adatum.com/MyApplication/` która `deploymentProvider` zawiera `http://www.adatum.com/MyApplication/`punktowanie . Następnie zwolnij kolejną `deploymentProvider` aktualizację `http://subdomain.adatum.com/MyApplication/`później ze wskazaniem .  
  
  W drugim przykładzie można opublikować ClickOnce `deploymentProvider`aplikacji, która określa , a następnie zdecydujesz się go usunąć. Po pobraniu `deploymentProvider` nowej wersji bez zostanie pobrana do klientów, nie będzie można przekierować ścieżkę `deploymentProvider` używaną do aktualizacji, dopóki nie wydasz wersji aplikacji, która została przywrócona. Podobnie jak w `deploymentProvider` pierwszym przykładzie, musi początkowo wskazywać bieżącą lokalizację aktualizacji, a nie nową lokalizację. W takim przypadku, jeśli spróbujesz `deploymentProvider` wstawić, który odwołuje się do `http://subdomain.adatum.com/MyApplication/`, a następnie następna aktualizacja zakończy się niepowodzeniem.  
  
## <a name="creating-a-deployment"></a>Tworzenie wdrożenia  
 Aby uzyskać wskazówki krok po kroku dotyczące tworzenia wdrożeń, które można wdrożyć z różnych lokalizacji sieciowych, zobacz [Wskazówki: Ręczne wdrażanie aplikacji ClickOnce, która nie wymaga ponownego podpisywania i która zachowuje informacje o znakowaniu.](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required?view=vs-2015)  
  
## <a name="see-also"></a>Zobacz też  
 [Mage.exe (narzędzie do generowania manifestów i edycji)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (narzędzie do generowania manifestu i edycji, klient graficzny)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)
