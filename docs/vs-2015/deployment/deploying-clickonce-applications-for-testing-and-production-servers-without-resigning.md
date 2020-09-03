---
title: Wdrażanie aplikacji ClickOnce do testowania i serwerów produkcyjnych bez konieczności przepisywania | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "80395372"
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Wdrażanie technologii ClickOnce do testowania i obsługi serwerów produkcyjnych bez ponownego podpisywania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie omówiono nową funkcję technologii ClickOnce wprowadzoną w .NET Framework w wersji 3,5, która umożliwia wdrażanie aplikacji ClickOnce z wielu lokalizacji sieciowych bez ponownego podpisywania lub zmiany manifestów ClickOnce.  
  
> [!NOTE]
> Rejestracja jest nadal preferowaną metodą wdrażania nowych wersji aplikacji. Za każdym razem, gdy to możliwe, użyj metody podpisywania. Aby uzyskać więcej informacji, zobacz [Mage.exe (narzędzie tworzenia i edycji manifestów)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
 Deweloperzy innych firm i dostawcy oprogramowania mogą korzystać z tej funkcji, ułatwiając klientom aktualizowanie aplikacji. Ta funkcja może być używana w następujących sytuacjach:  
  
- Podczas aktualizacji aplikacji, a nie pierwszej instalacji aplikacji.  
  
- Jeśli na komputerze jest tylko jedna konfiguracja aplikacji. Jeśli na przykład aplikacja jest skonfigurowana tak, aby wskazywała dwie różne bazy danych, nie można użyć tej funkcji.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Wykluczanie deploymentProvider z manifestów wdrożenia  
 W .NET Framework 2,0 i .NET Framework 3,0 wszystkie aplikacje ClickOnce, które są instalowane w systemie w celu zapewnienia dostępności w trybie offline, muszą określać `deploymentProvider` w manifeście wdrożenia. `deploymentProvider`Jest często określana jako lokalizacja aktualizacji; jest to lokalizacja, w której ClickOnce będzie sprawdzać dostępność aktualizacji aplikacji. Ten wymóg, który jest niezbędny dla wydawcy aplikacji do podpisywania wdrożeń, utrudnia firmie aktualizację aplikacji ClickOnce od dostawcy lub innej innej firmy. Utrudnia to również wdrażanie tej samej aplikacji z wielu lokalizacji w tej samej sieci.  
  
 Ze zmianami wprowadzonymi w technologii ClickOnce w .NET Framework 3,5, istnieje możliwość, że firma zewnętrzna dostarcza aplikację ClickOnce do innej organizacji, która następnie może wdrożyć aplikację w własnej sieci.  
  
 Aby móc korzystać z tej funkcji, deweloperzy aplikacji ClickOnce muszą wykluczyć `deploymentProvider` z ich manifestów wdrożenia. Oznacza to wykluczenie `-providerUrl` argumentu podczas tworzenia manifestów wdrożenia za pomocą Mage.exe lub upewnienie się, że pole tekstowe **Lokalizacja uruchamiania** na karcie **manifest aplikacji** jest puste, jeśli są generowane manifesty wdrożenia z MageUI.exe.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider i aktualizacje aplikacji  
 Począwszy od .NET Framework 3,5, nie trzeba już określać `deploymentProvider` w manifeście wdrożenia, aby można było wdrożyć aplikację ClickOnce zarówno w trybie online, jak i offline. To rozwiązanie obsługuje scenariusz, w którym trzeba samodzielnie spakować i podpisać wdrożenie, ale zezwolić innym firmom na wdrożenie aplikacji za pośrednictwem swoich sieci.  
  
 Najważniejszym miejscem do zapamiętania jest to, że aplikacje, które wykluczają, `deploymentProvider` nie mogą zmieniać lokalizacji instalacji podczas aktualizacji, dopóki nie wyślą aktualizacji, która zawiera `deploymentProvider` znacznik ponownie.  
  
 Poniżej przedstawiono dwa przykłady do wyjaśnienia tego punktu. W pierwszym przykładzie należy opublikować aplikację ClickOnce, która nie ma `deploymentProvider` tagu, i poprosił użytkowników o ich zainstalowanie `http://www.adatum.com/MyApplication/` . Jeśli zdecydujesz, że chcesz opublikować następną aktualizację aplikacji z programu `http://subdomain.adatum.com/MyApplication/` , nie będzie można jej wyznaczać w manifeście wdrożenia, który znajduje się w `http://www.adatum.com/MyApplication/` . Można wykonać jedną z dwóch czynności:  
  
- Poinformuj użytkowników, aby odinstalował poprzednią wersję, i zainstaluj nową wersję z nowej lokalizacji.  
  
- Uwzględnij aktualizację `http://www.adatum.com/MyApplication/` , która zawiera `deploymentProvider` wskazanie elementu `http://www.adatum.com/MyApplication/` . Następnie zwolnij kolejną aktualizację później, `deploymentProvider` wskazując polecenie `http://subdomain.adatum.com/MyApplication/` .  
  
  W drugim przykładzie należy opublikować aplikację ClickOnce, która określa `deploymentProvider` , a następnie zdecydować o jej usunięciu. Gdy nowa wersja nie zostanie `deploymentProvider` pobrana do klientów, nie będzie można przekierować ścieżki używanej do aktualizacji do momentu wydania wersji aplikacji, która została `deploymentProvider` przywrócona. Podobnie jak w przypadku pierwszego przykładu, `deploymentProvider` musi początkowo wskazywać bieżącą lokalizację aktualizacji, a nie nową lokalizację. W takim przypadku próba wstawienia elementu `deploymentProvider` , który odwołuje się do programu `http://subdomain.adatum.com/MyApplication/` , kończy się niepowodzeniem.  
  
## <a name="creating-a-deployment"></a>Tworzenie wdrożenia  
 Aby uzyskać wskazówki krok po kroku dotyczące tworzenia wdrożeń, które można wdrożyć z różnych lokalizacji sieciowych, zobacz [Przewodnik: ręczne wdrażanie aplikacji ClickOnce, która nie wymaga ponownego podpisywania i zachowuje informacje o znakowaniu](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required?view=vs-2015).  
  
## <a name="see-also"></a>Zobacz też  
 [Mage.exe (Narzędzie tworzenia i edycji manifestów)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (Narzędzie tworzenia i edycji manifestów, klient graficzny)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)
