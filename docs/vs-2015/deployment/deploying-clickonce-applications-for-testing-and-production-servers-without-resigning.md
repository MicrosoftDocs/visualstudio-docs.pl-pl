---
title: Wdrażanie aplikacji ClickOnce do testowania i obsługi serwerów produkcyjnych bez ponownego podpisywania | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 2a65f2e39eac5889b287b082b4cad6842f44aa2e
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65675552"
---
# <a name="deploying-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Wdrażanie technologii ClickOnce do testowania i obsługi serwerów produkcyjnych bez ponownego podpisywania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano nową funkcję wprowadzone w .NET Framework w wersji 3.5, która umożliwia wdrażanie aplikacji ClickOnce z wielu lokalizacji sieciowych bez ponownego podpisywania lub zmiana ClickOnce manifesty ClickOnce.  
  
> [!NOTE]
> Rezygnacja nadal jest to preferowana metoda wdrażania nowych wersji aplikacji. Jeśli to możliwe, należy użyć metody resigning. Aby uzyskać więcej informacji, zobacz [Mage.exe (Manifest Generation i narzędzia do edytowania)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1).  
  
 Niezależnych dostawców oprogramowania i deweloperów innych firm można wyrazić zgodę na tę funkcję, co ułatwia ich klienci będą mogli aktualizować aplikacje usługi. Ta funkcja może być używana w następujących sytuacjach:  
  
- Podczas aktualizacji aplikacji, a nie pierwszej instalacji aplikacji.  
  
- Gdy ma tylko jedną konfigurację aplikacji na komputerze. Na przykład jeśli aplikacja jest skonfigurowana by wskazywał dwóch różnych bazach danych, nie można użyć tej funkcji.  
  
## <a name="excluding-deploymentprovider-from-deployment-manifests"></a>Wykluczanie deploymentProvider manifesty wdrożenia  
 W .NET Framework 2.0 i .NET Framework 3.0, każda aplikacja ClickOnce, która jest instalowana na systemu pod kątem dostępności w trybie offline należy określić `deploymentProvider` w manifeście wdrożenia. `deploymentProvider` Często nazywa się aktualizującej; to lokalizacja, w którym ClickOnce będzie szukać aktualizacji aplikacji. To wymaganie, połączone z konieczności wydawcy aplikacji zarejestrować swoje wdrożenia wprowadzone trudne dla firmy zaktualizować aplikacji ClickOnce, od dostawcy lub innych firm. Zapewnia także go trudniejsze do wdrożenia tej samej aplikacji z wielu lokalizacji w tej samej sieci.  
  
 Ze zmianami, które zostały wprowadzone do ClickOnce w .NET Framework 3.5 jest możliwe dla innych firm w celu zapewnienia aplikacji ClickOnce do innej organizacji, które można następnie wdrożyć ją na własnej sieci.  
  
 Aby można było skorzystać z tej funkcji, należy wykluczyć deweloperom aplikacji ClickOnce `deploymentProvider` z ich wdrażania manifestów. Oznacza to, z wyłączeniem `-providerUrl` argumentów podczas tworzenia wdrożenia manifesty Mage.exe lub upewniając się, **Uruchom lokalizacji** pola tekstowego **Manifest aplikacji** karta jest puste Jeśli możesz generują manifesty wdrożenia za pomocą MageUI.exe.  
  
## <a name="deploymentprovider-and-application-updates"></a>deploymentProvider i aktualizacji aplikacji  
 Począwszy od programu .NET Framework 3.5, nie trzeba określać `deploymentProvider` w manifeście wdrożenia w celu wdrożenia aplikacji ClickOnce do użycia w trybie online i offline. Obsługuje ten scenariusz, w których należy spakować i samodzielnie zarejestrować wdrożenia, ale zezwala na innych firm wdrożyć aplikację w swoich sieciach.  
  
 Kluczowym punktem do zapamiętania jest to, że aplikacje, które wykluczyć `deploymentProvider` nie można zmienić ich lokalizacji instalacji podczas aktualizacji, dopóki ich dostarczania aktualizacji, która zawiera `deploymentProvider` tag ponownie.  
  
 Poniżej przedstawiono dwa przykłady, aby wyjaśnić tego punktu. W pierwszym przykładzie publikowanie aplikacji ClickOnce, który nie ma `deploymentProvider` tagu i poproś użytkowników o zainstaluj go z http://www.adatum.com/MyApplication/. Jeśli zdecydujesz, aby opublikować na następną aktualizację aplikacji z http://subdomain.adatum.com/MyApplication/, konieczne będzie żadnej możliwości oznaczającą to w pliku manifestu wdrożenia, która znajduje się w http://www.adatum.com/MyApplication/. Możesz wykonać jedną z następujących czynności:  
  
- Poinformuj użytkowników, aby odinstalować poprzednią wersję, a następnie zainstalowanie nowej wersji z nowej lokalizacji.  
  
- Obejmujące aktualizację na http://www.adatum.com/MyApplication/ zawierającej `deploymentProvider` wskazujący http://www.adatum.com/MyApplication/. Zwolnij inną aktualizację później za pomocą `deploymentProvider` wskazujący http://subdomain.adatum.com/MyApplication/.  
  
  W drugim przykładzie publikowanie aplikacji ClickOnce, który określa `deploymentProvider`, a następnie zdecydujesz się usunąć go. Raz nowej wersji bez `deploymentProvider` została pobrana do klientów, nie można przekierować ścieżki używany do aktualizacji, dopóki nie zostanie wydana wersja Twojej aplikacji, która ma `deploymentProvider` przywrócona. Podobnie jak w pierwszym przykładzie `deploymentProvider` początkowo musi wskazywać bieżącą lokalizację aktualizacji nie nowej lokalizacji. W tym przypadku próba wstawienia `deploymentProvider` odwołujący się do http://subdomain.adatum.com/MyApplication/, Następna aktualizacja zakończy się niepowodzeniem.  
  
## <a name="creating-a-deployment"></a>Tworzenie wdrożenia  
 Aby uzyskać instrukcje krok po kroku dotyczące tworzenia wdrożenia, które mogą zostać wdrożone w różnych lokalizacjach sieciowych, zobacz [instruktażu: Ręczne wdrażanie aplikacji ClickOnce, które nie wymagają ponownego podpisywania i zachowują informacje o znakowaniu](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required?view=vs-2015).  
  
## <a name="see-also"></a>Zobacz też  
 [Mage.exe (manifestu narzędzie generowania i edytowania)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)   
 [MageUI.exe (narzędzie generowania i edytowania manifestu, klient z interfejsem graficznym)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14)
