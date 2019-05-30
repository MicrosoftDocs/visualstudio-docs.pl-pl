---
title: Wdrażanie aplikacji ClickOnce, bez konieczności ponownego podpisywania
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
ms.openlocfilehash: 0b1abda86c8fdd80c20b03a6d3869d025d0a7aaa
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263298"
---
# <a name="deploy-clickonce-applications-for-testing-and-production-servers-without-resigning"></a>Wdrażanie aplikacji ClickOnce do testowania i produkcji serwerów bez ponownego podpisywania
W tym artykule opisano funkcję wprowadzone w .NET Framework w wersji 3.5, która umożliwia wdrażanie aplikacji ClickOnce z wielu lokalizacji sieciowych bez ponownego podpisywania lub zmiana ClickOnce manifesty ClickOnce.

> [!NOTE]
> Rezygnacja nadal jest to preferowana metoda wdrażania nowych wersji aplikacji. Jeśli to możliwe, należy użyć metody resigning. Aby uzyskać więcej informacji, zobacz [ *Mage.exe* (Manifest Generation i narzędzia do edytowania)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool).

 Deweloperzy innych firm i niezależni dostawcy oprogramowania zgodzić się na tej funkcji, co ułatwia ich klienci będą mogli aktualizować aplikacje usługi. Ta funkcja może być używana w następujących sytuacjach:

- Podczas aktualizacji aplikacji, nie dla pierwszej instalacji aplikacji.

- Gdy ma tylko jedną konfigurację aplikacji na komputerze. Na przykład jeśli aplikacja jest skonfigurowana by wskazywał dwóch różnych bazach danych, nie można użyć tej funkcji.

## <a name="exclude-deploymentprovider-from-deployment-manifests"></a>Wyklucz deploymentProvider z manifestów wdrożenia
 .NET Framework 2.0 i .NET Framework 3.0, każda aplikacja ClickOnce, która jest instalowana na systemu pod kątem dostępności w trybie offline należy liście `deploymentProvider` w manifeście wdrożenia. `deploymentProvider` Często nazywa się aktualizującej; to lokalizacja, gdzie ClickOnce szuka aktualizacji aplikacji. To wymaganie, wraz z konieczności wydawcy aplikacji zarejestrować swoje wdrożenia wprowadzone trudne dla firmy zaktualizować aplikacji ClickOnce, od dostawcy lub innych firm. Zapewnia także go trudniejsze do wdrożenia tej samej aplikacji z wielu lokalizacji w tej samej sieci.

 Ze zmianami, które zostały wprowadzone do ClickOnce w .NET Framework 3.5 jest możliwe do firm zapewnić aplikacji ClickOnce do innej organizacji, które można następnie wdrożyć ją na własnej sieci.

 Aby można było skorzystać z tej funkcji, należy wykluczyć deweloperom aplikacji ClickOnce `deploymentProvider` z ich wdrażania manifestów. To wymaganie oznacza, że musisz wykluczyć `-providerUrl` argumentów podczas tworzenia wdrożenia manifesty za pomocą Mage.exe. Lub generowania manifesty wdrożenia za pomocą MageUI.exe, upewnij się, że **Uruchom lokalizacji** pola tekstowego **Manifest aplikacji** karta jest pusty.

## <a name="deploymentprovider-and-application-updates"></a>aktualizacje deploymentProvider i aplikacji
 Począwszy od programu .NET Framework 3.5, nie trzeba określać `deploymentProvider` w manifeście wdrożenia w celu wdrożenia aplikacji ClickOnce do użycia w trybie online i offline. Ta zmiana umożliwia obsługę scenariusza, w których należy spakować i samodzielnie zarejestrować wdrożenia, ale zezwala na innych firm wdrożyć aplikację w swoich sieciach.

 Jest to istotną kwestią, należy pamiętać, że aplikacje, które są wykluczone `deploymentProvider` nie można zmienić ich lokalizacji instalacji podczas aktualizacji, dopóki ich dostarczania aktualizacji, która zawiera `deploymentProvider` tag ponownie.

 Poniżej przedstawiono dwa przykłady, aby wyjaśnić tego punktu. W pierwszym przykładzie publikowanie aplikacji ClickOnce, który nie ma `deploymentProvider` tagu i poproś użytkowników o zainstaluj go z http://www.adatum.com/MyApplication/. Jeśli zdecydujesz, aby opublikować na następną aktualizację aplikacji z http://subdomain.adatum.com/MyApplication/, użytkownik nie ma możliwości oznaczającą to w pliku manifestu wdrożenia, która znajduje się w http://www.adatum.com/MyApplication/. Możesz wykonać jedną z następujących czynności:

- Poinformuj użytkowników, aby odinstalować poprzednią wersję, a następnie zainstalowanie nowej wersji z nowej lokalizacji.

- Obejmujące aktualizację na http://www.adatum.com/MyApplication/ zawierającej `deploymentProvider` wskazujący http://www.adatum.com/MyApplication/. Zwolnij inną aktualizację później za pomocą `deploymentProvider` wskazujący http://subdomain.adatum.com/MyApplication/.

  W drugim przykładzie publikowanie aplikacji ClickOnce, który określa `deploymentProvider`, a następnie zdecydujesz się usunąć go. Raz nowej wersji bez `deploymentProvider` zostanie pobrana do klientów, nie można przekierować ścieżki używany do aktualizacji, dopóki nie zostanie wydana wersja Twojej aplikacji, która ma `deploymentProvider` przywrócona. Podobnie jak w pierwszym przykładzie `deploymentProvider` początkowo musi wskazywać bieżącą lokalizację aktualizacji nie nowej lokalizacji. W tym przypadku próba wstawienia `deploymentProvider` odwołujący się do http://subdomain.adatum.com/MyApplication/, Następna aktualizacja zakończy się niepowodzeniem.

## <a name="create-a-deployment"></a>Tworzenie wdrożenia
 Aby uzyskać instrukcje krok po kroku dotyczące tworzenia wdrożenia, które mogą zostać wdrożone w różnych lokalizacjach sieciowych, zobacz [instruktażu: Ręczne wdrażanie aplikacji ClickOnce, które nie wymagają ponownego podpisywania i zachowują informacje o znakowaniu](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).

## <a name="see-also"></a>Zobacz także
- [*Mage.exe* (Manifest narzędzie generowania i edytowania)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
- [*MageUI.exe* (Manifest narzędzie, graficzny klient generowania i edytowania)](/dotnet/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client)
